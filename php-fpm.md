```

推荐static

pm 设置进程管理器如何管理子进程
    static   子进程数量是固定的 pm.max_children

    ondemand 进程在有需求时才产生(当请求时才启动)
        pm.max_children
        pm.process_idle_timeout
        pm.max_requests

    dynamic   
            子进程的数量在下面配置的基础上动态设置：
                pm.max_children
                pm.start_servers
                pm.min_spare_servers
                pm.max_spare_servers。

pm.max_children (所有模式必填)
    static 时表示创建的子进程的数量
    dynamic 时表示最大可创建的子进程的数量

pm.start_servers:设置启动时创建的子进程数目
    pm 设置为 dynamic 时使用 min_spare_servers + (max_spare_servers - min_spare_servers) / 2。

pm.min_spare_servers:设置空闲服务进程的最低数目
    仅在 pm 设置为 dynamic 时使用。必须设置。

pm.max_spare_servers:设置空闲服务进程的最大数目
    仅在 pm 设置为 dynamic 时使用。必须设置。


pm.process_idle_timeout 秒数，多久之后结束空闲进程
    仅当设置 pm 为 ondemand。 可用单位：s（秒），m（分），h（小时）或者 d（天）。默认单位：10s。

pm.max_requests
    设置每个子进程重生之前服务的请求数,默认为0,不限制


//Reference
https://haydenjames.io/php-fpm-tuning-using-pm-static-max-performance/
https://ma.ttias.be/a-better-way-to-run-php-fpm/
https://www.php.net/manual/zh/install.fpm.configuration.php

```
