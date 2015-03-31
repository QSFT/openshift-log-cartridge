## OpenShift Logstash Cartridge

The logstash cartridge allows you to start a version of logstash which can be used to stream, collect all the logs from OPENSHIFT_LOG_DIR (in a pre-defined format) into Doradus.


## Environment Variables

These environment variables are used when configuring Logstash:

 * **`OPENSHIFT_DORADUS_HOST`**: URL of the Doradus hosting server. 
 * **`OPENSHIFT_DORADUS_PORT`**: Username to connect as. 
 * **`OPENSHIFT_DORADUS_TENANT`**: Password to connect with. 
 * **`OPENSHIFT_DORADUS_CRDL`**: Base-64 encoded tenant credentials. 


## Installation

First, configure the application with the appropriate environment variables. Then, add the cartridge to your application:

    # Configure environment
    $ rhc set-env --app my-app --env "OPENSHIFT_DORADUS_HOST=abc123-us-east-1.foundcluster.com"
    $ rhc set-env --app my-app --env "OPENSHIFT_DORADUS_PORT=readwrite"
    $ rhc set-env --app my-app --env "OPENSHIFT_DORADUS_TENANT=secret"
	$ rhc set-env --app my-app --env "OPENSHIFT_DORADUS_CRDL=U3VwZXJEb3J5OkFscGhhMQ=="

    # Add cartridge
    $ rhc cartridge add -a your-app-name https://github.com/PiyushMattoo/openshift-log-cartridge/blob/master/metadata/manifest.yml


## License

Released under the [Apache License 2.0](http://www.apache.org/licenses/LICENSE-2.0.html).