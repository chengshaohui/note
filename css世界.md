# css世界

## 概述

##### 流

> 一种基本的定位和布局机制

## 需提前了解的术语和概念

## 流、元素与基本尺寸

## 盒尺寸四大家族

## 内联元素与流

## 流的破坏与保护

## css世界的层叠规则

## 强大的文本处理能力

## 元素的装饰与美化

## 元素的显示与隐藏

## 用户界面样式

## 流向的改变



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

