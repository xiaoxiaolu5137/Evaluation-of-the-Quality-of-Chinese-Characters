[评价指标](#s1)

# 一、任务简介
### 汉字书写能力是大学生语言文字应用能力的重要组成部分，体现了大学生人文素养。随着信息时代下电脑运用的普及，大学生的汉字书写能力在整体上明显减退，同时高校的书法教学受制于师资数量及评价手段，课后训练和评价反馈不够，这导致学生的书写水平无法得到有效提升。在汉字书写质量评价领域，传统的深度学习方法在提供细粒度、个性化的文本评价方面仍有不足。大语言模型凭借其强大的自然语言理解和生成能力，为解决这一问题提供了新的思路，大语言模型可以根据输入的特征生成详细、个性化的评价意见，模仿人类专家的评价风格。
### “大学生汉字硬笔书写质量自动评价”任务旨在利用多模态大语言模型进行图像理解与文本生成，弥补现有评价方法在提供个性化的细粒度评价与反馈方面的不足，实现从单一的人工评价到个性化智能评价的跨越。本任务包括以下两个子任务：
#### 子任务一：汉字书写质量评级（Handwritten Chinese Characters Grading）
#### 基于给定的汉字图片，对其书写质量进行等级分类。
#### 子任务二：汉字书写质量评语反馈 （Comment Generation of Handwritten Chinese Characters）
#### 基于给定的汉字图片，对其书写质量生成个性化、细粒度的评语与反馈。
# 二、评测数据
## （一）数据集概况
### 本任务使用的汉字书写样本数据均来自本校师范生参与书写训练实践项目所提交的作业。下面分别介绍两个子任务的数据集情况。
#### 子任务一：汉字书写质量评级 
#### 本任务所涉及的书写作业，从性质上看属于汉字书写而并非书法创作，所以仅从书写技法的层面展开评价，使用被社会广泛认可的标准对不同书写水平等级做出客观的描述。因此，本任务将结构与笔画形态作为分级的参照，其中以结构的美感作为重要评判依据，将汉字书写质量分为优秀、中等、不合格三个等级，具体的描述如下：<br>
#### •	优秀：结构比例安排适当，重心平稳，字体匀称美观。点画形态正确且有呼应，笔画清晰到位，用笔有轻重变化之分。字体无明显缺陷。<br>
#### •	中等：结构比例基本合理，重心基本稳定，字体较匀称。笔画形态基本正确，点画清晰但轻重变化不够。字体在某一类或几类问题上存在系统性缺陷。<br>
#### •	不合格：结构比例失衡或重心不稳，字体不匀称。点画随意，笔画不清晰或潦草。字体存在较严重缺点。<br>
#### 汉字的等级类别均由专业书法教师进行人工标注，具体的数量分布如表所示。
等级 | 训练集 | 测试集
 ---- | ----- | ---- 
 优秀  | 500 | 100
 中等  | 500 | 100
 不合格  | 500 | 100
#### 所有汉字图片为jpg格式，像素大小为224 *224。
#### 子任务二：汉字书写质量评语反馈
#### 用笔与结构是书法艺术的两大核心技术，书写水平高的作品往往兼具结构的美和用笔的妙。所以，在硬笔楷书书写质量评语反馈中，本任务针主要对结构和笔画形态两大维度，进行有针对性的评价和描述，具体的评价指标维度如表所示。<br>
![image](https://github.com/xiaoxiaolu5137/Evaluation-of-the-Quality-of-Chinese-Characters/blob/main/%E8%AF%84%E4%BB%B7%E6%8C%87%E6%A0%87%E7%BB%B4%E5%BA%A6.png)
#### 本任务的汉字书写质量评语均由专业书法教师进行人工标注，样本数量为700，将数据集切分为训练集和测试集2个部分，分布情况如表所示。
数据集 | 数量 
 ---- | ----- 
 训练集  | 600 
 测试集  | 100 
## (二)数据集样例
### 本任务标注数据由json格式给出，下面给出具体数据样例。
#### 子任务一：训练数据包含1500个样本，用A、B、C代表汉字书写质量等级，A: 优秀，B: 中等，C: 不合格，图片数据位于路径“Task1\Train”对应的各文件夹。测试数据包含300个#### 样本，位于文件夹“Task1\Test”，参赛队伍将对应测试图片的预测等级写入”task1-answer-submit.json”文件中（请勿修改图片编号），如下所示。
{<br>
    "TEST-001.jpg":"",<br>
    "TEST-002.jpg":"",<br>
    "TEST-003.jpg":"",<br>
    "TEST-004.jpg":"",<br>
    "TEST-005.jpg":""<br>
}
#### 子任务二：训练数据共600个样本，图片位于文件夹“Task2\Train\img“， 其中comments.json文件给出了对应图片的专家评价，样例如下所示。
{<br>
"TRAIN-385.jpg": "左右组合不够合理，左边位置过于偏上。字体重心不稳，向左倾斜。弯钩钩角太向内倾斜，弯钩不舒展。",<br>
"TRAIN-386.jpg": "左右组合不够合理，右边重心偏下。点笔、撇笔形态不合理，竖弯钩弧度不够。",<br>
 "TRAIN-387.jpg": "结构基本合理，点笔过长，倾斜角度不合理，右边笔画间距过大。",<br>
"TRAIN-388.jpg": "结构基本合理，点笔过长，折笔角度偏小，笔画缺少轻重变化。",<br>
"TRAIN-389.jpg": "结构基本合理，左边短撇太短，右边部件太过方正，折笔角度应略小。",<br>
 "TRAIN-390.jpg": "结构基本合理，提笔过长，横笔太短，折笔角度过小，笔画缺少轻重变化。",<br>
 "TRAIN-391.jpg": "结构基本合理，笔画之间缺少穿插避让，撇笔与垂直方向夹角过小，折笔角度过小，笔画缺少轻重变化。",<br>
}
#### 测试数据共100个样本，位于文件夹“Task2\Test\img”，参赛队伍将对应测试图片的生成评语写入”task2-answer-submit.json”文件中（请勿修改图片编号），如下所示。
{<br>
    "TEST-001.jpg":"",<br>
    "TEST-002.jpg":"",<br>
    "TEST-003.jpg":"",<br>
    "TEST-004.jpg":"",<br>
    "TEST-005.jpg":"",<br>
}
 
# 三、评价指标<a id="s1"></a>
#### 子任务1：我们主要关注每一类的Precision（P）、Recall（R）和F1值（F1）三个指标。其中 P = 该类正确预测的样本数/预测为该类的样本数，R = 该类正确预测的样本数/该类样本数，F1 = 2 * P * R / （P + R）。
#### 子任务2：我们主要关注以下几个指标：ROUGE-1、ROUGE-2、ROUGE-L。其中，ROUGE-1=预测结果与参考答案重合的词语个数/参考答案的词语总数， ROUGE-2 = 预测结果与参考答案重合的2-gram个数/参考答案的2-gram总数，ROUGE-L = 最长公共子序列长度/参考答案的总长度。最后，综合得分score= 0.4 * ROUGE-L + 0.3 * ROUGE-2+0.3* ROUGE-1。
# 四、报名事项
#### 1.报名参赛队伍在报名截止之前（2025年04月01日）将[报名表](https://github.com/xiaoxiaolu5137/Evaluation-of-the-Quality-of-Chinese-Characters/blob/main/%E6%AF%94%E8%B5%9B%E6%8A%A5%E5%90%8D%E8%A1%A8.docx)、[承诺书](https://github.com/xiaoxiaolu5137/Evaluation-of-the-Quality-of-Chinese-Characters/blob/main/%E6%89%BF%E8%AF%BA%E4%B9%A6.pdf)(填写完成后的图片)由队伍负责人填写完成后发送至邮箱：zsdlsc@163.com，即可完成报名操作。每位选手只能加入一支队伍，选手需确保报名信息准确有效，组委会有权取消不符合条件队伍的参赛资格及奖励，选手报名、组队变更等操作需要在报名截止之前（2025年04月01日）向zsdlsc@163.com邮箱发送变更信息。
#### 2.请确保报名表中填写的“队伍负责人邮箱”正确且在比赛期间保持正常使用，后续的训练集、数据集等相关文件会在相应的时间点发送至该邮箱。
# 五、时间安排

 流程 | 时间
 ---- | ----- 
 任务征集结束  | 2024年12月31日
 开放报名  | 2025年01月05日（根据官网任务发布时间调整） 
 发布训练集、测试集和评分细则  | 2025年02月10日 
 报名截止  | 2025年04月01日 
 开放提交技术报告与模型  | 2025年05月10日 
  提交技术报告与模型截止  | 2025年05月31日 
   公布获奖名单  | 2025年06月15日 
# 六、奖项设置
### 本次评测将设置一、二、三等奖，将会为本次评测获奖队伍提供荣誉证书及纪念品。
# 七、赛事规则
#### 1.由于版权保护问题，数据集只提供给用户用于本比赛使用，参赛人员不得将数据用于任何商业用途。
#### 2.每名参赛选手只能参加一支队伍，一旦发现某选手以注册多个账号的方式参加多支队伍，将取消相关队伍的参赛资格。
#### 3.数据集的具体内容、范围、规模及格式以最终发布的真实数据集为准。
#### 4.参赛团队需保证提交作品的合规性，若出现下列或其他重大违规的情况，将取消参赛团队的参赛资格和成绩，获奖团队名单依次递补。重大违规情况如下：<br>
a. 使用小号、串通、剽窃他人代码等涉嫌违规、作弊行为。<br>
b. 团队提交的材料内容不完整，或提交任何虚假信息。<br>
c. 参赛团队无法就作品疑义进行足够信服的解释说明。
# 八、组织和联系人
#### 评测组织者：王萌、胡智丹、田娜
#### 任务负责及联系人：卢世聪（江南大学硕士生，zsdlsc@163.com）
#### 评测团队成员：苏晨、曹语婕、王怡文、郭士钦、朱歆怡
# 参考文献：
[1]王开玲.论人工智能在传统书法艺术中的应用与探索[J].江苏教育,2021,(30):7-9.<br>
[2]许兵.基于机器学习的中小学书法评价研究综述及展望[J].江苏教育,2021,(30):17-21.<br>
[3]孙铭蔚.智能书法美学评测算法的研究及应用[D].中南大学,2022.<br>
[4]Rongju Sun, Zhouhui Lian, Yingmin Tang, and Jianguo Xiao. 2015. Aesthetic visual quality evaluation of Chinese handwritings. In Proceedings of the 24th International Conference on Artificial Intelligence (IJCAI'15). AAAI Press, 2510–2516.<br>
[5] 李牧.书法临帖计算机评价的研究[D].华南理工大学,2013.<br>
[6]吴楚洲.书法临帖评价系统研究与实现[D].华南理工大学,2017.<br>
[7]常庆贺,吴敏华,骆力明.基于改进ZS细化算法的手写体汉字骨架提取[J].计算机应用与软件,2020,37(07):107-113.<br>
[8]张子珺.基于深度学习的书法字骨架提取算法研究[D].华东理工大学,2023.<br>
