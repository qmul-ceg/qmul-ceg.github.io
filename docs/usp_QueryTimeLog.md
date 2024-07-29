# usp_QueryTimeLog
**db_lookup.dbo**

Logs the provided query and step text with datetime into ceg_admin.dbo.querytimelog.  Enables logging of times of within a query.

**usp_QueryTimeLog @query, @step, @clean**

**@query** nvarchar(50): free text to identify query being run

**@step** nvarchar(50): free text to identify step being logged

**@clean** smallint: instruction for cleaning previous log entries. Default = 0
* 0 = log step to ceg_admin.dbo.querytimelog
* 1 = delete previous logs with the same @query and log step to ceg_admin.dbo.querytimelog
* 2 = delete previous logs with the same @query.

```SQL
EXEC db_lookup.dbo.usp_querytimelog 'test query', 'start', 1

EXEC db_lookup.dbo.usp_querytimelog 'test query', 'end'
```

## Output

| id | query | step | tstamp
| :------- | :--- |:----|:----
| -        | -    |- |- |-