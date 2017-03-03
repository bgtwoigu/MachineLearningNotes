
#Notes

1. Response retrieval：从文档中找出候选回答的句子；
2. Response ranking：从候选中选择最优的；
3. Response triggering：根据阈值判断是否输出 2 中的结果；

选取候选句子时使用了多个feature

总结：
>机器问答聊天方法的思路都是比较固定的，基本就是找候选回答，再进行打分排名，再输出。DocChat相比于之前的直接从QR pairs中抽取回答的方法，最大的好处就是能够使用更多的数据，从而能够找出更好的回答，而对于framework来说，找feature是最重要的一步，DocChat使用了7大类不同层面的feature，最后将他们线性加权组合。这样的模型在未来如果发现有更好的feature，往里面加也是特别容易的，所以在工程层面确实是不错的framework。不可置疑，framework思想简单，但是工作量还是非常大的，毕竟就每个feature来说，提取的工作包括从中训练CNN等模型，而且还得对于不同的数据调整CNN模型的参数等，工作量就已经上去了，何况是7大类共12个feature。当然了，我认为DocChat仅考虑了一轮问答的情况，并且是信息类的问答，这样对于科研做实验确实是比较简单，并且容易对比，但对于一个成熟的机器问答聊天系统，如XiaoIce，用户往往倾向更多的是闲聊，所以真正对做一个可用的系统，还真心不容易。

#Implementations



#Reference

1. <a href="http://blog.csdn.net/john159151/article/details/53240627">CSDN上的论文笔记</a>

