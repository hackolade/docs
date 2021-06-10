# Server timeout during read query at consistency LOCAL_ONE

There are several possible issues.

* It may be a problem with a[ large amount of tombstones](<https://support.datastax.com/hc/en-us/articles/204612559-ReadTimeoutException-seen-when-using-the-java-driver-caused-by-excessive-tombstones> "target=\"\_blank\"") in cassandra. In this case we would suggest to either increase ‘tombstone\_failure\_threshold’ in cassandra.yaml or [clean up](<https://stackoverflow.com/questions/27566615/can-i-force-cleanup-of-old-tombstones> "target=\"\_blank\"") tombstones.
* There are not [enough alive replicas](<https://stackoverflow.com/questions/38231621/cassandra-operation-timed-out> "target=\"\_blank\""). We would propose to increase the replication factor.
* In some cases there is [not enough request timeout](<https://stackoverflow.com/questions/38231621/cassandra-operation-timed-out> "target=\"\_blank\""). We are proposing to try to increase ‘read\_request\_timeout\_in\_ms’ in cassandra.yaml, if it is possible.

&nbsp;

