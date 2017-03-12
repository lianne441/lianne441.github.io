---
layout: default
title: Blogging Like a Hacker
---

###  MongoDB 数据库

    网站运行需要有大量的数据的读取，同时用户也需要把自己的数据存储到服务器，对于海量数据的操作。
    就需要有专门的软件配合，这个软件就是数据库。

    当前比较流行的数据库，Oracle 甲骨文，SQL server ，这些都是商业数据库。
    但是，开源数据库目前更受青睐。一个是 Mysql , 另一个是 MongoDB 。

    我们课程中采用 MongoDB 数据库。MongoDB 是非关系型数据库，
    传统的关系型数据库的 table （表）和 record （记录），在 MongoDB 这里都有对应的替代物。

### MongoDB 基本概念    

    https://www.mongodb.com/ 是 MongoDB 的官网。
    http://www.mongoing.com/ 是 MongoDB 中文社区。
    http://www.mongodb.org.cn/ 是 MongoDB 中文网。

    MongoDB：是一个数据库软件，有时候我们简称它叫一个数据库，但是其实一个 MongoDB 运行起来
            可以里面同时运行多个数据库
    Database: 数据库。一般做法是，一个项目对应一个数据库。(是上面的子集，可以是多个)
    Collection: 集合。类似于关系型数据库下的表的概念。(是上面的子集，可以是多个)
    Document：文档。一个集合中会包含多个文档。文档对应关系型数据库中的 记录 这个概念。
            (是上面的子集，可以是多个)

    举例子来说，一个项目叫 facebook ，那么我们就建立一个c database 来存储这个项目的所有数据。
    可以创建多个集合，比如 users 。一个 users 集合中，可以包含多个文档，每个文档中存储一个
    user的信息（信息可以有多项：email, name, brithday …）。

    这个是安装的深度公司服务器上的 mongodb。

    $ sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 0C49F3730359A14518585931BC711F9BA15703C6
    $ echo "deb http://repo.mongodb.org/apt/ubuntu trusty/mongodb-org/3.4
    multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.4.list
    $ sudo apt-get update
    $ sudo apt-get install -y mongodb-org

    安装完成后，启动 mongodb

    vim .gitignore　//忽略特定文件或文件夹：项目中有些文件或文件夹不是我们写的代码，
                    例如node_modules。那么我们就没有必要把它们进行版本控制，
                    可以把它们放到项目内一个特殊文件，叫做.gitignore中。可以加快上传速度。

    .gitignore中：
      node_modules
      data

    在后台express-backend中：

    mkdir -p data/db
    mongod --dbpath=./data/db

    这样，mongodb 就启动成功了，启动端口是 27017 。

    现在要进行 Mongodb 数据库操作，我们就开启 Mongo Shell,另起一个命令行窗口：

    $ mongo

    第一步，创建一个数据库

    > use digicity
    switched to db digicity

    查看数据库有没有创建成功，可以用

    > show dbs
    暂时，没有保存数据到该数据库，所以，输出中没有 digicity 。

    第二步，创建集合
    创建集合，集合名称叫 users

    > db.createCollection('users')
    { "ok" : 1 }

    第三步，把一条数据，保存成一条文档（ Document ）

    > db.users.insert({username: 'suiliyan', email: 'suiliyan441@sina.cn' })
    WriteResult({ "nInserted" : 1 })

    输出结果 WriteResult({ "nInserted" : 1 }) 表述成功写入一条数据。

    第四步，列出一个集合中的所有文档：

    > db.users.find({})

###   对数据记录进行增删改查

    第一步，增。

    > db.users.insert({username: 'billie', email: 'billie@billie.com'})
    > db.users.find({})

    第二步，改。

    代码中比较推荐用 save ，不推荐 update。id为需要修改的ＩＤ

     > db.users.update({_id: ObjectId("58c250e4165147ec1bd2b71b")}, {username:
     "billie66", email:"billie@billie.com"})

    update 接口中有两个参考，第一个是查询条件，用来定位要更新的是哪一个文档，后面是更新后的数据。

    第三步，查。

    > db.users.find({})

    可以列出所有的 users 集合中的文档。

    第四步，删。

    删除特定一个文档：

    > db.users.remove({_id:  ObjectId("584b62b830a2a2cbf4c4c3f6")})
    WriteResult({ "nRemoved" : 1 })

    删除集合中所有文档：   

    > db.users.remove({})

    npm i -g mongo-express
    npm list -g mongo-express
