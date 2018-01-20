开始设置好用户直接重启，本地登录认证都ok，远程认证总是失败，网上找了各种资料，都没有进行说明，找了很久，终于发现一篇文章告诉mongodb3.0认证信息需要修改才能进行连接
修改命令如下，进入shell:

> use admin 
switched to db admin 
>  var schema = db.system.version.findOne({"_id" : "authSchema"}) 
> schema.currentVersion = 3 
3 
> db.system.version.save(schema) 
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 }) 

在修改完成之后再创建用户。http://yrandy.iteye.com/blog/2246780



见
http://jingyan.baidu.com/article/6b97984dbeef881ca2b0bf3e.html
http://www.bubuko.com/infodetail-1153759.html
https://docs.mongodb.com/manual/reference/method/js-user-management/


#单次启动方法
mongod -dbpath "D:\MongoDB\data\db" -logpath D:\MongoDB\Data\log\MongoDB.log --logappend


#注册为服务,并启动安全模式认证  -auth
mongod -dbpath "D:\MongoDB\Data\db" -logpath "D:\MongoDB\Data\log\MongoDB.log" -install -auth -serviceName "MongoDB"

#删除服务
mongod -dbpath "D:\MongoDB\Data\db" -logpath "D:\MongoDB\Data\log\MongoDB.log" -remove -serviceName "MongoDB"

#创建用户，先用非安全模式登陆
#系统管理员
db.createUser(
    {
      user: "root",
      pwd: "233",
      roles: [ "root" ]
    }
)
#数据管理员
use ND
use xxx
db.createUser(
    {
      user: "username",
      pwd: "password",
      roles: [
         { role: "dbAdmin", db: "xxx" },
         { role: "dbOwner", db: "xxx" },
         { role: "read", db: "xxx" },
         { role: "readWrite", db: "xxx" },
         { role: "userAdmin", db: "xxx" }
      ]
    }
)

#连接方法
mongo 10.0.10.87:27017/admin -u root -p 233
mongo 10.0.10.87:27017/ND -u ND -p 233

#若连接失败，考虑端口防火墙

#在连接后登陆
use admin
db.auth('root','233')