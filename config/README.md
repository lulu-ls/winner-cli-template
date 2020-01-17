
# 配置文件说明

```
{
  "apps": //配置文件为一个数组,可配置多个项目
   [
    {
      "name": "test", //项目名称
      "cwd": "/project/test", //项目目录
      "script": "bin/www", //项目的启动文件
      "log_date_format": "YYYY-MM-DD HH:mm Z", // 日志日期格式，Z 为时区
      "error_file": "/project/log/testError.log", // 错误日志目录
      "out_file": "/project/log/test.log", // 日志目录
      "pid_file": "/project/pid/test.pid", // 项目pid文件
      "min_uptime": "120s", // 最小运行时间，如果程序在这个时间内退出，会被认为错误，自动重启
      "max_restarts": 8, // 最大的自动重启次数
      "max_memory_restart": "10M", // 重启占用最大内存
      "cron_restart": "1 0 * * *", // 定时重启 （*/30 * * * *）每隔30分钟重启一次，（0 10 9 * * *） 每天9:10重启一次 
      "exec_interpreter": "node", //项目的脚本类型，默认node，可选shell
      "exec_mode": "fork", // 项目的启动方式，默认fork,可选cluster[集群]，若为cluster，可配置instances
      "instances": 4, // 实例个数，如果exec_mode为cluster[集群]，可配置集群实例的个数
      "autorestart": false, // 启用/禁用 项目崩溃或退出时自动重启
      "vizion": false // 启用/禁用 vizion特性(版本控制)
    }
  ]
}
```

## 常用单实例启动

```
[{
    "name": "xxx",
    "script": "xxx.js",
    "cwd": "./bin/",
    "env": {
      "NODE_ENV": "production",
      "NETWORK_ENV": "inner"
    },
    "merge_logs": true,
    "log_date_format":"YYYY-MM-DD HH:mm:ss"
  }]
```
## 常用多实例启动

```
[
  {
    "name": "xxx",
    "script": "xxx.js",
    "cwd": "./bin/",
    "exec_mode": "cluster",
    "instances": 2, // 实例个数
    "env": {
      "NODE_ENV": "production",
      "NETWORK_ENV": "inner"
    },
    "merge_logs": true,
    "log_date_format": "YYYY-MM-DD HH:mm:ss"
  }
]

```
