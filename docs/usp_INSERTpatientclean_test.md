# usp_INSERTpatientclean_test
Inserts patients into patientclean_test.

ceg_admin.dbo.**usp_INSERTpatientclean_test**

inserts patients identified as test patients because of their name (eg EMIS test, Mikey Mouse etc) or with who have an invalid NHS number.  The reason for inclusion is provided by a code in the invalid_pt field.

See [patientclean tables]

```SQL
USE ceg_admin;
EXEC usp_INSERTpatientclean_test
```
