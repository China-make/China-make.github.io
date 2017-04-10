
## 配置文件

```bash
root@ubuntu75:/etc/nginx/conf.d# tail -3 /etc/kibana/kibana.yml 
server.host: "0.0.0.0"
elasticsearch.url: "http://127.0.0.1:9200"

# 使用search guard会有额外的配置,参考Search Guard笔记

启动kibana
systemctl start kibana.service

tcp    LISTEN     0      128       *:5601                  *:*                   users:(("node",pid=28924,fd=11))
kibana 默认监听5601端口
```

## 问题解决

> kibana Unable to connect to Elasticsearch at https://127.0.0.1:9200.

```bash
如果使用了https需要做如下修改
修改kibana.yml配置，添加elasticsearch.ssl.verify: false

解决方法：
server.host: "0.0.0.0"
elasticsearch.url: "http://127.0.0.1:9200"
```