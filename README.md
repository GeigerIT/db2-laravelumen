# db2-laravelumen

db2-laravelumen is a fork of Cooperl22/laravel-db2 in order to support Laravel and Lumen v5.2. 
It provides a DB2 Connection by extending the Illuminate Database component working with both Fluent (query builder) and Eloquent.

---

- [Installation](#installation)
- [Registering the Package](#registering-the-package)
- [Configuration](#configuration)
- [Usage](#usage)

## Installation

Ensure you have the proper drivers installed. 
For our AS400 system, I installed iSeriesAccess-7.1.0-1.0.x86_64.rpm from [ibm](http://www-01.ibm.com/support/docview.wss?uid=swg21585490) using alien for our debian distribution and configuring the /etc/odbc.ini and /etc/odbcinst.ini.

Add db2-laravelumen to your composer.json file:

```
"require": {
    "geiger-it/db2-laravelumen": "~3.0"
}
```

Use [composer](http://getcomposer.org) to install this package.

```
$ composer update
```

### Registering the Package

Add the db2-laravelumen Service Provider to your ``bootstrap/app.php``:

```php
$app->register(geiger-it\Database\DB2\DB2ServiceProvider::class);
```

### Configuration

Put your DB2 connection and credential information into your ``config/database.php`` file. You'll notice Lumen does not have a config directory, but will read from it when you create it.

```php

    'ibmi' => [
        'driver'               => 'odbc' / 'ibm',
        'driverName'           => '{IBM i Access ODBC Driver}' / '{iSeries Access ODBC Driver}',
         // General settings
        'host'                 => 'server',
        'username'             => '',
        'password'             => '',
        //Server settings
        'database'             => 'WRKRDBDIRE entry',
        'prefix'               => '',
        'schema'               => 'default schema',
        'signon'               => 3,
        'ssl'                  => 0,
        'commitMode'           => 2,
        'connectionType'       => 0,
        'defaultLibraries'     => '',
        'naming'               => 0,
        'unicodeSql'           => 0,
        // Format settings
        'dateFormat'           => 5,
        'dateSeperator'        => 0,
        'decimal'              => 0,
        'timeFormat'           => 0,
        'timeSeparator'        => 0,
        // Performances settings
        'blockFetch'           => 1,
        'blockSizeKB'          => 32,
        'allowDataCompression' => 1,
        'concurrency'          => 0,
        'lazyClose'            => 0,
        'maxFieldLength'       => 15360,
        'prefetch'             => 0,
        'queryTimeout'         => 1,
        // Modules settings
        'defaultPkgLibrary'    => 'QGPL',
        'defaultPackage'       => 'A/DEFAULT(IBM),2,0,1,0',
        'extendedDynamic'      => 1,
        // Diagnostic settings
        'QAQQINILibrary'       => '',
        'sqDiagCode'           => '',
        // Sort settings
        'languageId'           => 'ENU',
        'sortTable'            => '',
        'sortSequence'         => 0,
        'sortWeight'           => 0,
        'jobSort'              => 0,
        // Conversion settings
        'allowUnsupportedChar' => 0,
        'ccsid'                => 1208,
        'graphic'              => 0,
        'forceTranslation'     => 0,
        // Other settings
        'allowProcCalls'       => 0,
        'DB2SqlStates'         => 0,
        'debug'                => 0,
        'trueAutoCommit'       => 0,
        'catalogOptions'       => 3,
        'libraryView'          => 0,
        'ODBCRemarks'          => 0,
        'searchPattern'        => 1,
        'translationDLL'       => '',
        'translationOption'    => 0,
        'maxTraceSize'         => 0,
        'multipleTraceFiles'   => 1,
        'trace'                => 0,
        'traceFilename'        => '',
        'extendedColInfo'      => 0,
        'options'  => [
            PDO::ATTR_CASE => PDO::CASE_LOWER,
            PDO::ATTR_EMULATE_PREPARES => false,
            PDO::ATTR_PERSISTENT => false
        ]
    ],

```
driver setting is either 'odbc' for ODBC connection or 'ibm' for pdo_ibm connection
Then if driver is 'odbc', database must be set to ODBC connection name.
if driver is 'ibm', database must be set to IBMi database name (WRKRDBDIRE).


## Usage

Consult the [Laravel framework documentation](http://laravel.com/docs).
