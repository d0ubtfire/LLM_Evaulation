# BLiMP语言学概念导读

> 《BLiMP如何测试大模型的英语语法能力》配套附录  
> 面向没有语言学专业背景的读者

BLiMP的题目通常只有两个句子，真正考查的却可能是主谓一致、动词配价、反身代词约束或长距离依存。这个附录不要求读者先掌握一套句法理论，而是把每类现象还原为三个可观察的问题：**句子中哪两个部分发生关系，正负例改变了什么，为什么这一改变会影响可接受性。**

文中的星号“*”表示：按照BLiMP采用的主流美国英语标准，该句被设为不可接受的负例。星号不是说现实中绝不可能听到这种表达，也不等于句子“完全没有意义”。

## 一、先理解BLiMP怎样出题

### 1. 语法可接受性

语法可接受性（grammatical acceptability）是母语者对一个句子能否作为本族语自然表达的判断。它与“能否猜出意思”不同，也不完全等同于是否符合学校语法规范。

> These casseroles **disgust** Kayla.  
> *These casseroles **disgusts** Kayla.

两句都能让人猜到意思；差别在于复数主语 *these casseroles* 要求动词使用 *disgust*，而不是第三人称单数形式 *disgusts*。

### 2. 正例、负例与标准答案

- **正例**：模板按照目标语法规则生成的可接受句。
- **负例**：模板只改变关键条件后生成的不可接受句。
- **标准答案**：数据生成程序根据模板预先写入的正负标签，不是模型自动猜出的标签。

BLiMP又让英语母语者抽样判断，以检验人工判断是否支持这些模板标签。因此，“人工抽样一致率”表示母语者判断与模板标准答案相符的比例，不表示人类做完了全部67,000组题。

### 3. 最小对比对

最小对比对（minimal pair）由一条正例和一条负例组成。两句尽量使用相同词汇和相同结构，只改变决定可接受性的因素。这样，模型若偏向正例，研究者可以较有针对性地解释模型利用了什么语法线索。

“最小”是实验控制目标，不保证每组句子在表面上只差一个词。某些题需要同时调整词形、语序或空位，才能维持目标对立。

### 4. 语言现象、问题模板与测试题

BLiMP分为三个层级：

> **12类语言现象** → **67个问题模板** → **每个模板1,000组测试题**

原论文把一种具体测试类型称为 *paradigm*（范式）。为避免把“理论范式”和“出题类型”混为一谈，正文与本附录统一称为**问题模板**。例如，“主谓一致”是一类语言现象；“规则复数主语与动词的一致”“含关系从句干扰项的一致”是两个不同的问题模板。

### 5. 模型怎样得分

原始BLiMP分别计算正例和负例的整句概率。若模型赋予正例更高的概率，这一组题记1分；否则记0分。这个分数衡量模型能否稳定地区分正负例，不直接说明模型能否说出规则，更不能单独证明模型采用了与人相同的分析过程。

## 二、12类语言现象

### 1. 照应语一致（anaphor agreement）

**普通读者看到的现象：** *herself、himself、themselves* 要与所指的人或事物相配。  
**语言学分析：** 英语反身代词要与先行词在人称、数和传统语法性别特征上保持一致。

> Katherine can't help **herself**.  
> *Katherine can't help **himself**.

这里的反身代词指回 *Katherine*；BLiMP把 *herself* 设为正例。该类只有2个问题模板，分别考查性别一致和数一致。它不等于完整的照应理论；反身代词能否由某个名词短语约束，还要看后文“约束”中的结构条件。

### 2. 论元结构（argument structure）

**普通读者看到的现象：** 有些动词后面必须带宾语，有些不能直接带宾语；不同动词对主语、宾语的语义类型也有要求。  
**语言学分析：** 谓词规定自己可以或必须结合哪些论元，以及这些论元承担何种语义角色。BLiMP也把部分语义选择限制（s-selection）归入这一组。

> Rose wasn't **disturbing Mark**.  
> *Rose wasn't **boasting Mark**.

*disturb*可以直接带宾语，*boast*通常不能按同一结构直接带人名宾语。9个问题模板还涉及及物、不及物、被动、使役—起始交替和论元省略。生成句有时语义生硬；测试重点是动词许可的结构，不是事件是否符合常识。

### 3. 约束（binding）

**普通读者看到的现象：** *himself、herself*不能任意指向句中的任何人。  
**语言学分析：** 反身代词通常必须在适当的局部结构域内，由一个与它匹配且在结构上统领它的先行词约束。BLiMP主要考查约束理论的原则A。

> Carla explained that Samuel discussed **her**.  
> *Carla explained that Samuel discussed **herself**.

若 *herself* 指 *Carla*，二者隔着一个有限从句，超出了该题设定的局部约束域；普通代词 *her* 则可以。7个问题模板分别改变结构统领、格、局部域和移位后的解释位置。它没有系统考查代词与指称表达式对应的原则B、原则C。

### 4. 控制与提升（control and raising）

**普通读者看到的现象：** 一些动词、形容词后的不定式主语虽然没有读出来，却与主句成分有固定关系；形式主语 *there*、*it* 也不是到处都能出现。  
**语言学分析：** 提升结构中的名词短语被分析为从嵌入位置移到更高位置，或形式成分占据该位置；控制结构中的未明说主语则由主句论元确定所指。

> There is **likely** to be a cat outside.  
> *There is **willing** to be a cat outside.

*likely*一类提升谓词可与无具体所指的 *there* 结合；*willing*一类控制谓词要求一个能够“愿意”的有意志主体。5个问题模板使用存在式 *there*、形式 *it* 和 tough结构区分相关句法。它们测的是若干诊断环境，而不是控制与提升的全部类型。

### 5. 限定词—名词一致（determiner–noun agreement）

**普通读者看到的现象：** *this/that*通常配单数名词，*these/those*通常配复数名词。  
**语言学分析：** 指示限定词和中心名词之间存在数特征一致；形容词插入两者之间也不取消这一关系。

> Raymond is selling **this sketch**.  
> *Raymond is selling **this sketches**.

8个问题模板交叉改变限定词、名词、规则或不规则复数，以及中间是否带形容词。它们主要检验局部数一致，不覆盖冠词选择、可数性和限定词语义等更广问题。

### 6. 省略（ellipsis）

**普通读者看到的现象：** 后一句可以省掉已经出现过的名词，但省略部分的内部结构仍受限制。  
**语言学分析：** BLiMP只测试名词短语内部的N-bar省略：数量词后未说出的名词性成分，需要从前文恢复；形容词是否随之省略会改变可接受性。

> Brad passed one **big museum**, and Eva passed several **[big museums]**.  
> *Brad passed one **museum**, and Eva passed several **big [museums]**.

方括号表示听者需要恢复但没有读出的内容。2个问题模板改变形容词位于先行项还是残余项。BLiMP没有覆盖动词短语省略、空缺、替代等其他重要省略现象，因此“省略得分”不能代表模型的全部省略能力。

### 7. 填充语—空位依存（filler–gap dependency）

**普通读者看到的现象：** 疑问词或关系词出现在句子前部时，后面通常要有一个本可放置相应成分的位置。  
**语言学分析：** 前置的填充语与句内未发音的空位形成依存关系；既不能“有填充语而没有空位”，也不能在需要填充语时只留下空位。

> Brett knew **what** many waiters find **__**.  
> *Brett knew **that** many waiters find **__**.

双下划线是分析时标出的空位，不是数据中的可见字符。7个问题模板比较 *wh* 成分和 *that*、主语空位和宾语空位，以及局部和较长距离的依存。它们检测依存是否成对出现；依存能否跨越特殊边界，则由“岛效应”进一步考查。

### 8. 不规则形式（irregular forms）

**普通读者看到的现象：** 英语不规则动词的过去式、过去分词不能只靠统一后缀推导。  
**语言学分析：** 词项需要存储或学习特定的屈折形式，并在定语和谓语环境中选择正确形式。

> The **hidden** offspring aren't confident.  
> *The **hid** offspring aren't confident.

2个问题模板分别考查过去分词作形容词和过去时/过去分词在动词位置的选择。这里的“不规则形式”范围很窄，不包括不规则比较级、派生形态或构词能力。

### 9. 岛效应（island effects）

**普通读者看到的现象：** 疑问词与后面空位可以相隔很远，但并非任何句法成分内部都允许把一部分抽出来。  
**语言学分析：** 某些结构是抽取的“岛”；填充语—空位依存跨越这些边界时，可接受性显著下降。

> Who did Derek hug **__** after shocking Richard?  
> *Who did Derek hug Richard after shocking **__**?

正例的空位是主句动词 *hug* 的宾语；负例试图从 *after* 引导的附加语从句中抽取宾语。8个问题模板还涉及复杂名词短语、并列结构、左分支、句子主语和 *wh* 岛。岛效应常受语境、加工负担和方言影响；二选一模板只能给出受控诊断，不能消除这些理论争议。

### 10. 否定极性项许可（NPI licensing）

**普通读者看到的现象：** *ever、any*等词在否定句、某些疑问句或 *only* 环境中较自然，在普通肯定句中往往不自然。  
**语言学分析：** 否定极性项（negative polarity item, NPI）需要合适的许可成分，而且通常要处在该成分的语义作用域内。

> Teresa had **not ever** sold a movie theater.  
> *Teresa had **probably ever** sold a movie theater.

否定词 *not*许可 *ever*，频率副词 *probably*不提供同样条件。7个问题模板分别操纵否定、矩阵疑问句、*only*及其作用域。NPI许可同时涉及句法、语义和语用；BLiMP的标签体现特定受控语境，不宜解释为所有语境中的绝对规则。

### 11. 量词（quantifiers）

**普通读者看到的现象：** *all、each、no、at most*等数量表达在不同句型中的分布和解释并不相同。  
**语言学分析：** 量词受存在句结构、单调性、作用域和数量表达兼容关系的约束。

> There was **a documentary** irritating Allison.  
> *There was **each documentary** irritating Allison.

英语存在句的名词短语通常表现出“确定性效应”：不定名词短语较自然，*each*一类强量词通常受限。4个问题模板另考查 *all* 与存在句、*no* 与 *fewer than/at most* 的组合。后两类判断带有明显语义和语用成分，不应简单称为词序语法题。

### 12. 主谓一致（subject–verb agreement）

**普通读者看到的现象：** 单数或复数主语要求相应的限定动词形式；主语内部出现另一个名词时，不能被它“带偏”。  
**语言学分析：** 限定动词与句法主语在人称和数特征上保持一致；线性上更近的干扰名词可能造成一致吸引错误。

> A niece of most senators **hasn't** descended most slopes.  
> *A niece of most senators **haven't** descended most slopes.

真正的主语中心语是单数 *niece*，介词短语中的复数 *senators*不是主语。6个问题模板包括规则/不规则复数，以及关系名词和关系从句中的干扰项。BLiMP采用主流美国英语标准；某些非标准变体中的一致形式可能与模板标签不同。

## 三、跨类别常见术语

| 术语 | 简明解释 | 在题目中怎样识别 |
|---|---|---|
| 先行词（antecedent） | 为代词或反身代词提供所指的成分 | 找出 *herself*“指回”谁 |
| 照应语（anaphor） | 依赖句中另一成分确定所指的表达式；BLiMP主要指反身代词 | *himself, herself, themselves* |
| 结构统领（c-command） | 句法树上的结构关系，不等于“在前面”或“离得近” | 主句主语可统领谓语内部成分，嵌在主语内部的名词通常不能反向统领主句宾语 |
| 局部域（local domain） | 反身代词通常必须在其中找到先行词的最小结构范围 | 检查反身代词和先行词是否处在同一局部从句 |
| 论元（argument） | 谓词在意义和句法上选择的参与者 | 谁做事、事情影响谁、动词后是否必须有宾语 |
| 配价/及物性 | 谓词可带多少、哪类论元的结构属性 | *disturb someone*可以，*boast someone*通常不可以 |
| 形式成分（expletive） | 占据句法位置但不指称具体对象的 *there* 或 *it* | *There seems to be…; It seems that…* |
| 填充语（filler） | 出现在依存关系前端、对应后方空位的成分 | 前置的 *who, what, which book* |
| 空位（gap） | 句法上需要、语音上未读出的论元位置 | *What did Pat buy __?* 中 *buy* 后的位置 |
| 抽取（extraction） | 填充语与原位置分离而形成远距离依存的现象 | 疑问词前置、关系词与从句内空位对应 |
| 岛（island） | 限制成分从其内部抽取的结构 | 附加语从句、复杂名词短语、部分并列结构等 |
| 许可成分（licensor） | 使某种受限表达式可以出现的成分 | *not*、某些疑问结构或 *only* 可许可 *ever* |
| 作用域（scope） | 一个运算成分在解释上影响的范围 | *not/only* 是否在结构和意义上覆盖 *ever* |
| 省略先行项 | 为未读出的内容提供恢复依据的已出现表达式 | 前一分句的 *big museum* 帮助理解后一分句的 *several* |
| 一致吸引（agreement attraction） | 非主语名词干扰主谓一致判断 | *the key to the cabinets is/*are* 中的 *cabinets* |

## 四、怎样使用这个附录

阅读正文或题目索引时，可以按以下顺序判断：

1. 先找正负例中真正改变的词形、成分或空位；
2. 再确定这一改变涉及哪两个成分之间的关系；
3. 最后区分它属于局部形式匹配、动词结构要求、长距离依存，还是语义许可条件。

对于争议较大或高度依赖语境的例子，应把BLiMP标签理解为一个受控实验假设，而不是英语使用的最终裁决。若希望逐项查阅67个问题模板，可参见同目录下的《BLiMP 67个问题模板索引》。



[BLiMP 67个问题模板索引](.blimp_67_templates.html)



## 资料来源

1. Warstadt et al. 2020. *BLiMP: The Benchmark of Linguistic Minimal Pairs for English*.  
   https://aclanthology.org/2020.tacl-1.25/
2. BLiMP官方数据、模型结果与人工验证结果。  
   https://github.com/alexwarstadt/blimp
3. BLiMP官方范式补充材料。  
   https://github.com/alexwarstadt/blimp/blob/master/supplemental_materials/BLiMP_Paradigms.pdf

