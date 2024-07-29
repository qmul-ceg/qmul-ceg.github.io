# usp_GetQueryCodes
**db_lookup.gpp**

Maps the codes in provided cluster_ids to SNOMED, Read2, CTV3, and EMIS, TPP and VISION local codes. Thereby provides a full codeset of mapped codes.

**usp_GetQueryCodes @codesettable, @codesetclusters, @print**

**@codesettable**: address of table containing code clusters in format 'database.schema.table' or '#temp_table'. Must contain
*cluster_id* nvarchar - field with identifiers that group the code clusters
*code* nvarchar - field with the codes within the cluster.
*scheme*  or *scheme_id*  [big]int or nvarchar - field with either the dbid or the prefix id of the code's scheme. Commonly used prefixs and dbids are:

code name | scheme_id | scheme
-|-|-
SNOMED | SN | 71
Read 2 | R2 | 1040444
Read3 / CTV3 | R3 | 1130062
EMIS Local | EMLOC | 1335379
TPP Local | TPPLOC | 1440863
Vision Local | VISLOC | 1526923

**@codesetclusters**: list of comma seperated cluster ids.

**@print**: flag to print rather than run the procedure's dynamic SQL. Set to 1 to print. Default = 0.
```SQL
USE db_lookup;
EXEC gpp.usp_GetQueryCodes 'codesets.dbo.codeset_PCD', 'AF_COD, DM_COD, DMRES_COD'
```

## Output
cluster_id | scheme | scheme_id | code | name | dbid | sn_dbid | sn_code
-|-|-|-|-|-|-|-
-|-|-|-|-|-|-|-

## tt_QueryCodes
**db_lookup.gpp**

Table Type for output of usp_GetQueryCodes. Can be used to insert output into a table variable.
```SQL
USE db_lookup;
DECLARE @querycodes gpp.tt_QueryCodes
INSERT INTO @querycodes
EXEC gpp.usp_GetQueryCodes 'codesets.dbo.codeset_PCD', 'AF_COD, DM_COD, DMRES_COD'
```
