**最开始不知道为什么的时候才是最重要的，因为你清楚自己哪里不知道，也知道其他初学者的疑问**

###### 疑惑

1.quartz如何知道什么时候调度。

为什么我加入一个定时任务，他就能准确的执行了呢？cron_expression又是谁解析的呢？如何被解析成准确的时间调度，就是cron表达式是如何被程序理解的，知道我要在下午9点整执行，为什么到了9点整就能执行了呢？



1.1稍微明确之后，再换个问法：是如何监听的？

2.是如何调度的





##### 看了文档之后才知道的一些东西

1.quartz可以在完成job之后通过返回的JobCompletionCode通知成功or失败，来进行其他行动，例如重新执行。

2.通过JDBCJobStore，RAMJobStore来持久化，并且RAMJobStore有个好处是不用拓展数据库。

3.之前的生产双活出现的一起执行定时任务可以通过配置文件解决，可能是因为他支持Load balancing。准确的说是：Quartz’s built-in clustering features rely upon database persistence via JDBCJobStore (described above).