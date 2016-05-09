# Getting Started

To start using Relax you should start by configuring the Relax module for operation, then create our Relax DSL for our ReSTful web services. Finally, we can move into the RelaxLogs setup so we can monitor the logs produced by our RESTful service.

## Configuration
Let's open the module's configuration file `ModuleConfig.cfc` and see what we can modify in it. Look for the settings structure, this is the configuration structure for the Relax module and you have some control over it. Below is the default configuration structure:

```javascript
// Relax Configuration Settings
relax = {
    // The location of the relaxed APIs, defaults to models.resources
    APILocation = "models.resources",
    // Default API to load, name of the directory inside of resources
    defaultAPI = "myapi",
    // History stack size, the number of history items to track in the RelaxURL
    maxHistory = 10
};
```


## Relax Logs
RelaxLogs structure settings:

| Setting | Type | Required | Default | Description |
| --- | --- | --- | --- | --- |
| datasource  | srting | true | --- | The datasource registered in the ColdFusion administrator to use for connectivity |
| table | string | true | --- | The database table where all the log entries are located in. |
| adapter | string | true | --- | The adapter to use for talking to the correct database implementation. The available adapters are:<ul><li>mysql</li><li>mssql</li><li>postgres</li><li>oracle</li></ul> |
| maxrows  | numeric | true | 50 | The maximum number of rows to retrieve in the RelaxLogs as paging is provided. |
| bandGap | numeric | true | 3 | The number of pages to display left and right of the paging carrousel when paging is provided. |


> **INFO** To use the RelaxLogs you will need to make some configuration adjustments. Essentially, you need to configure RelaxLogs to work with a database table with columns specified by the LogBox [Database Appender](http://wiki.coldbox.org/wiki/LogBox.cfm#DBAppender). 


