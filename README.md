# 数据简介
数据来源自某风电场群的1年SCADA真实运行数据，主要有4个维度信息分别为时间戳、风速、功率和风轮转速，并且给出风机参数说明罗列了各风机的风轮直径、额定功率和风轮转速范围等信息，该数据集从风机实际生产过程中收集，是风机在实际工况条件下运行的典型结果，因此每台风机的原始数据中都包含大量异常数据点，该数据集与风机SCADA系统异常数据检测应用场景相适配。参赛者根据提供的数据集建立无监督聚类模型，识别出SCADA数据中的异常数据。
# 数据说明
数据文件依次为：
文件类别	文件名	文件内容
数据集	dataset.csv	12台风机运行数据文件，无标签
提交样例	submission.csv	仅有三个字段WindNumber\Time\label
数据集中各个字段说明如下：
字段英文名	字段中文名
Time	时间戳
WindSpeed	风速
Power	功率
RotorSpeed	风轮转速
WindNumber	风机编号
风机参数说明如下：
风机编号	风轮直径	额定功率	切入风速	切出风速	风轮转速范围
(m)	(kW)	(m/s)	(m/s)	(r/min)	
1#	99	2000	3	25	8.33-16.8
2#	99	2000	3	25	8.33-16.8
3#	99	2000	3	25	8.33-16.8
4#	99	2000	3	25	8.33-16.8
5#	100.5	2000	3	22	5.5-19
6#	99	2000	3	25	8.33-16.8
7#	99	2000	3	25	8.33-16.8
8#	99	2000	3	25	8.33-16.8
9#	99	2000	3	25	8.33-16.8
10#	99	2000	3	25	8.33-16.8
11#	115	2000	2.5	19	5-14
12#	104.8	2000	3	22	5.5-17
# 提交要求
建议提交方式：
参赛者以csv文件格式提交，提交模型结果到大数据竞赛平台，平台进行在线评分，实时排名。目前平台仅支持单文件提交，即所有提交内容需要放在一个文件中；submission.csv文件字段如下：
字段名	类型	取值范围	字段解释
WindNumber	Int	-	风机编号
Time	Date	-	时间戳
label	Int	{0,1}	是否为异常数据点，1为异常数据
# 提交示例
示例如下：
WindNumber	Time	label
152	2017/11/1 0:10	1
152	2017/11/1 0:20	0
# 评测标准
本赛题采用F1值进行评价，其中对于测试集每台风机计算单独的F1值，最终取各风机的算术平均F1做为评价标准。详细评分算法如下：
（1）求各风机F1值

式中，TP是真样例，FP是假阳例，FN是假阴例，通过以上公式得到该台风机的F1值
（2）求F1平均值

式中，N为风机数量。
