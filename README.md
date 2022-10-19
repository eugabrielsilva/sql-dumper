# SQLDumper
This is a PHP package designed to generate an **SQL dump from a MySQL database using pure PHP**, without needing to rely on `mysqldump` or other tools.

### Requirements
- PHP version 7.4 or higher with **mysqli** and **mbstring** extensions enabled
- MySQL server and a user with `SHOW` and `SELECT` privileges

### Installation
**Through Composer:**
```
composer require eugabrielsilva/sql-dumper
```

**Manual installation:**\
Copy `src/SQLDumper.php` and include it in your script.

### Usage
```php
// Include Composer packages if not yet
require 'vendor/autoload.php';

// Create SQLDumper instance
$db = new \GabrielSilva\SQLDumper\SQLDumper();

// Set your server settings and connect to the database
$db->host = 'localhost';
$db->user = 'root';
$db->password = '';
$db->db = 'app';
$db->connect();

// Generate dump to an SQL file
$db->dumpToFile('backup.sql');

// You can also dump to a string
$dump = $db->dumpToString();
```

### Options
There are a few options that you can use to modify SQLDumper, these options are properties from the instance that can be overwritten.

**Note:** values shown below are the default ones

```php
$db->port = 3306; // Server port
$db->charset = 'utf8'; // Database charset
$db->includes = []; // Array of tables to include in dump, empty for all
$db->excludes = []; // Array of tables to exclude from dump
$db->createTables = true; // Include CREATE TABLE statements in dump
$db->createDatabase = false; // Include CREATE DATABASE statement in dump
$db->dropTables = false; // Include DROP TABLE statements in dump
$db->dropDatabase = false; // Include DROP DATABASE statement in dump
$db->insertData = true; // Include data in dump
$db->deleteData = false; // Delete data from table before inserting
$db->insertType = 'INSERT'; // Insert type: INSERT, INSERT IGNORE or REPLACE
$db->safeMode = true; // Use IF EXISTS and IF NOT EXISTS clauses in dump
```

### Credits
Library developed and currently maintained by [Gabriel Silva](https://github.com/eugabrielsilva).