# temporary save



```properties
#============================================================================
# Configure Main Scheduler Properties  
#============================================================================

org.quartz.scheduler.instanceName = MyClusteredScheduler
org.quartz.scheduler.instanceId = AUTO

#============================================================================
# Configure ThreadPool  
#============================================================================

org.quartz.threadPool.class = org.quartz.simpl.SimpleThreadPool
org.quartz.threadPool.threadCount = 10
org.quartz.threadPool.threadPriority = 5

#============================================================================
# Configure JobStore  
#============================================================================

org.quartz.jobStore.misfireThreshold = 60000

org.quartz.jobStore.class = org.quartz.impl.jdbcjobstore.JobStoreTX
org.quartz.jobStore.driverDelegateClass = org.quartz.impl.jdbcjobstore.StdJDBCDelegate
org.quartz.jobStore.useProperties = false
org.quartz.jobStore.dataSource = qukan3
org.quartz.jobStore.tablePrefix = QRTZ_

org.quartz.jobStore.isClustered = true
org.quartz.jobStore.clusterCheckinInterval = 20000

#============================================================================
# Configure Datasources  
#============================================================================

org.quartz.dataSource.qukan3.driver = com.mysql.jdbc.Driver
org.quartz.dataSource.qukan3.URL = jdbc:mysql://localhost:3306/cloud?autoReconnect=true&useSSL=false&useSSL=false&useUnicode=true&characterEncoding=UTF-8
#org.quartz.dataSource.qukan3.URL = jdbc:mysql://112.74.25.39:3308/cloud?autoReconnect=true&useSSL=false&useSSL=false&useUnicode=true&characterEncoding=UTF-8
org.quartz.dataSource.qukan3.user = root
org.quartz.dataSource.qukan3.password = c54133413402
org.quartz.dataSource.qukan3.maxConnections = 3
org.quartz.dataSource.qukan3.validationQuery=select 0 from dual
```

