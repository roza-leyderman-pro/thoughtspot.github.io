---
title: [TQL service reference]
summary: "The TQL service APIs enable you to query the ThoughtSpot TQL cli from a remote machine."
last_updated: 09/10/2020
sidebar: mydoc_sidebar
permalink: /:collection/:path.html
---

## Design
The TQL service accepts HTTP/HTTPS requests through a python client to provide a TQL-cli like experience.
You can develop your own REST client to use the REST APIs documented below. No setup is required on the server side.

## Client requirements
- Must contact the TQL service over a standard HTTPS port (i.e. 443)
- Must authenticate before using any REST API
- Must be authorized to perform certain TQL operations

## HTTP APIs

### Login
The existing Callosum login API is used. The following API is provided for reference.

#### API

##### POST request

```
/callosum/v1/session/login
```
##### Input
```
{
	"username": "<thoughtspot user name>",
	"password": "<thoughtspot password>"
}
```
##### Output
```
Status: 200 OK
Set-cookie: <token>
```
### Input/output structure
Following proto structure is proposed for API input and output. Latest structure can be looked up in git repository at “etl/sqlparser/sql_requests.proto”

```
// The context in which the query is to be executed. This can be altered by the
// execution of the query. E.g., a "USE db_name;" query can change the database,
// and an "ALTER TABLE table_name ...;" query can change the version, etc. The
// server must respond back with the new context.
message QueryContext {
   // Schema name to use in case statements have empty schema.
   optional string schema = 1 [default = "falcon_default_schema"];
   // DB name to use in case statements have empty db.
  optional string database = 2;
  optional int64 server_schema_version = 3;
}

// A query can be interactive and ask the user for some extra input via a
// prompt. E.g. A query to reshard asks the user whether they want to turn
// the table offline while resharding. The InteractiveQueryQuestion/Answer
// structures are to facilitate this interaction.
message InteractiveQueryQuestion {
  optional string question_id = 1;
  // The banner of the question, i.e. the details that are displayed once
  optional string banner = 2;
  // The prompt to be displayed to the user.
  optional string prompt = 3;
  // If options are present, the user's answer must match one of the values
  // provided.
  repeated string options = 4;
}

message InteractiveQueryAnswer {
  optional string question_id = 1;
  // The answer provided by the user.
  optional string answer = 2;
}

// Options specified by the client that can affect the execution or results of
// the query.
message TqlOptions {
  message QueryOptions {
    message PaginationOptions {
      // Offset to fetch query results from.
      // When only result set row count is requested, then it is interpreted
      // as number of rows after pagination_start.
      optional int64 start = 1 [default = 0];
      // Batch size of a result.
      optional int64 size = 2 [default = 5000000];
    }

    // Limits number of rows returned from the backend server by adding
    // a top condition to the query. This prevents the case where user
    // accidentally issues a select * from T kind of queries that may
    // end up otherwise fetching an extremely large result set into the
    // client when using the default settings of the tool. If a query
    // already has a top condition, then this flag is ignored. To get
    // all results from server i.e., to override this behavior, set
    // value of this flag to 0 or a negative number.
    optional int64 query_results_apply_top_row_count = 1 [default = 50];
    // When true, only displays row counts from query results, otherwise
    // displays results.
    optional bool query_row_count_only = 2 [default = false];
    // Pagination options.
    optional PaginationOptions pagination = 3;
  }

  message FormattingOptions {
    message DateFormat {
      // Format string for date values. Default is yearmonthday e.g.
      // Dec 30th, 2001 is represented as 2001-12-30. System accepts date
      // format specifications supported in strptime datetime library.
      optional string date_format = 1 [default = "%Y-%m-%d"];
      // Format string for datetime values. Default is
      // yearmonthday hour:minute:second e.g. Dec 30th, 2001 1:15:12 is
      // represented as 2001-12-30 01:15:12. System accepts date time
      // format specifications supported in strptime datetime library.
      optional string date_time_format = 2 [default = "%Y-%m-%d %H:%M:%S"];
      // Format string for time values. Default is hour:minute:second
      // System accepts time format specifications supported in strptime
      // datetime library.
      optional string time_format = 3 [default = "%H:%M:%S"];
      // If true, shows date, time and date time as epoch values.
      // Otherwise shows these as strings.
      optional bool format_date_as_epoch = 4 [default = false];
    }
    // Separator between field values of a row
    optional string field_separator = 1 [default = "|"];
    // Separator between rows
    optional string row_separator = 2 [default = "\n"];
    // String to represent null values.
    optional string null_string = 3 [default = "(null)"];
    // Date formatting details
    optional DateFormat date_format = 4;
  }

  message ScriptingOptions {
    // When true, add database name to fully qualify table names,
    // otherwise emit [userschema].[table] for foreign key references.
    optional bool add_database = 1 [default = true];
    // When true, scripts comments otherwise comments are not added to scripts.
    optional bool script_comments = 2 [default = true];
    // When true, scripts extensions specific to our system e.g., fact,
    // dimension, parsing hint etc; otherwise ignores these extensions
    // from the generated script.
    optional bool script_extensions = 3 [default = true];
    // When true, add guid information to generated script. Otherwise
    // guids are omitted from the script.
    optional bool script_guids = 4;
    // When true, add date parsing hints to generated script. Otherwise
    // parsing hints are omitted from the script.
    optional bool script_parsing_hints = 5;
    // When true, add live and max schema version to generated script.
    // Otherwise schema versions are omitted from the script.
    optional bool script_schema_versions = 6;
  }

  message AdvancedOptions {
    // Limits number of rows that are fetched to estimate row size.
    // If zero or negative value is specified, all rows are queried.
    optional int64 input_row_size_fetch_max_rows = 1 [default = 10000];
    // When true, may use jit for queries, otherwise does not jit queryplan.
    optional bool use_jit = 2 [default = true];
    // When true, we skip the falcon results cache.
    optional bool skip_cache = 3;
    // Timeout for commands that report progress. This value overrides
    // the rpc_socket_timeout_sec flag. Commands involving resharding
    // and updating columns are currently affected.
    optional int64 progress_wrapper_timeout_sec = 4 [default = 86400];
    // When true, sets table offline during resharding operations. This
    // value is overridden by user input when user prompts are
    // displayed.
    optional bool offlining_during_resharding_default = 5;
    // If set uses postgres sql parser.
    optional bool use_postgres_sql_parser = 6;
    // If true, thoughtspot system generates guids for objects to be
    // created, otherwise guids are used from sql script specification
    optional bool generate_guids_in_ddl = 7 [default = true];
    // If true, allows certain \"unsafe\" commands to be executed.
    // Specifically if sharding keys are not included in primary key
    // of a table, currently primary key enforcement is not guaranteed
    // by the system. In this case caller if they know that input data
    // has unique rows for primary key, they can override system behavior
    //  to still allow such schema to be generated.
    optional bool allow_unsafe = 8;
    // If true, continues to execute remaining sql statements in input
    // file in case of execution error. Otherwise sql statements
    // execution is terminated.
    optional bool continue_execution_on_error = 9 [default = true];
  }

  optional QueryOptions query_options = 1;
  // If true, shows formatted results as field separated rows.
  // Otherwise shows proto representation of the object.
  optional bool format_output = 2 [default = true];
  optional FormattingOptions formatting_options = 3;
  optional ScriptingOptions scripting_options = 4;
  optional AdvancedOptions adv_options = 5;
}

// Request to be sent to the server.
message ExecuteQueryRequest {
  message Query {
    optional string statement = 1;
    // There might be multiple questions in the flow of the query. Since
    // the server will be stateless, the client must send all the answers
    // to the previous questions as part of the new query in order to get
    // the next question or to have the query executed.
    repeated InteractiveQueryAnswer prompt_responses = 2;
  }
  optional TqlOptions options = 1;
  optional QueryContext context = 2;
  optional Query query = 3;
}

// Response by the server.
message ExecuteQueryResponse {
  message Result {
    message TableResult {
      message ColumnHeader {
        enum Type {
          UNKNOWN = 0;
          VARCHAR = 1;
          DOUBLE = 2;
          FLOAT = 3;
          BOOL = 4;
          INT = 5;
          DATETIME = 6;
          DATE = 7;
          TIME = 8;
          BIGINT = 9;
        }
        optional string name = 1;
        optional Type type = 2;
      }
      message Row {
        // Used "v" instead of "values" to minimize json size.
        repeated string v = 1;
      }
      repeated ColumnHeader headers = 1;
      repeated Row rows = 2;
    }
    message Progress {
      optional string id = 1;
      // There might be progress bars for multiple stages.
      optional string label = 2;
      optional int32 percentage = 3;
      // This can give extra details e.g. 3/8 regions completed.
      optional string details = 4;
    }
    message OutMessage {
      enum Type {
        INFO = 0;
        WARNING = 1;
        ERROR = 2;
      }
      optional Type type = 1;
      optional string value = 2;
    }
    // This might be fully or partially omitted in favor of minimizing response
    // size, if the final context is same as the initial.
    optional QueryContext final_context = 1;
    // Generally, there will be only one question sent at a time, but if the
    // next questions to be asked are the same irrespective of the answer to the
    // first question, then all of them can be asked at once to reduce back and
    // forth calls between client and server.
    repeated InteractiveQueryQuestion interactive_question = 2;
    // Progress of all steps.
    repeated Progress progress = 3;
    // Result of DQL queries will be provided in this.
    optional TableResult table = 4;
    repeated OutMessage message = 5;
    // Indicator of whether query execution has been completed. This is needed
    // as the progress counters might only be available for some intermediate
    // stages in the query.
    optional bool complete = 6;
  }
  // In case of a script request, this can be used by the server to indicate
  // which particular query corresponds to this response.
  optional ExecuteQueryRequest request = 1;
  // This can be used by server in case of a script request to indicate that it
  // has processed the complete script.
  optional bool script_complete = 2;
  optional Result result = 3;
}

// Request to execute a complete script instead of a single query.
message ExecuteSqlScriptRequest {
  enum Type {
        UNKNOWN = 0;
        TQL_SCRIPT = 1;
        PROTO_SCRIPT = 2;
      }
  // Since we do not want the client to have parsing intelligence, it will
  // send the entire script as one string. The server will parse and break the
  // script into commands and execute them one by one.
  // Script can be a sql script or proto script
  optional Type script_type = 1;
  optional TqlOptions options = 2;
  optional QueryContext context = 3;
  optional string script = 4;
}

// The server's response will be an array of query responses - each one
// corresponding to a single query in the script. This can be sent to the
// client in a streaming fashion, so the client can show the query results to
// the user as the script is progressing, instead of waiting for all the queries
// to be done then showing the output at once.
message ExecuteSqlScriptResponse {
  repeated ExecuteQueryResponse responses = 1;
}

message StaticAutocompleteResponse {
  // List of tokens that are specific to the language, e.g. SELECT, WHERE etc.
  repeated string tokens = 1;
}

message DynamicAutocompleteResponse {
  // This can be used in conjunction with the context received from a query to
  // figure out whether the client needs to request for a fresh list of dynamic
  // tokens.
  optional int64 server_schema_version = 1;
  // List of tokens generated from the schema. These are db, table, schema and
  // column names.
  repeated string tokens = 2;
}
```

### Execute

#### API
##### POST request
```
/ts_dataservice/v1/public/tql/query
```
##### Input
###### Request header
```
JSESSIONID=<token>
```
###### Request body
```
{
	"context": {
		"server_schema_version": -1
	},
	"options": {
		"query_options": {
			"pagination": {}
		},
		"formatting_options": {
			"date_format": {}
		},
		"scripting_options": {},
		"adv_options": {
			"skip_cache": true,
			"allow_unsafe": true,
			"continue_execution_on_error": true
		}
	},
	"query": {
		"statement": "show databases;"
	}
}
```
##### Output
```
Status:   200 OK

{
	"result": {
		"final_context": {
			"schema": "falcon_default_schema",
			"database": "",
			"server_schema_version": "163"
		},
		"message": [{
			"type": "INFO",
			"value": "thoughtspot_internal_stats\n"
		}, {
			"type": "INFO",
			"value": "TPCH5K\n"
		}, {
			"type": "INFO",
			"value": "FalconTestUserDataDataBase\n"
		}, {
			"type": "INFO",
			"value": "rls_test\n"
		}, {
			"type": "INFO",
			"value": "geo\n"
		}, {
			"type": "INFO",
			"value": "RDBMS_SNOWFLAKE_46030ea3-ecba-4cbf-a02c-c2ef5d5f29f1_SUPPLYCHAIN_MAIN\n"
		}, {
			"type": "INFO",
			"value": "complex_schema\n"
		}, {
			"type": "INFO",
			"value": "thoughtspot_internal\n"
		}, {
			"type": "INFO",
			"value": "Statement executed successfully. \n"
		}],
		"complete": true
	}
}
```
### Execute file
#### API
##### POST API
###### Multipart file upload API
```
/ts_dataservice/v1/public/tql/script
```
##### Input
###### Request header
```
JSESSIONID=<token>
```
###### Request body
TQL script file is uploaded. Requests will have the flag passing mechanism too.
```
{
	"context": {
		"server_schema_version": "generation id"
	},
	"options": {
		"skip_cache": true,
		"top_row_count": 100
	},
	"script_type": TQL_SCRIPT,
	"script": "show databases;\nshow tables;"
}

```
##### Output
An array of JSON objects will be sent by the server. Same as what is sent for the non-file-upload case - one JSON per tql-command in the script.

### Autocomplete static
#### API
##### GET request
```
/ts_dataservice/v1/public/tql/tokens/static
```
##### Input
###### Request header
```
JSESSIONID=<token>
```
##### Output
```
{
	"tokens": ["abs", "absday", ... ]
}
```
### Autocomplete dynamic
#### API
##### GET request
```
/ts_dataservice/v1/public/tql/tokens/dynamic
```
##### Input
###### Request header
```
JSESSIONID=<token>
```
###### Request body
This API can be improved upon to make it a bit more context sensitive. Context-sensitive completion means that only those tokens which are applicable in current context are returned (only those table names which are in the database).

In the first version, all dynamic tokens are returned. Server side code is written so that the in-memory data-structure lookup is organized in a context-sensitive manner.

##### Output
```
{
	"server_schema_version": "163",
	"tokens": [“table-1”, “col-1”, “col-2”, "start_of_year_epoch", "absolute_month_number", ...]
}
```
### Get schema version
#### API
##### GET request
```
/ts_tqlservice/v1/public/schema_version
```
##### Input
###### Request header
```
JSESSIONID=<token>
```
##### Output
```
{
	"context": {
		"server_schema_version": "generation id"
	}
}
```
### Client
A python client is developed on top of TQL Service APIs. The code is available in the developer git repository. Contact ThoughtSpot for details.

## Related information

[TBD]