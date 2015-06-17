## OpenShift Logstash Cartridge

The logstash cartridge allows you to start a version of logstash which can be used to stream, collect all the logs from OPENSHIFT_LOG_DIR (in a pre-defined format) into Doradus. The cartridge monitors the OPENSHIFT_LOG_DIR, tailing the log files, queueing up batches of records and when it either reaches the maximum batch size or when the maximum idle time has elapsed then cartridge would then write the log events to Doradus for enhanced performance reasons.


## Environment Variables

These environment variables are used when configuring Logstash:

 * **`OPENSHIFT_DORADUS_HOST`**: URL of the Doradus hosting server. 
 * **`OPENSHIFT_DORADUS_PORT`**: Port-number of the Doradus service. 
 * **`OPENSHIFT_DORADUS_TENANT`**: Tenant name. 
 * **`OPENSHIFT_DORADUS_USER`**: Tenant User. 
 * **`OPENSHIFT_DORADUS_PWD`**: Tenant Password. 
 * **`OPENSHIFT_APP_NAME`**: Openshift Application Name. 
 * **`OPENSHIFT_NAMESPACE`**: Openshift Namespace. 


## Installation

First add the cartridge to your application followed by configuring the application with the appropriate environment variables as shown below: 

    # Add cartridge
    $ rhc cartridge add -a <your-app-name> https://raw.githubusercontent.com/PiyushMattoo/openshift-log-cartridge/master/metadata/manifest.yml
	
	# Configure environment
    $ rhc env set OPENSHIFT_DORADUS_HOST=abc123-us-east-1.foundcluster.com OPENSHIFT_DORADUS_PORT=1123 OPENSHIFT_DORADUS_TENANT=secret 
	  OPENSHIFT_DORADUS_USER=lucille OPENSHIFT_DORADUS_PWD=agnes OPENSHIFT_APP_NAME=LoggingApplication OPENSHIFT_NAMESPACE=Logspace -a my-app

## Usage

Redirect the application logs to OPENSHIFT_LOG_DIR in the below format and the log will be tailed, loaded into Doradus.

`<ISO 8601 Standard time> <LogLevel> <Log Message>`  
For example: `2015-03-20 11:08:05 INFO Test Message One` 

Doradus REST command to view the logs:

`http://<DoradusHost>:<DoradusPort>/<OPENSHIFT_APP_NAME>/logs_<OPENSHIFT_APP_NAME>_<OPENSHIFT_NAMESPACE></_query?tenant=<DoradusTenant>&q=*`

Doradus Spider documentation can be viewed at:

`https://github.com/dell-oss/Doradus/blob/master/docs/Doradus%20Spider%20Database.pdf`
	
## License

Released under the [Apache License 2.0](http://www.apache.org/licenses/LICENSE-2.0.html).