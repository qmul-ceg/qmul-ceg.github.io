# sp_WhoIsActive
Provides information on current user actvity. Downloaded from http://whoisactive.com which also provides comprehensive documentation.

db_lookup.dbo.**sp_WhoIsActive**

**@filter** sysname = ''  
**@filter_type** VARCHAR(10) = 'session'  
**@not_filter** sysname = ''  
**@not_filter_type** VARCHAR(10) = 'session'  
**@show_own_spid** BIT = 0  
**@show_system_spids** BIT = 0  
**@show_sleeping_spids** TINYINT = 1  
**@get_full_inner_text** BIT = 0  
**@get_plans** TINYINT = 0  
**@get_outer_command** BIT = 0  
**@get_transaction_info** BIT = 0  
**@get_task_info** TINYINT = 1  
**@get_locks** BIT = 0  
**@get_avg_time** BIT = 0  
**@get_additional_info** BIT = 0  
**@find_block_leaders** BIT = 0  
**@delta_interval** TINYINT = 0  
**@output_column_list** VARCHAR(8000) = '[dd%][session_id][sql_text][sql_command][login_name][wait_info][tasks][tran_log%][cpu%][temp%][block%][reads%][writes%][context%][physical%][query_plan][locks][%]'  
**@sort_order** VARCHAR(500) = '[start_time] ASC'  
**@format_output** TINYINT = 1  
**@destination_table** VARCHAR(4000) = ''  
**@return_schema** BIT = 0  
**@schema** VARCHAR(MAX) = NULL OUTPUT  
**@help** BIT = 0

```SQL
EXEC sp_WhoIsActive
```

## Output

dd hh:mm:ss.mss	| session_id	|sql_text	|login_name	|wait_info|	CPU	|tempdb_allocations|	tempdb_current|	blocking_session_id|	reads|	writes|	physical_reads|	used_memory|	status|	open_tran_count|	percent_complete|	host_name|	database_name|	program_name|	start_time|	login_time|	request_id|	collection_time
-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|
-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|