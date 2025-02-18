# Host Functions

The following is a list of all host functions exported by the W3bstream VM. You can import them into your applets to access the functionalities provided by W3bstream. However, if you're using one of the programming languages supported by the W3bstream SDK, calling these functions directly isn't necessary.

For functions that require it, please note that the allowed values for `chain_id` are:

<table><thead><tr><th width="163">chain_id</th><th>Network</th></tr></thead><tbody><tr><td><code>4690</code></td><td>IoTeX Testnet</td></tr><tr><td><code>4689</code></td><td>IoTeX Mainnet</td></tr><tr><td><code>1</code></td><td>Ethereum Mainnet</td></tr><tr><td><code>5</code></td><td>Ethereum Testnet (Goerli)</td></tr><tr><td><code>137</code></td><td>Polygon Mainnet</td></tr><tr><td><code>80001</code></td><td>Polygon Testnet (Mumbai)</td></tr></tbody></table>

### ws\_log

```go
/**
 Log a message
 Logs a string to the W3bstream console
 
 @param log_level The log level (Trace = 1, Debug, Info, Warn, Error) 
 @param ptr The pointer to the string to be logged
 @param size the length of the string
 @return 0 if no errors.
*/
pub fn ws_log(log_level: i32, ptr: *const u8, size: i32) -> i32;
```

### ws\_get\_data

```rust
/**
 Get event message payload.
 Provides access to the buffer of data attached to the W3bstream event 

 @param resource_id the event id, provided by W3bstream as an argument of the handler function.
 @param return_ptr pointer to the data buffer
 @param return_size is the size in bytes of the data buffer
 @return 0 if no errors.
 */
pub fn ws_get_data(resource_id: i32, return_ptr: *const *mut u8, return_size: *const i32, ) -> i32;




```

### ws\_set\_data

```rust
/**
  Set Event Data.
  Injects modified event data back into the source event for further processing inside W3bstream.
  
  @notice This function is currently not used.
  
  @param resource_id The event ID provided by W3bstream in the _start function.
  @param ptr Pointer to the data buffer.
  @param size Size in bytes of the data buffer.
  @return Returns 0 if the function executes successfully.
*/
pub fn ws_set_data(resource_id: i32, ptr: *const u8, size: i32) -> i32;
```

### ws\_get\_env

```rust
/**
 Get environment
 Gets the value of a W3bstream environment variable
 
 @param ptr is the pointer to the name of the env variable
 @param size is the length of the variable name 
 @param return_ptr is the pointer to the returned value
 @param return_size is the length of the returned value
 @return 0 if there are no errors.
*/
pub fn ws_get_env(ptr: *const u8, size: i32, return_ptr: *const *mut u8, return_size: *const i32, ) -> i32;
```

### ws\_get\_db

```rust
/**
 Read entry from key/value DB
 Gets a serialized object from W3bstream's key/value store.
 
 @param key_ptr is the pointer to the key name you want to fetch
 @param key_size the length of the key name 
 @param return_ptr is the pointer to the fetched data
 @param return_size the size of fetched data
 @return 0 if there are no errors.
*/
pub fn ws_get_db(key_ptr: *const u8, key_size: i32, return_ptr: *const *mut u8, return_size: *const i32, ) -> i32;
```

### ws\_set\_db

```rust
/**
 Store entry to the key/value DB
 Stores a serialized object into W3bstream's key/value DB.
 
 @param key_ptr is the pointer to the key name
 @param key_size the length of the key string
 @param value_ptr is the pointer to the data to store under the specified key name
 @param value_size is the size of the data
 @return 0 if there are no errors.
*/
pub fn ws_set_db(key_ptr: *const u8, key_size: i32, value_ptr: *const u8, value_size: i32, ) -> i32;
```

### ws\_get\_sql\_db

```rust
/**
 Query data from the SQL database
 Executes a query that returns data from W3bstream's SQL database

 @param ptr Pointer to the query string. 
 @param size Length of the query string.
 @param return_ptr Pointer to the returned data.
 @param return_size Size of the returned data.
 @return Returns 0 if the function executes successfully.
*/
pub fn ws_get_sql_db(ptr: *const u8, size: i32, return_ptr: *const *mut u8, return_size: *const i32, ) -> i32;
   
```

### ws\_set\_sql\_db

```rust
/**
 Modify data into the SQL DB
 Executes a query that modifies data inside W3bstream's SQL database

 @param ptr Pointer to the query string. 
 @param size Length of the query string.
 @return Returns 0 if the function executes successfully.
*/    
pub fn ws_set_sql_db(ptr: *const u8, size: i32) -> i32;
```

### ws\_send\_tx

```rust
/**
  Send a blockchain transaction
  Sends a transaction to the specified blockchain network
  
  @param chain_id is the actual blockchain to send the transaction. 
  @param payload_ptr is the pointer to the raw transaction string
  @param size the length of the data
  @return 0 if no errors.
*/
pub fn ws_send_tx(chain_id: i32, payload_ptr: *const u8, payload_size: i32, return_hash_ptr: *const *mut u8, return_hash_size: *const i32, ) -> i32;
```

### ws\_call\_contract

```rust
/**
  Call a contract function
  Calls a ("view" or "pure") contract function on the specified blockchain network  
    
  @param chain_id is the actual blockchain to send the transaction to. 4690 (IoTeX Testnet) is the only supported value by now. 
  @param ptr The pointer to the stringified raw transaction
  @param size the length of the raw transaction string
  @param return_ptr is the pointer to the returned data
  @param return_size is the size of the returned data
  @return 0 if no errors.
*/
pub fn ws_call_contract(chain_id: i32, ptr: *const u8, size: i32, return_ptr: *const *mut u8, return_size: *const i32, ) -> i32;
```

### ws\_submit\_metrics

```rust
/**
  Submit Custom Metrics
  Submit Custom Data Metrics to the Trusted Metrics service.
    
  @param ptr The address in memory where the JSON data is stored (as a string)
  @param size The length of the JSON data
  @return 0 if no errors.
*/
pub fn ws_submit_metrics(ptr: *const u8, size: i32) -> i32;

```
