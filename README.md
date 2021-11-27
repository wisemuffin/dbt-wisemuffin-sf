# snowflake and dbt (plus other goodies)

This is a playground for me to test and document my analytical engineering skills.

![image](./images/wisemuffin.JPG)

## repos

This project is broken down into several repos to isolate environments and to simplify CICD.

- [dbt-wisemuffin-sf-trading](https://github.com/wisemuffin/dbt-wisemuffin-sf-trading) - demo dbt features
- [terraform-snowflake-fast-data-warehouse](https://github.com/wisemuffin/terraform-snowflake-fast-data-warehouse) - manages all cloud infrastructure.

## architecture
![image](./images/architecturedrawio.png)

## features - snowflake

### query tagging

if you go in Snowflake UI and click ‘History' icon on top, you are going to see all SQL queries run on Snowflake account(successful, failed, running etc) and clearly see what dbt model this particular query is related to:

![image](./images/query_tagging.png)

[source](https://quickstarts.snowflake.com/guide/data_engineering_with_dbt_cli/index.html?index=..%2F..index#6)

## resource monitor

Ideally this will be included in my terraform infrastructure as code. However currently due to the limitation of only accountadmin role only have the ability to create this resource i have set this up manually.s

![image](./images/snowflake_resource_monitor.png)

## features - dbt

### custom schema naming

By default, dbt is [generating a schema name](https://docs.getdbt.com/docs/building-a-dbt-project/building-models/using-custom-schemas) by appending it to the target schema environment name(dev, prod). In dbt_trading I show you a quick way to override this macro, making our schema names to look exactly the same between dev and prod databases. 

### CICD

TODO

![image](./images/cicd.drawio.png)

### lineage in cloud
 TODO


## dbt projects

### bt-wisemuffin-sf-trading

repo: [dbt-wisemuffin-sf-trading](https://github.com/wisemuffin/dbt-wisemuffin-sf-trading)

This is build from snowflakes quick start [Accelerating Data Engineering with Snowflake & dbt CLI](https://quickstarts.snowflake.com/guide/data_engineering_with_dbt_cli/index.html?index=..%2F..index#1)

*dbt features demoed:*
- custom schema naming
- query tagging
- basic incremental model (append only) - models/l30_mart/fct_trading_pnl.sql as the source data is live this is easy to show.
- dbt_utils.union_relations - see models/l20_transform/tfm_book.sql which unions two manually uploaded (seeds) trading books.

*snowflake features demoed*
- uses live data market data shared on snowflake

*sources*
-  Knoema Dataset Catalog table: daily exchange rates  
-  Knoema Dataset Catalog table: daily US trading history


## infrastructure

All dbt projects infrastructure is being managed by a single [terraform repo](https://github.com/wisemuffin/terraform-snowflake-fast-data-warehouse).

## data integration

TODO

## orchistration

TODO

## data quality and goverance

TODO

## data visualisation

TODO