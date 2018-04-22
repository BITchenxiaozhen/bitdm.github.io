---
layout: page
mathjax: true
permalink: /2018/projects/p07/midterm/
---

## 项目进展报告

### 数据获取及预处理

本项目采用阿里云天池大数据竞赛所提供的微博用户数据集。天池官方提供两个数据集：测试集和预测集。
- 训练集数据是用户在2015-02-01至2015-07-31时间段发表的微博数据。包括用户标识、博文标识、发表时间、发表一周后的转发数、发表一周后的评论数、发表一周后的赞数、博文内容。博文的全部信息都映射为一行数据，其中对用户做了一定抽样，获取了抽样用户半年的原创博文，对用户标记和博文标记做了加密 发博时间精确到天级别。对数据集简单分析可得到：训练数据共有122,5088条（仅三条内容有缺失值），涉及37251个用户，每个用户至少发一条博文，博文最多数量前十在4909~31015条。
- 测试集数据是用户2015-08-01至2015-08-31时间段内发表的微博数据，包括用户标识、博文标识、发表时间、博文内容，共有17,7923条。我们将会预测测试集中的微博发表一周后转发、评论、点赞的具体数值。

重新对数据进行处理，分别对训练集和预测集进行处理。
- 删除“无用”的用户。因为数据集中存在大量的“无用”的用户，虽然他们看起来比较活跃，会存在微博发表的活跃度特别高，但是对于这部分用户互动（转发、评论、点赞）数平均值为0，并没有与其他的用户产生交互。这类用户很可能属于“僵尸粉”用户，可以直接处理为最低的档位，不用参与模型的预测。对于“无用”的用户，我们可以设置了一些规则将他们过滤掉，比如发表微博数很大，但是总的互动数基本为0的用户。
- 找出测试集中用户没有历史数据的用户集合。找到需要预测的用户之后，我们从训练集中抽取出他们的历史数据，从而进一步发现有1214个用户在训练集中不存在历史数据。对于这部分用户我们有两个方面考虑，一个是直接将他们统一处理为最低的档位；另一方面是根据模型，这个模型是根据用户发表微博的特征维度来考虑，而不结合用户的特征。

### 数据分析与可视化

我们可以简单的统计下每条微博的转发数，然后做图可以看出绝大多数微博的转发数处于比较低的水平(100以内)，服从长尾分布。
- 所有用户总体发表博文一周后的转发数的可视化分布
![long-tailed distributions for all users](https://github.com/ChenDanLu/bitdm.github.io/blob/master/2018/projects/P07/images/figure_1.png)

- 某个用户发表的博文一周后转发数的可视化分布
![ingle user1](https://github.com/ChenDanLu/bitdm.github.io/blob/master/2018/projects/P07/images/figure_13.png)
![ingle user2](https://github.com/ChenDanLu/bitdm.github.io/blob/master/2018/projects/P07/images/figure_7.png)
![ingle user3](https://github.com/ChenDanLu/bitdm.github.io/blob/master/2018/projects/P07/images/figure_3.png)

### 模型选取

> 选择了哪些数据挖掘方法对数据进行分析与挖掘，及选择的理由

### 挖掘实验的结果

> 进行数据挖掘后得到的结果

### 存在的问题

> 到目前为止，遇到哪些问题，及解决方法或思路

### 下一步工作

> 准备如何完成后续的工作