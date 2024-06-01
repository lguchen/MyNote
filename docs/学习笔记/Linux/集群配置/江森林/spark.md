# 导入文件
val f1=sc.textFile("/data/2.txt")   

# flatMap分割，并在flatMap里使用filter过滤标点符号  正则表达式
val f2=f1.flatMap(x=>x.split(" ").filter(x=>x.matches("[A-Za-z]+")))

# 类型转换 元组元素
val f3=f2.map(word=>(word,1)).reduceByKey((a,b)=>a+b)

# 按单词出现次数排序(降序)
f3.sortBy(x=>x._2,false).take(10).foreach(println)

# 去重 并统计不重复单词出现次数
f3.distinct().count()

# 重构 f2  参数与前一个不同的地方是，上面的split(" ")里面为空格，这里不需要空格
val f2=f1.flatMap(x=>x.split("").filter(x=>x.matches("[A-Za-z]+")))
# 重构f3 RDD

val f3=f2.map(word=>(word,1)).reduceByKey((a,b)=>a+b)

# 按单词出现次数排序(降序)
f3.sortBy(x=>x._2,false).take(10).foreach(println)
# 统计字母数量
f2.count()