
```bash
root@ubuntu75:~# whereis logstash
logstash: /etc/logstash /usr/share/logstash

root@ubuntu75:~# cd /usr/share/logstash/
root@ubuntu75:/usr/share/logstash# bin/logstash -e 'input{stdin{}}output{stdout{codec=>rubydebug}}'
hello
WARNING: Could not find logstash.yml which is typically located in $LS_HOME/config or /etc/logstash. You can specify the path using --path.settings. Continuing using the defaults
Could not find log4j2 configuration at path /usr/share/logstash/config/log4j2.properties. Using default config which logs to console
09:45:23.163 [LogStash::Runner] INFO  logstash.agent - No persistent UUID file found. Generating new UUID {:uuid=>"a4fa3620-5845-4851-9544-f9385004be25", :path=>"/usr/share/logstash/data/uuid"}
09:45:23.407 [[main]-pipeline-manager] INFO  logstash.pipeline - Starting pipeline {"id"=>"main", "pipeline.workers"=>2, "pipeline.batch.size"=>125, "pipeline.batch.delay"=>5, "pipeline.max_inflight"=>250}
The stdin plugin is now waiting for input:
09:45:23.421 [[main]-pipeline-manager] INFO  logstash.pipeline - Pipeline main started
09:45:23.511 [Api Webserver] INFO  logstash.agent - Successfully started Logstash API endpoint {:port=>9600}
{
    "@timestamp" => 2017-01-20T01:45:23.741Z,
      "@version" => "1",
          "host" => "0.0.0.0",
       "message" => "hello"
}
```

```bash
root@ubuntu75:/etc/logstash/conf.d# /usr/share/logstash/bin/logstash -f /etc/logstash/conf.d/nginx.conf 
Java HotSpot(TM) 64-Bit Server VM warning: INFO: os::commit_memory(0x00000000ca660000, 899284992, 0) failed; error='Cannot allocate memory' (errno=12)
#
# There is insufficient memory for the Java Runtime Environment to continue.
# Native memory allocation (mmap) failed to map 899284992 bytes for committing reserved memory.
# An error report file with more information is saved as:
# /etc/logstash/conf.d/hs_err_pid6848.log
```