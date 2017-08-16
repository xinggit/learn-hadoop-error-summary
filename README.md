# learn-hadoop-error-summary
All the errors will be accessed here

Study hadoop a year, encountered a lot of mistakes, are summed up, I will move them all to git,A collection of errors is a good way to learn when learning a technique
汇集学习hadoop以来所有遇到的错误

Hope to help you,thanks

--------------------------------------------------------------------------------------------------------------------
java.lang.ClassCastException: class com.sun.jersey.core.impl.provider.entity.XMLJAXBElementProvider$Text
    at java.lang.Class.asSubclass(Class.java:3404)
    at org.apache.hadoop.mapred.JobConf.getOutputKeyComparator(JobConf.java:887)
    at org.apache.hadoop.mapred.MapTask$MapOutputBuffer.init(MapTask.java:1004)
    at org.apache.hadoop.mapred.MapTask.createSortingCollector(MapTask.java:402)
    at org.apache.hadoop.mapred.MapTask.access$100(MapTask.java:81)
    at org.apache.hadoop.mapred.MapTask$NewOutputCollector.<init>(MapTask.java:698)
    at org.apache.hadoop.mapred.MapTask.runNewMapper(MapTask.java:770)
    at org.apache.hadoop.mapred.MapTask.run(MapTask.java:341)
    at org.apache.hadoop.mapred.LocalJobRunner$Job$MapTaskRunnable.run(LocalJobRunner.java:243)
    at java.util.concurrent.Executors$RunnableAdapter.call(Executors.java:511)
    at java.util.concurrent.FutureTask.run(FutureTask.java:266)
    at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1142)
    at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:617)
    at Java.lang.Thread.run(Thread.java:748)
    
    Low-level error, text class error package, it should be in org.apache.hadoop.io.Text
    低级错误，导错包了，应该导org.apache.hadoop.io.Text下的包
 
--------------------------------------------------------------------------------------------------------------------
KeyValueInputFormat Custom delimiter
 
         Configuration conf = new Configuration();
        
        //设置行的分隔符，这里是制表符，第一个制表符前面的是Key，第一个制表符后面的内容都是value  
        //设置属性mapreduce.input.keyvaluelinerecordreader.key.value.separator = 分割符
        //在KeyValueLineRecordReader将调用属性
        conf.set("mapreduce.input.keyvaluelinerecordreader.key.value.separator",",");
        
        Job job = Job.getInstance(conf, "run job");
        
        job.setInputFormatClass(KeyValueTextInputFormat.class);
--------------------------------------------------------------------------------------------------------------------       
java.lang.RuntimeException: java.io.EOFException
        at org.apache.hadoop.io.WritableComparator.compare(WritableComparator.java:165)
        at org.apache.hadoop.mapred.MapTask$MapOutputBuffer.compare(MapTask.java:1268)
        at org.apache.hadoop.util.QuickSort.sortInternal(QuickSort.java:74)
        at org.apache.hadoop.util.QuickSort.sort(QuickSort.java:63)
        at org.apache.hadoop.mapred.MapTask$MapOutputBuffer.sortAndSpill(MapTask.java:1600)
        at org.apache.hadoop.mapred.MapTask$MapOutputBuffer.flush(MapTask.java:1489)
        at org.apache.hadoop.mapred.MapTask$NewOutputCollector.close(MapTask.java:723)
        at org.apache.hadoop.mapred.MapTask.closeQuietly(MapTask.java:2019)
        at org.apache.hadoop.mapred.MapTask.runNewMapper(MapTask.java:797)
        at org.apache.hadoop.mapred.MapTask.run(MapTask.java:341)
        at org.apache.hadoop.mapred.LocalJobRunner$Job$MapTaskRunnable.run(LocalJobRunner.java:243)
        at java.util.concurrent.Executors$RunnableAdapter.call(Executors.java:511)
        at java.util.concurrent.FutureTask.run(FutureTask.java:266)
        at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1142)
        at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:617)
        at java.lang.Thread.run(Thread.java:748)
        Caused by: java.io.EOFException
        at java.io.DataInputStream.readInt(DataInputStream.java:392)
        at com.zx.sorttemperature.KeyPair.readFields(KeyPair.java:57)
        at org.apache.hadoop.io.WritableComparator.compare(WritableComparator.java:158)
        ... 15 more
        
        错误：序列化与反序列号错误，因为不同类型在序列号，反序列时所占字节不同，当同时进行多次反序列，而类型未匹配，就会抛出异常
        所以序列号时一定要调用相应的write（）方法
        
        Error: serialization and anti-sequence number error, because different types in the serial number, anti-sequence when the bytes      are different, when the number of anti-sequence at the same time, and the type does not match, it will throw an exception
     So the serial number must call the corresponding write () method








        
        
        
        
        
        
        
        
        
        
        
        
        
      
