# usp_GetEthnicity
**db_lookup.gpp**

Returns the latest legacy and SNOMED, [CEG] 16+1 and [NHS] 5+1 codes for a given cohort, plus code terms, date and dbid. Patient's without an ethnicity code are returned as NULLs.

**usp_GetEthnicity @cohorttable, @latestday, @print**

**@cohorttable** nvarchar(100): address of table containing code clusters in format 'database.schema.table' or '#temp_table'. Must contain:
	* *patient_id* bigint - id of patients on which to search. No duplicates.

**@latestday** smallint: flag to return either the codes from the latest day on which ethnicity recorded (1) or the latest classifiable code ever recorded (0). The row field shows which row, within the date ranked ethnicity codes for the patient, was returned. This allows for an assessment of whether the code is too historic to used. Set to 1 for the latest date. Default = 1.

**@print** int: flag to print rather than run the procedure's dynamic SQL. Set to 1 to print. Default = 0.
```SQL
USE db_lookup;
EXEC gpp.usp_GetEthnicity 'analysis_ceg.dbo.testpop'

EXEC gpp.usp_GetEthnicity 'analysis_ceg.dbo.testpop'
```

## Output

patient_id | person_id | code | sn_code | term | clinical_effective_date | ceg_16 | ceg_16_term | nhs_5 | nhs_5_term | dbid | row
-|-|-|-|-|-|-|-|-|-|-|-
-|-|-|-|-|-|-|-|-|-|-|-

## tt_Ethnicity
**db_lookup.gpp**

Table Type for output of usp_GetEthnicity. Can be used to insert output into a table variable.
```SQL
USE db_lookup;
DECLARE @ethpop gpp.tt_Ethnicity
INSERT INTO @ethpop
EXEC gpp.usp_GetEthnicity #CH_pop
```
