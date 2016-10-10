### 常用pm2命令
#### 1. 启动
```
 pm2 start app.js
 pm2 start app.js --name my-api   #my-api为PM2进程名称
 pm2 start app.js -i 0           #根据CPU核数启动进程个数
 pm2 start app.js --watch   #实时监控app.js的方式启动，当app.js文件有变动时，pm2会自动reload
```
#### 2. 查看进程
``` 
 pm2 list
 pm2 show 0 或者 # pm2 info 0  #查看进程详细信息，0为PM2进程id`
```

#### 3. 监控
```
 pm2 monit
```
#### 4. 停止
```
 pm2 stop all  #停止PM2列表中所有的进程
 pm2 stop 0    #停止PM2列表中进程为0的进程
```

#### 5. 重载
```
 pm2 reload all    #重载PM2列表中所有的进程
 pm2 reload 0     #重载PM2列表中进程为0的进程
```

#### 6. 重启
```
 pm2 restart all     #重启PM2列表中所有的进程
 pm2 restart 0      #重启PM2列表中进程为0的进程`
```

#### 7. 删除PM2进程
```
 pm2 delete 0     #删除PM2列表中进程为0的进程
 pm2 delete all   #删除PM2列表中所有的进程
```

#### 8. 日志操作
```
 pm2 logs [--raw]   #Display all processes logs in streaming
 pm2 flush              #Empty all log file
 pm2 reloadLogs    #Reload all logs
```

#### 9. 升级PM2
```
 npm install pm2@lastest -g   #安装最新的PM2版本
 pm2 updatePM2                    #升级pm2
```

### PM2目录结构
默认的目录是：当前用于家目录下的.pm2目录（此目录可以自定义），详细信息如下：
```
$HOME/.pm2                   #will contain all PM2 related files
$HOME/.pm2/logs           #will contain all applications logs
$HOME/.pm2/pids           #will contain all applications pids
$HOME/.pm2/pm2.log    #PM2 logs
$HOME/.pm2/pm2.pid    #PM2 pid
$HOME/.pm2/rpc.sock    #Socket file for remote commands
$HOME/.pm2/pub.sock   #Socket file for publishable events
$HOME/.pm2/conf.js       #PM2 Configuration
```

### 自定义启动文件
```
创建一个test.json的示例文件，格式如下：
{
  "apps":
    {
      "name": "test",
      "cwd": "/data/wwwroot/nodejs",
      "script": "./test.sh",
      "exec_interpreter": "bash",
      "min_uptime": "60s",
      "max_restarts": 30,
      "exec_mode" : "cluster_mode",
      "error_file" : "./test-err.log",
      "out_file": "./test-out.log",
      "pid_file": "./test.pid"
      "watch": false
    }
}

```

