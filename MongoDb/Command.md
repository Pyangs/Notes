#### see http://www.runoob.com/mongodb/mongodb-tutorial.html

#### show 类
##### 数据库
	> show dbs

##### 显示集合
	> show collectiongs



#### 查询
##### find()
	# 按 键-值查找
	> db.set_name.find()
	> db.set_name.find({'type':'cd'})
	# 使用点号，进入复杂结构内部
	> db.set_name.find({'attribute.type':'cd'})
##### 查找一个，即只返回一个
	> findOne()
##### distinct() 返回集合，去重
	> distinct('type')
##### 辅助功能，xx指查询结果
	# 排序
	> xx.sort()
	# 限制条数
	> xx.limit()
	# 跳前面若干条
	> xx.skip()
##### 分组
	# group() 3个参数 key initial reduce
	# 获得集合中任何类型元素的所有唯一标题的列表，如果有相同元素，就组成分组返回：
	> db.set_name.group(
	{
		key:{Title : true},
		initial: {Total : 0},
		reduce : function(items,prev)
		{
		prev.Total += 13;
		}
	}
	) 
##### 条件操作符
	# $gt 大于 
	> attribute:{$gt:2000}
	# $lt 小于
	> attribute:{$lt:2000}
	# $gte 大于等于
	> attribute:{$gte:2000}
	# $lte 小于等于
	> attribute:{$lte:2000}
	# 大于A小于B
	> attribute:{$gt:2000,$lt:2200}
	# $ne 不等于
	> attribute:{$ne:2000}
	# $in 匹配，即in
	> attribute:{$in:[1999,2000,2012]}
	# $nin 反向匹配，即not in
	> attribute:{$nin:[1999,2000,2012]}

	# $size

	# $mod 求余 ，只可对整数数据操作
	> $mod: [2,0] # 偶数
	> $mod: [2,1] # 奇数
	> $mod: [3,0] # 被3整除

	# $or 多个表达式
	> $or :[ExpressionA,ExpressionB....ExpressionX]
	# $slice 类似切片limit()和skip()的结合，传入1或2个参数
	> attribute:{$slice : 3}}#返回前3个
	> attribute:{$slice : -3}}#返回后3个
	> attribute:{$slice : 3，4}}#跳过前3个后返回前4个
	> attribute:{$slice : -4,5}}#跳过后5个后返回前4个

	# $exists 键值存在判断
	# {Author： {$exists:true}} #返回所有有Author键的文档

	# $type 数据类型限制 对应BSON类型代码

	# $not 逻辑取反

##### 正则表达式查询
	> db.media.find({Title:/Matrix*/i})

#### update() 更新
	# 接受参数 criteria,objNew,options
	# criteria 用于查询
	# objNew 更新内容
	# options 是否插入

	# $inc 就地增加 += 
	> {$inc:{'Read':4}}
	# $set 就地改变 =
	> {$set:{'Read':14}}
	# $unset 就地删除
	> {$set:{'Read':14}}
	# $push 给数据增加元素，如果数组不存在就创建，如果不是数据会报错
	> {$push:{Author:'Pyangs'}}
	# $addToSet
	# $pull
	> {$pusl:{Author:'Pyangs'}}
	# $pullAll
	> 
	# $pop
	> {$pop:{Author:1}} # 删除最后一个元素
	> {$pop:{Author:-1}} # 删除第一个元素


#### 聚集命令
##### 文档数目
	> db.set_name.count()

##### 创建固定集合，即有序的集合
	> db.createCollection('collection_name',{capped:true, size:20480, max:100})


#### 辅助功能
##### 检查集合大小
	> db.set_name.validate()


#### 重命名集合
	> db.xx_set.renameCollection('newName')

#### 删除之类
##### 删除数据库
	> db.dropDataBase()

##### 删除集合
	> db.xx_set.drop()

##### 删除文档
	> db.xx_set.remove({Released:{$ne:2000}}) # 删除Released不是2000的文档
	> db.xx_set.remove({}) # 删除全部