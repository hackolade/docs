---
description: Connect Hackolade Studio to Hive with Plain SASL, when hive.server2.authentication is set to none.
seoTitle: Hive Plain SASL authentication
image: lib/Hive - Connection settings - Plain SASL.png
---
# None (Plain SASL)

## Plain SASL Authentication

If the property “hive.server2.authentication” in the Hive configuration is set as “none”, it means that Hive uses Plain SASL authentication method.

```xml
<property>
  <name>hive.server2.authentication</name>
  <value>none</value>
</property>
```

![Hive - Connection settings - Plain SASL](<lib/Hive - Connection settings - Plain SASL.png>)
