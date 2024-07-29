
# usp_GetRandomPPt
**db_lookup.gpp**

Returns a list of random, unique patient or person ids - no duplicates.  Created from ids in person or patient table, so all subsequent JOINS will work. A list of 100 ids takes c.30 seconds.

**usp_GetRandomPPt @size, @table**

**@size** int: number of ids to return

**@table** nvarchar(7): table for id extraction - person table = 'p' or 'per\*', patient table = 'pt' or 'pat*'.

```SQL
USE db_lookup;
EXEC gpp.usp_GetRandomPPt 100, 'pt'
```

## Output

| id_table | id   |
| :------- | :--- |
| -        | -    |

## tt_RandomPPt
**db_lookup.gpp**

Table Type for output of usp_GetRandomPPt. Can be used to insert output into a table variable.
```SQL
USE db_lookup;
DECLARE @random gpp.tt_RandomPPt
INSERT INTO @random
EXEC gpp.usp_GetRandomPPt 100, 'pt'
```
