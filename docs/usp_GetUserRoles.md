# usp_GetUserRoles
Returns the database user roles attached to given server login with role permissions information obtained from `db_lookup.dbo.compass_roles`.

db_lookup.dbo.**usp_GetUserRoles @login**

**@login** sysname: server login


```SQL
EXEC db_lookup.dbo.usp_GetUserRoles user_ksmith
```

## Output

| db | username | role | grant | deny
| :------- | :--- |:----|:----|:----
| -        | -    |- |- |-|-