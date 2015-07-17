#RedisMM ---Redis manage and monitor system

##说明
* 系统名称:RedisMM
* 版本：v1.0
* Redis版本：>2.4，小于此版本未经测试。
* 开发工具：lamp+python+jquery 要求python2.7，php5.3以上，低于此版本未经测试。
* 概要:本系统是针对Redis的企业级管理和监控系统，主要功能包括Redis运行状态数据采集、展示、监控、RDB/AOF远程备份、告警等。

##监控及告警
* 监控项：进程状态、性能、资源、库键、主从。后台数据采集，前台有完善的图表展示。
* 告警项：是否可用、连接数、内存、复制状态告警。用户可以配置是否告警、告警阈值、告警接收人、告警间隔、告警方式以及告警的收敛方式。

##配置
+ 后台配置：
```bash
  1)初始化mysql库表。按照sql/init.txt执行。
  2)配置项。monitor/conf/config.ini中配置monitor_server项。
  3)告警接口。monitor/global_functions.py中send_alarm配置您公司的告警接口。
  4)启动。monitor/redisMM_ctl.sh  Usage: ./redisMM_ctl.sh {start|stop|restart|status}
```
+ 前台配置：
```bash
  1)安装lamp配置环境,配置apache并重启 ./apachectl -k restart
  2)配置frontweb/application/config/database.php，同monitor/conf/config.ini中的配置。
```
+ 附apache配置示例：
```bash
  <VirtualHost yourip:port>
    DocumentRoot "/data/redisMM/frontweb"

    ErrorLog /data/ApacheLogs/redisMM_error_log
    CustomLog /data/ApacheLogs/redisMM_access_log

    <Directory /data/redisMM/frontweb>
      Options -Indexes FollowSymLinks
      AllowOverride None
      DirectoryIndex index.html index.php
      Order allow,deny
      Allow from all
    </Directory>
  </VirtualHost>
```

##系统截图
* 进程状态
![image](doc/images/process_status.png)
* 运行状态
![image](doc/images/run_status.png)
* 资源状态
![image](doc/images/resource_monitor.png)
* 键状态
![image](doc/images/key_status.png)
* 备份状态
![image](doc/images/backup_status.png)
* 主备状态
![image](doc/images/master_slave_status.png)
* 冷备
![image](doc/images/coldback.png)
* 内存使用图表
![image](doc/images/mem_use_pic.png)
* 键状态图表
![image](doc/images/key_status_pic.png)
* 键查找图表
![image](doc/images/key_search_pic.png)
* 连接状态图表
![image](doc/images/connections_pic.png)
* 主机管理
![image](doc/images/host_manage.png)
* 告警展示
![image](doc/images/alarm.png)

本系统实际使用中监控近100个实例，运行状态良好。这是本人的第一个开源项目，希望大家多多鼓励支持，并在使用过程中提出宝贵意见，再进行系统的不断优化，谢谢！

##作者
* blythli

