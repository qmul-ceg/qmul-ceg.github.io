# usp_MakePassword
**db_lookup.dbo**

Creates a password of random characters (0-9, A-Z, a-z, symbols) of given length, up to 25 characters.  Returns as @pwd.

**usp_GetCurrReg @len, @charnum, @pwd OUTPUT**

**@len** int: length of password

**@charnum** int: character sets to include
	* 1 = 0-9
	* 2 = 0-9 and A-Z
	* 3 = 0-9, A-Z and a-z
	* 4 = 0-9, A-Z, a-z and :;<=>?@
	* 5 = 0-9, A-Z, a-z, :;<=>?@ and [\]^_

**@pwd** nvarchar(25): Output variable. Needs to be declared  as, or passed into, a declared and set variable.  Variable is usually set to '' (no value) but a value could be given, in which case this value will prefix the generated random password.

```SQL
USE db_lookup;
DECLARE @pwd nvarchar(12) = ''
EXEC usp_MakePassword 12, 3, @pwd OUTPUT

SELECT @pwd
```
```SQL
USE db_lookup;
DECLARE @password nvarchar(16) = 'CEG_'
EXEC usp_MakePassword 12, 3, @pwd = @password OUTPUT

SELECT @password
```

## Output

@pwd varchar(25)