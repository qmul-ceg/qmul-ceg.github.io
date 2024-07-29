# usp_GetCurrReg
**db_lookup.gpp**

Returns the current registered population for the provided relative run date and CCG/areas.

**usp_GetCurrReg @RELRUN_DAT, @CCG**

**@RELRUN_DAT**: date at which population registered. Script searches for dates before and up to (<) this date.

**@CCG**: list of comma separated old CCG ods codes (eg '08V, 08M, 07T') or area identifiers (eg 'CH, NH, TH, WF, HV, RB, BK').

```SQL
USE db_lookup;
EXEC gpp.usp_GetCurrReg '2021-05-01', 'TH, NH, CH'
```

## Output

relrun_dat | person_id | patient_id | organization_id | reg_date | dereg_date
-|-|-|-|-|-
-|-|-|-|-|-

## tt_CurrReg
**db_lookup.gpp**

Table Type for output of usp_GetCurrReg. Can be used to insert output into a table variable.
```SQL
USE db_lookup;
DECLARE @querypop gpp.tt_CurrReg
INSERT INTO @querypop
EXEC gpp.usp_GetCurrReg '2021-05-01', 'TH, NH, CH'
```

