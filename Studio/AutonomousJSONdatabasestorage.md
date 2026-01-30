# Autonomous JSON database storage

Storage is one of the parameters in your monthly OCI invoice.&nbsp; To understand this aspect, we cover below

* how to monitor your storage utilization,&nbsp;
* how to get further details,&nbsp;
* and how to reclaim unused space.

&nbsp;

## Monitor storage utilization

To view the storage utilization for your instance, go to the OCI Console, open the menu \> Oracle AI Database \> Autonomous AI Database or [https://cloud.oracle.com/db/adbs](<https://cloud.oracle.com/db/adbs> "target=\"\_blank\""), then click on your database name to open its Details page, then go:

&nbsp;

* either to the Monitoring tab (all the way to the right...) to view the Storage utilization graph

![OCI storage utilization monitoring graph](<lib/OCI storage utilization monitoring graph.png>)\
&nbsp;

* or click on the Database actions button and choose the option "View all database actions"

![OCI view all database actions](<lib/OCI view all database actions.png>)

then in the menu, choose Monitoring \> Database Dashboard:

![OCI database actions menu](<lib/OCI database actions menu.png>)

&nbsp;

and view this summary on the left hand side:

![OCI database dashboard storage used and allocated](<lib/OCI database dashboard storage used allocated.png>)

&nbsp;

The above graph shows that 52% of storage is allocated. The storage actually used is 29% within this storage, and only 8% is allocated to the JSON data coming from your Git repositories (the small bar at the bottom of the graph).

&nbsp;

In Oracle Cloud Infrastructure (OCI), the difference between storage allocated and storage used is as follows:

* Storage Allocated: amount of storage physically reserved or allocated for the database in all tablespaces (data and temporary), including the free space within those tablespaces. It represents the total storage capacity dedicated to the database, whether it is currently occupied with data or not.&nbsp; Allocated storage excludes storage for sample schemas.
* Storage Used: actual amount of storage actively used by database objects such as tables, indexes, and also includes any internally used temporary space within the tablespaces.&nbsp; It excludes the free space in the allocated tablespaces and also excludes the sample schema storage.

&nbsp;

OCI supports auto scaling of storage, where maximum storage can be up to three times the base reserved storage, but allocated and used storage are the physical and actual consume metrics at any given time.

&nbsp;

You are billed based on the total amount of storage capacity allocated or reserved for your database or storage service, including both the space that contains data and the free space reserved within that allocation. Even if not all the allocated storage is actively used by data, you pay for what has been provisioned.

&nbsp;

This approach ensures capacity is available as needed, but it also means monitoring allocated storage is important for cost management, so you do not over-allocate storage and incur unnecessary charges.

&nbsp;

&nbsp;

## Further details

Now, let's dig a bit deeper to understand how our data is stored.&nbsp; The queries below are mostly coming from [this source](<https://database-heartbeat.com/2021/11/22/calc-storage-adb/> "target=\"\_blank\"").&nbsp;

&nbsp;

### Storage used

You can run the following query:

&nbsp;

> select owner, sum(bytes)/1024/1024/1024 as size\_gb \
from dba\_segments \
group by owner \
order by size\_gb desc;

&nbsp;

Which will lead to a result not unlike this:

&nbsp;

> "OWNER"&nbsp; &nbsp; "SIZE\_GB"\
"SSB"&nbsp; &nbsp; 162.41888427734375\
"HCK\_HUB"&nbsp; &nbsp; 2.767822265625\
"SYS"&nbsp; &nbsp; 1.6702880859375\
"APEX\_240200"&nbsp; &nbsp; 0.82513427734375\
"OML$METADATA"&nbsp; &nbsp; 0.15924072265625\
"ODI\_REPO\_USER"&nbsp; &nbsp; 0.142822265625\
"MDSYS"&nbsp; &nbsp; 0.07470703125\
"GRAPH$METADATA"&nbsp; &nbsp; 0.02197265625\
"C##ADP$SERVICE"&nbsp; &nbsp; 0.0091552734375\
"C##CLOUD$SERVICE"&nbsp; &nbsp; 0.009033203125\
"ORDS\_METADATA"&nbsp; &nbsp; 0.0069580078125\
"SH"&nbsp; &nbsp; 0.005615234375\
"AUDSYS"&nbsp; &nbsp; 0.00518798828125\
"CTXSYS"&nbsp; &nbsp; 0.00494384765625\
"DVSYS"&nbsp; &nbsp; 0.00445556640625\
"RMAN$CATALOG"&nbsp; &nbsp; 0.0020751953125\
"GSMADMIN\_INTERNAL"&nbsp; &nbsp; 0.0010986328125\
"XDB"&nbsp; &nbsp; 0.00091552734375\
"ADMIN"&nbsp; &nbsp; 0.00079345703125\
"VECSYS"&nbsp; &nbsp; 0.00054931640625\
"SYSTEM"&nbsp; &nbsp; 0.0003662109375\
"LBACSYS"&nbsp; &nbsp; 0.00030517578125\
"OML$MODELS"&nbsp; &nbsp; 0.0001220703125

&nbsp;

The [SSB](<https://docs.oracle.com/en-us/iaas/autonomous-database-serverless/doc/sample-queries.html>) and [SH](<https://www.oracle.com/europe/database/technologies/appdev/datamodeler-samples.html> "target=\"\_blank\"") schema are sample schemas, and its storage isn't counted toward the storage billed.

&nbsp;

To calculate your actual storage uses, simply sum the bytes used in the segments (except for the SSB and SH sample schemas)

&nbsp;

> select sum(bytes)/1024/1024/1024 as USED\_TOTAL\_GB\
from dba\_segments \
where owner not in ('SSB', 'SH');

&nbsp;

In our example above, the user schema for the Model Hub is HCK\_HUB and it show a manageable size of less than 3GB for the 1500 or so models in our various Git repositories.&nbsp; This storage used will grow with the number of synchronized models.

&nbsp;

### Storage allocated

Allocated storage is important because it is the actual disk space reserved on the disk used by OCI to bill for the database instance.

&nbsp;

This query&nbsp;

&nbsp;

> with cte as\
(\
&nbsp; &nbsp; select 'data\_files' as type, sum(bytes)/1024/1024/1024 as size\_gb from dba\_data\_files where tablespace\_name \!= 'SAMPLESCHEMA'\
&nbsp; &nbsp; union all\
&nbsp; &nbsp; select 'temp\_files' as type, sum(bytes)/1024/1024/1024 as size\_gb from dba\_temp\_files\
)\
select \* from cte;

&nbsp;

gives us our allocated space:

&nbsp;

> "TYPE" "SIZE\_GB"\
"data\_files" 10.220703125\
"temp\_files" 2.064453125\
"total" 12.285

&nbsp;

The data files are where the bulk of the data is stored, which is normal since they contain actual data, while the temp files are temporary files used by the database for operations like sorting data.

&nbsp;

## Reclaim unused space

Storage management is handled automatically by the database. Normally, you should not have to care about clean up tasks, especially when using the Autonomous AI Database.

&nbsp;

However, if you just inserted a huge amount of data for a test in a non-production environment, then want to free up space yourself, it is still possible by resizing the data files.&nbsp; To reduce the storage allocated, you may reclaim some free space by following [these instructions](<https://anjo.pt/keyword-oracle/2020/09/04/how-to-reclaim-storage-space-on-oracle-autonomous-database/> "target=\"\_blank\"").

