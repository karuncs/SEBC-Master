###### db properties

`
com.cloudera.cmf.db.type=mysql
com.cloudera.cmf.db.host=ip-172-31-36-142.eu-west-2.compute.internal
com.cloudera.cmf.db.name=scm
com.cloudera.cmf.db.user=scm
com.cloudera.cmf.db.setupType=EXTERNAL
com.cloudera.cmf.db.password=Bootcamp

`

###### server logs 

2018-10-19 07:59:26,464 INFO main:com.cloudera.server.cmf.Main: ================================================================================
2018-10-19 07:59:26,480 INFO main:com.cloudera.server.cmf.Main: Starting SCM Server. JVM Args: [-Dlog4j.configuration=file:/etc/cloudera-scm-server/log4j.properties, -Dfile.encoding=UTF-8, -Dcmf.root.logger=INFO,LOGFILE, -Dcmf.log.dir=/var/log/cloudera-scm-server, -Dcmf.log.file=cloudera-scm-server.log, -Dcmf.jetty.threshhold=WARN, -Dcmf.schema.dir=/usr/share/cmf/schema, -Djava.awt.headless=true, -Djava.net.preferIPv4Stack=true, -Dpython.home=/usr/share/cmf/python, -XX:+UseConcMarkSweepGC, -XX:+UseParNewGC, -XX:+HeapDumpOnOutOfMemoryError, -Xmx2G, -XX:MaxPermSize=256m, -XX:+HeapDumpOnOutOfMemoryError, -XX:HeapDumpPath=/tmp, -XX:OnOutOfMemoryError=kill -9 %p], Args: [], Version: 5.14.4 (#3 built by jenkins on 20180707-0445 git: 0971e84bdceb60db9b96533f46451f40ed8cbdf9)


###### Jetty Server

2018-10-19 08:00:28,099 INFO WebServerImpl:org.springframework.web.servlet.DispatcherServlet: FrameworkServlet 'Spring MVC Dispatcher Servlet': initialization completed in 5028 ms
2018-10-19 08:00:28,137 INFO WebServerImpl:com.cloudera.server.web.cmon.JobDetailGatekeeper: ActivityMonitor configured to allow job details for all jobs.
2018-10-19 08:00:30,272 INFO SearchRepositoryManager-0:com.cloudera.server.web.cmf.search.components.SearchRepositoryManager: Initializing SearchTemplateManager:2018-10-19T08:00:30.272Z
2018-10-19 08:00:30,322 INFO SearchRepositoryManager-0:com.cloudera.server.web.cmf.search.components.SearchRepositoryManager: Generating entities:2018-10-19T08:00:30.322Z
2018-10-19 08:00:30,334 INFO SearchRepositoryManager-0:com.cloudera.server.web.cmf.search.components.SearchRepositoryManager: Num entities:209
2018-10-19 08:00:30,334 INFO SearchRepositoryManager-0:com.cloudera.server.web.cmf.search.components.SearchRepositoryManager: Generating documents:2018-10-19T08:00:30.334Z
2018-10-19 08:00:30,362 INFO SearchRepositoryManager-0:com.cloudera.server.web.cmf.search.components.SearchRepositoryManager: Num docs:222
2018-10-19 08:00:30,365 INFO SearchRepositoryManager-0:com.cloudera.server.web.cmf.search.components.SearchRepositoryManager: Constructing repo:2018-10-19T08:00:30.365Z
2018-10-19 08:00:30,433 INFO WebServerImpl:com.cloudera.server.web.cmf.AggregatorController: AggregateSummaryScheduler started.
2018-10-19 08:00:30,816 INFO WebServerImpl:org.mortbay.log: jetty-6.1.26.cloudera.4
2018-10-19 08:00:30,817 INFO WebServerImpl:org.mortbay.log: Started SelectChannelConnector@0.0.0.0:7180
2018-10-19 08:00:30,817 INFO WebServerImpl:com.cloudera.server.cmf.WebServerImpl: Started Jetty server.
2018-10-19 08:00:30,911 INFO SearchRepositoryManager-0:com.cloudera.server.web.cmf.search.components.SearchRepositoryManager: Finished constructing repo:2018-10-19T08:00:30.911Z
2018-10-19 08:00:32,574 INFO ScmActive-0:com.cloudera.server.cmf.components.ScmActive: ScmActive completed successfully.
2018-10-19 08:06:00,749 INFO 1394856988@scm-web-2:com.cloudera.server.web.cmf.CMFUserDetailsService: First user 'admin' logging in.
2018-10-19 08:06:00,802 INFO 1394856988@scm-web-2:com.cloudera.server.web.cmf.AuthenticationSuccessEventListener: Authentication success for user: 'admin' from 90.74.80.112
