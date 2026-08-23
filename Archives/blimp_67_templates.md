# BLiMP 67个问题模板索引

> 《BLiMP如何测试大模型的英语语法能力》配套资料  
> 资料版本：BLiMP官方仓库当前公开的67个数据文件

这份索引回答一个比正文更细的问题：BLiMP所说的“67个问题模板”分别在测什么？每项保留官方UID，便于读者回到原始数据文件核查；中文名称是依据测试对立给出的说明性译名，不是官方另行发布的中文标签。



[BLiMP语言学概念导读](.appendix_blimp_glossary.html)



## 阅读说明

- **样例来源**：每项均列出相应官方JSONL文件的第1组句对，因此可以复核，不是另造例句。星号表示模板设定的不可接受句。程序生成句有时语义生硬；判断重点是目标语法对立。
- **原始参照**：GPT-2成绩来自Warstadt等（2020）的官方结果；“人工抽样一致率”是母语者判断与模板标准答案相符的比例。人工实验只抽取每个模板5组题，每组约20次判断，并非人类完成全部1,000组。
- **分数用途**：这里的分数用于理解BLiMP发布时各模板的难度，不代表2026年头部模型的最新水平。不同提示、计分和题目子集的结果不能直接与它横向排名。
- **分类说明**：官方数据把两个生命度选择模板的字段写作 `s-selection`；原论文和本文将它们归入“论元结构”，因此12类数量仍为2、9、7、5、8、2、7、2、8、7、4、6，共67项。





## 一、照应语一致（2项）

这组题只改变反身代词的性别或数特征，检查它是否与先行词匹配。它测“形式一致”，不等于约束理论的全部内容。

### 1. `anaphor_gender_agreement`｜反身代词的性别一致

- **通俗问题**：指回女性人名时，应选择 *herself* 还是 *himself*？
- **官方样例**：正：*Katherine can't help herself.*　负：\**Katherine can't help himself.*
- **判断依据**：反身代词与先行词 *Katherine* 的传统语法性别特征要一致。
- **解读边界**：该模板使用二元性别词表和人名刻板对应，不能代表非二元代词或真实人物的性别认同。
- **原始参照**：GPT-2 99.4%；人工抽样一致率96.0%。

### 2. `anaphor_number_agreement`｜反身代词的数一致

- **通俗问题**：单数先行词能否与复数反身代词 *themselves* 搭配？
- **官方样例**：正：*Susan revealed herself.*　负：\**Susan revealed themselves.*
- **判断依据**：模板要求单数 *Susan* 与单数 *herself* 一致。
- **解读边界**：当代英语中的单数 *they/themself/themselves* 存在变异；本题采用BLiMP设定的主流美国英语标签。
- **原始参照**：GPT-2 99.2%；人工抽样一致率99.0%。

## 二、论元结构（9项）

论元结构说明一个动词允许或要求哪些参与者，以及这些参与者以什么句法形式出现。前两项还操纵主语或被动施事的语义选择限制。

### 3. `animate_subject_passive`｜被动句施事的生命度选择

- **通俗问题**：被动句 *by* 短语中的成分能否充当该动词的施事？
- **官方样例**：正：*Amanda was respected by some waitresses.*　负：\**Amanda was respected by some picture.*
- **判断依据**：能实施“尊重”行为的是有生命施事，*picture*不符合该语义角色要求。
- **解读边界**：这是语义选择限制，不是所有被动句都要求有生命施事；拟人和特殊语境也会改变判断。
- **原始参照**：GPT-2 76.6%；人工抽样一致率86.0%。

### 4. `animate_subject_trans`｜及物句主语的语义选择

- **通俗问题**：主语能否成为该动词所描述行为的合理发出者？
- **官方样例**：正：*Tina revealed Margaret.*　负：\**The horse revealed Margaret.*
- **判断依据**：模板词库把人类主语与特定认知或交际行为相配，把不符合选择限制的主语设为负例。
- **解读边界**：生命度不是单一充分条件；例句可在故事、拟人或隐喻语境中获得不同接受度。
- **原始参照**：GPT-2 84.9%；人工抽样一致率87.0%。

### 5. `causative`｜使役交替

- **通俗问题**：一个动词能否表示“主语使宾语发生某种变化”？
- **官方样例**：正：*Aaron breaks the glass.*　负：\**Aaron appeared the glass.*
- **判断依据**：*break*可用于“施事使玻璃破裂”的使役结构；*appear*通常不能直接带宾语形成同类结构。
- **解读边界**：该题同时涉及动词词义和句法框架，不能只靠是否“及物”概括全部差别。
- **原始参照**：GPT-2 78.2%；人工抽样一致率98.0%。

### 6. `drop_argument`｜宾语省略许可

- **通俗问题**：动词后原本可出现的宾语，能否在没有上下文时省掉？
- **官方样例**：正：*Travis is touring.*　负：\**Travis is revealing.*
- **判断依据**：模板把可作绝对用法的动词与通常要求明确宾语的动词对比。
- **解读边界**：论元能否省略高度依赖词义和语境；在“秘密已经揭晓”等特定语境中，负例动词可能获得省略读法。
- **原始参照**：GPT-2 80.7%；人工抽样一致率86.9%。

### 7. `inchoative`｜起始式/反使役式

- **通俗问题**：变化动词能否不用施事，只说某物自行进入某种状态？
- **官方样例**：正：*Patricia had changed.*　负：\**Patricia had forgotten.*
- **判断依据**：*change*可形成“某人/物发生变化”的起始式；模板设定中的 *forget* 需要遗忘对象，不能按同一交替分析。
- **解读边界**：部分动词有多义用法；某个读法能否不带宾语，不代表该词所有读法都相同。
- **原始参照**：GPT-2 65.9%；人工抽样一致率82.0%。

### 8. `intransitive`｜不及物框架完整性

- **通俗问题**：句尾结构是否已经满足动词或介词的补足要求？
- **官方样例**：正：*Todd can't yawn.*　负：\**Todd can't walk through.*
- **判断依据**：*yawn*可以单独构成不及物谓语；该模板中的 *walk through* 把 *through* 用作要求后接宾语的介词，句子因缺少补足语而不完整。
- **解读边界**：*through*也可作副词；在支持该读法的语境里，负例的接受度可能提高。
- **原始参照**：GPT-2 84.2%；人工抽样一致率90.0%。

### 9. `passive_1`｜带施事短语的被动许可

- **通俗问题**：一个动词能否形成“主语被某人做某事”的被动句？
- **官方样例**：正：*Lucille's sisters are confused by Amy.*　负：\**Lucille's sisters are communicated by Amy.*
- **判断依据**：可带宾语的 *confuse* 能把宾语提升为被动主语；模板中的 *communicate* 不能按同一及物框架被动化。
- **解读边界**：判断针对给定词义和配价；专业语域中的 *communicate a message* 不等于 *communicate a person*。
- **原始参照**：GPT-2 89.3%；人工抽样一致率95.0%。

### 10. `passive_2`｜不带施事短语的被动许可

- **通俗问题**：去掉 *by* 短语后，过去分词能否独立组成被动谓语？
- **官方样例**：正：*A lot of nieces of some actor aren't scared.*　负：\**A lot of nieces of some actor aren't wept.*
- **判断依据**：*scare*可及物并形成被动；*weep*通常不及物，不能把对象提升为被动主语。
- **解读边界**：表面上的 *be + 分词* 也可能是形容词结构；本模板把它作为动词配价诊断。
- **原始参照**：GPT-2 90.2%；人工抽样一致率86.0%。

### 11. `transitive`｜直接宾语许可

- **通俗问题**：动词后能否直接接一个名词短语宾语？
- **官方样例**：正：*Some turtles alarm Kimberley.*　负：\**Some turtles come here Kimberley.*
- **判断依据**：*alarm*是及物动词；*come here*后不能再按同一结构直接接 *Kimberley*。
- **解读边界**：测试的是直接宾语框架，不是否认不及物动词可带介词短语、方向语或其他附加成分。
- **原始参照**：GPT-2 86.0%；人工抽样一致率99.0%。

## 三、约束（7项）

这组以反身代词为主要诊断材料，考查它的先行词是否满足结构统领、局部性、格和一致等条件。官方名称中的“Principle A”即约束理论原则A。

### 12. `principle_A_c_command`｜原则A与结构统领

- **通俗问题**：反身代词应与主句主语匹配，还是能由嵌在主语内部的名词决定？
- **官方样例**：正：*A lot of patients who can sell some couch didn't investigate themselves.*　负：\**A lot of patients who can sell some couch didn't investigate itself.*
- **判断依据**：主句复数主语 *patients*结构统领宾语反身代词；主语内部的单数 *couch*不能越出关系从句充当其先行词。
- **解读边界**：表面差别表现为数一致，但模板用一致特征来显现潜在的结构统领关系。
- **原始参照**：GPT-2 73.7%；人工抽样一致率86.0%。

### 13. `principle_A_case_1`｜反身代词与主格位置

- **通俗问题**：有限从句的明说主语位置能否直接使用反身代词？
- **官方样例**：正：*The teenagers explain that they aren't breaking all glasses.*　负：\**The teenagers explain that themselves aren't breaking all glasses.*
- **判断依据**：嵌入有限从句需要主格代词 *they*；*themselves*不能在这里独立充当主语。
- **解读边界**：英语口语中的强调性反身代词用法另有条件，不等于本题的普通从句主语。
- **原始参照**：GPT-2 100.0%；人工抽样一致率98.0%。

### 14. `principle_A_case_2`｜非限定结构中的反身形式

- **通俗问题**：*imagine*后的反身成分应进入非限定结构，还是能直接接一个带时态的动词？
- **官方样例**：正：*Eric imagines himself taking every rug.*　负：\**Eric imagines himself took every rug.*
- **判断依据**：*himself*可作为非限定小句 *taking…* 的主语/主句动词的宾格成分；后接过去式 *took* 时需要另一种有限从句结构。
- **解读边界**：该模板把格与有限性一并操纵，不能把分数解释为单独的“反身代词知识”。
- **原始参照**：GPT-2 94.8%；人工抽样一致率96.0%。

### 15. `principle_A_domain_1`｜跨有限从句的局部性

- **通俗问题**：反身代词能否跨过从句边界，指向主句主语？
- **官方样例**：正：*Carla had explained that Samuel has discussed her.*　负：\**Carla had explained that Samuel has discussed herself.*
- **判断依据**：*herself*需要在嵌入从句的局部域内找到合适先行词，不能在这里越过 *Samuel* 指向 *Carla*；普通代词 *her*可以有较远指称。
- **解读边界**：实际约束域的定义受理论分析和结构类型影响；本题只实现一种有限从句对立。
- **原始参照**：GPT-2 98.4%；人工抽样一致率95.0%。

### 16. `principle_A_domain_2`｜局部先行词的数匹配

- **通俗问题**：嵌入从句中的反身代词应与哪个局部主语在数上匹配？
- **官方样例**：正：*Donald can imagine those college campuses are boring themselves.*　负：\**Donald can imagine those college campuses are boring himself.*
- **判断依据**：局部复数主语 *college campuses*要求复数 *themselves*，不能选择与较远单数主语 *Donald*匹配的 *himself*。
- **解读边界**：句子词义较生硬，诊断依赖形式特征和局部结构，不应按常识合理性作答。
- **原始参照**：GPT-2 77.5%；人工抽样一致率75.0%。

### 17. `principle_A_domain_3`｜局部先行词与词序

- **通俗问题**：交换主句和从句中的人名后，反身代词还能否找到局部匹配的先行词？
- **官方样例**：正：*Steven explains Kayla won't hurt herself.*　负：\**Kayla explains Steven won't hurt herself.*
- **判断依据**：正例中局部主语 *Kayla*可约束 *herself*；负例局部主语变成 *Steven*，而较远的 *Kayla*不能跨域约束。
- **解读边界**：模板利用传统性别一致帮助锁定候选先行词，继承了二元性别词表的限制。
- **原始参照**：GPT-2 75.4%；人工抽样一致率82.9%。

### 18. `principle_A_reconstruction`｜移位后的重构

- **通俗问题**：句首反身代词能否在解释时回到句内原位置，从而获得先行词？
- **官方样例**：正：*It's himself that this cashier attacked.*　负：\**It's himself that attacked this cashier.*
- **判断依据**：正例可把前置的 *himself*解释为 *attacked __* 的宾语，并在重构位置受主语约束；负例对应主语空位，缺少同样的局部约束关系。
- **解读边界**：分裂句的自然度和语境会影响判断；该模板只提供一种重构诊断。
- **原始参照**：GPT-2 46.8%；人工抽样一致率78.0%。

## 四、控制与提升（5项）

这组利用无具体所指的 *there/it* 和不定式结构，区分提升谓词与控制谓词；后两项比较tough结构和提升结构。

### 19. `existential_there_object_raising`｜宾语提升与存在式there

- **通俗问题**：动词后能否出现形式成分 *there*，再接 *to be…*？
- **官方样例**：正：*William has declared there to be no guests getting fired.*　负：\**William has obliged there to be no guests getting fired.*
- **判断依据**：模板把允许“宾语提升/ECM”结构的谓词与要求有指称、有语义角色宾语的控制谓词对比；形式 *there*不能承担“被迫者”角色。
- **解读边界**：不同动词的补语选择也参与判断，不能把所有差异归结为 *there* 本身。
- **原始参照**：GPT-2 78.4%；人工抽样一致率89.8%。

### 20. `existential_there_subject_raising`｜主语提升与存在式there

- **通俗问题**：*there*能否占据主句主语位置，而真正的名词短语留在后面？
- **官方样例**：正：*There is soon to be a cat existing.*　负：\**There is willing to be a cat existing.*
- **判断依据**：提升类表达不要求表面主语获得语义角色，形式 *there*可以出现；控制形容词 *willing*要求有意志的主体，不能选择形式主语。
- **解读边界**：正例本身不够自然，较适合当结构诊断，不宜当作推荐写法。
- **原始参照**：GPT-2 91.1%；人工抽样一致率88.0%。

### 21. `expletive_it_object_raising`｜宾语提升与形式it

- **通俗问题**：动词后能否用无具体所指的 *it* 引出 *to be…that…*？
- **官方样例**：正：*Tara would ascertain it to be noteworthy that Kenneth didn't wash.*　负：\**Tara wouldn't entice it to be noteworthy that Kenneth didn't wash.*
- **判断依据**：提升/ECM类谓词可容纳形式 *it*；控制谓词 *entice*要求一个真正能被劝诱的宾语。
- **解读边界**：正负例还更换了谓词和极性，严格说并非只操纵一个表面词形，可能引入词频和搭配差异。
- **原始参照**：GPT-2 79.2%；人工抽样一致率85.7%。

### 22. `tough_vs_raising_1`｜tough结构中的宾语空位

- **通俗问题**：主句主语能否对应不定式中介词后的未读宾语？
- **官方样例**：正：*James is pleasant to flee from.*　负：\**James is apt to flee from.*
- **判断依据**：*pleasant*可进入tough类结构，使 *James*与 *from __* 的空位相关；提升形容词 *apt*要求 *James*是 *flee* 的主语，不能同时解释为 *from* 的宾语。
- **解读边界**：词汇选择会影响自然度；模板测的是两类形容词与空位结构的兼容性。
- **原始参照**：GPT-2 72.0%；人工抽样一致率75.0%。

### 23. `tough_vs_raising_2`｜tough结构与显式宾语冲突

- **通俗问题**：tough类形容词所要求的空位若已被别的名词占据，句子是否仍成立？
- **官方样例**：正：*Every hospital isn't about to tempt Tiffany to reference Matt.*　负：\**Every hospital isn't fun to tempt Tiffany to reference Matt.*
- **判断依据**：*about to*是提升式表达，不要求主语与后层宾语空位对应；*fun to…*的tough分析需要主语与不定式中的空位关联，但句内相关位置已由 *Tiffany/Matt*占据。
- **解读边界**：量词、否定和语义常识使样例较难；应把它看作结构对立，不要只凭句意自然度判断。
- **原始参照**：GPT-2 88.9%；人工抽样一致率81.0%。

## 五、限定词—名词一致（8项）

8项把“限定词的数”“名词的数”“名词是否不规则复数”“中间是否有形容词”组合起来，检查模型是否追踪名词短语内部的一致关系。

### 24. `determiner_noun_agreement_1`｜改变规则名词的数

- **通俗问题**：单数限定词 *this* 后应接单数还是复数名词？
- **官方样例**：正：*Raymond is selling this sketch.*　负：\**Raymond is selling this sketches.*
- **判断依据**：*this*与单数 *sketch*一致。
- **解读边界**：只测指示限定词的数一致，不测冠词和可数性。
- **原始参照**：GPT-2 98.8%；人工抽样一致率95.8%。

### 25. `determiner_noun_agreement_2`｜改变规则限定词的数

- **通俗问题**：单数名词 *committee* 前应使用 *this* 还是 *these*？
- **官方样例**：正：*Some dog stunned this committee.*　负：\**Some dog stunned these committee.*
- **判断依据**：单数中心名词要求单数限定词 *this*。
- **解读边界**：正负例只反映形式数，不涉及“委员会”在英美英语中的集合一致差异。
- **原始参照**：GPT-2 97.7%；人工抽样一致率94.9%。

### 26. `determiner_noun_agreement_irregular_1`｜不规则名词：改变名词形式

- **通俗问题**：复数限定词 *those* 后应使用 *cacti* 还是 *cactus*？
- **官方样例**：正：*Laurie hasn't lifted those cacti.*　负：\**Laurie hasn't lifted those cactus.*
- **判断依据**：*those*要求复数；模板词表把 *cacti*作为 *cactus*的复数。
- **解读边界**：现实词汇可能有多个合法复数，如 *cactuses*；模板只覆盖词库列出的形式。
- **原始参照**：GPT-2 95.7%；人工抽样一致率92.0%。

### 27. `determiner_noun_agreement_irregular_2`｜不规则名词：改变限定词形式

- **通俗问题**：单数 *child* 前应使用 *that* 还是 *those*？
- **官方样例**：正：*All boys boast about that child.*　负：\**All boys boast about those child.*
- **判断依据**：单数名词与单数限定词 *that*一致。
- **解读边界**：不规则性体现在 *child/children* 词项系统中，本组样例的负例直接操纵限定词。
- **原始参照**：GPT-2 95.3%；人工抽样一致率85.0%。

### 28. `determiner_noun_agreement_with_adjective_1`｜形容词介入：改变规则名词

- **通俗问题**：限定词和名词之间有形容词时，数一致是否仍要维持？
- **官方样例**：正：*Rebecca was criticizing those good documentaries.*　负：\**Rebecca was criticizing those good documentary.*
- **判断依据**：复数 *those*要求复数中心名词 *documentaries*；*good*不改变一致关系。
- **解读边界**：形容词在英语中本身通常不显现数，因此真正比较的仍是限定词和中心名词。
- **原始参照**：GPT-2 97.5%；人工抽样一致率95.0%。

### 29. `determiner_noun_agreement_with_adj_2`｜形容词介入：改变限定词

- **通俗问题**：形容词隔开两端后，模型还能根据复数名词选择 *these* 吗？
- **官方样例**：正：*Cynthia scans these hard books.*　负：\**Cynthia scans this hard books.*
- **判断依据**：复数 *books*要求复数限定词 *these*。
- **解读边界**：这是很短的局部依存；高分不代表模型能处理任意长度的一致关系。
- **原始参照**：GPT-2 94.9%；人工抽样一致率96.0%。

### 30. `determiner_noun_agreement_with_adj_irregular_1`｜形容词介入的不规则名词形式

- **通俗问题**：*this lost…* 后应接单数 *foot* 还是复数 *feet*？
- **官方样例**：正：*Some waiters broke this lost foot.*　负：\**Some waiters broke this lost feet.*
- **判断依据**：单数 *this*要求单数不规则名词 *foot*。
- **解读边界**：模板同时要求模型识别不规则词形和跨过形容词的一致关系。
- **原始参照**：GPT-2 92.7%；人工抽样一致率93.8%。

### 31. `determiner_noun_agreement_with_adj_irregular_2`｜形容词介入的不规则限定词形式

- **通俗问题**：单数不规则名词前，即使有形容词隔开，能否使用复数限定词？
- **官方样例**：正：*Alexander didn't walk through that new oasis.*　负：\**Alexander didn't walk through those new oasis.*
- **判断依据**：单数 *oasis*要求单数 *that*。
- **解读边界**：*oasis*的复数形式 *oases*并未在这组负例中出现；题目直接考查限定词选择。
- **原始参照**：GPT-2 94.0%；人工抽样一致率85.0%。

## 六、省略（2项）

BLiMP只覆盖N-bar省略：后一并列分句保留数量词等成分，名词性中心部分不发音，但要从前文恢复。

### 32. `ellipsis_n_bar_1`｜形容词包含在省略先行项中

- **通俗问题**：后半句只说 *many* 时，能否从前文恢复“many rough grocery stores”？
- **官方样例**：正：*Dawn's ex-husband wasn't going to one rough grocery store and Becca wasn't going to many.*　负：\**Dawn's ex-husband wasn't going to one grocery store and Becca wasn't going to many rough.*
- **判断依据**：正例的省略内容可由前文 *rough grocery store*提供；负例把 *rough*只留在省略后的残余位置，前文没有与之平行的含形容词先行结构。
- **解读边界**：自然语境可能改善某些残余形容词读法；模板实现的是特定平行性假设。
- **原始参照**：GPT-2 91.5%；人工抽样一致率92.0%。

### 33. `ellipsis_n_bar_2`｜前后形容词对照与省略

- **通俗问题**：后一名词短语保留新形容词时，中心名词能否省略？
- **官方样例**：正：*A friend of Pamela hasn't attacked one person and Ann hasn't attacked more unsure person.*　负：\**A friend of Pamela hasn't attacked one unemployed person and Ann hasn't attacked more unsure.*
- **判断依据**：模板把完整的 *unsure person*与形容词残余 *unsure*对比，后者缺少可按设定恢复的合适名词性结构。
- **解读边界**：官方首条正例本身较生硬，人工抽样一致率也只有78%；本项应视为数据质量较弱的诊断，而非无争议规则。
- **原始参照**：GPT-2 87.2%；人工抽样一致率78.0%。

## 七、填充语—空位依存（7项）

这组检查 *wh* 成分与句内空位是否同时出现。`with_gap`表示句内存在未读论元位置，`no_gap`表示相应论元位置已被明说成分占据；`long_distance`表示依存跨越更深的从句结构。

### 34. `wh_questions_object_gap`｜宾语位置的填充语—空位配对

- **通俗问题**：关系/疑问成分出现后，动词宾语位置还应不应该再出现一个完整名词短语？
- **官方样例**：正：*Joel discovered the vase that Patricia might take.*　负：\**Joel discovered what Patricia might take the vase.*
- **判断依据**：正例中 *that*对应 *take __* 的宾语空位；负例已有 *what*作填充语，却又把 *the vase*填回宾语位置，因而没有可对应的空位。
- **解读边界**：样例混合关系从句和嵌入问句表面形式，重点是填充语与宾语空位是否成对出现。
- **原始参照**：GPT-2 84.2%；人工抽样一致率85.0%。

### 35. `wh_questions_subject_gap`｜局部主语空位

- **通俗问题**：关系成分对应从句主语空位时，能否再明说另一个主语？
- **官方样例**：正：*Brian had questioned an association that can astound Diana.*　负：\**Brian had questioned who an association can astound Diana.*
- **判断依据**：正例中关系词 *that*对应 *can astound Diana* 的主语空位；负例加入 *who*后，从句已有明说主语 *an association*，没有相应空位。
- **解读边界**：句子类型的词义搭配不自然，诊断应聚焦从句主语位置是否空缺。
- **原始参照**：GPT-2 95.6%；人工抽样一致率98.0%。

### 36. `wh_questions_subject_gap_long_distance`｜长距离主语空位

- **通俗问题**：当前置成分跨过更复杂结构时，后方是否仍必须保留与它对应的主语空位？
- **官方样例**：正：*Dennis has seen this tooth that Kristin wasn't concealing that is astounding men.*　负：\**Dennis has seen who this tooth that Kristin wasn't concealing is astounding men.*
- **判断依据**：正例的关系结构为前置成分保留了主语空位；负例中的 *who*与后面已经出现的主语成分冲突，缺少可对应空位。
- **解读边界**：多层关系从句增加了加工负担；错误可能来自依存追踪，也可能来自句子复杂度。
- **原始参照**：GPT-2 87.1%；人工抽样一致率84.9%。

### 37. `wh_vs_that_no_gap`｜无空位时选择that

- **通俗问题**：嵌入从句中主语、宾语都已出现时，应使用陈述补语标记 *that* 还是疑问词 *who*？
- **官方样例**：正：*Mark figured out that most governments appreciate Steve.*　负：\**Mark figured out who most governments appreciate Steve.*
- **判断依据**：正例是成分完整的陈述补语；负例加入 *who*，但 *appreciate*的宾语已由 *Steve*占据，没有空位供 *who*解释。
- **解读边界**：该题不是一般比较 *who*和 *that*，而是比较它们与“有无空位”的组合。
- **原始参照**：GPT-2 96.8%；人工抽样一致率97.0%。

### 38. `wh_vs_that_no_gap_long_distance`｜长结构中无空位时选择that

- **通俗问题**：从句更长时，模型能否确认所有论元位置都已填满，从而拒绝多余的 *who*？
- **官方样例**：正：*Every association figured out that most drivers that forfeit investigated Irene.*　负：\**Every association figured out who most drivers that forfeit investigated Irene.*
- **判断依据**：*investigated*已有主语 *drivers*和宾语 *Irene*；*who*没有空位可以对应，*that*才与完整陈述补语相容。
- **解读边界**：关系从句 *that forfeit*是距离干扰项，不是目标依存的一部分。
- **原始参照**：GPT-2 93.8%；人工抽样一致率91.9%。

### 39. `wh_vs_that_with_gap`｜有空位时选择wh成分

- **通俗问题**：嵌入动词缺少宾语时，应使用能与空位对应的 *who*，还是普通补语标记 *that*？
- **官方样例**：正：*A lady has remembered who the actors conceal.*　负：\**A lady has remembered that the actors conceal.*
- **判断依据**：正例中 *who*对应 *conceal __* 的宾语空位；*that*本身不提供被隐瞒对象，负例留下未获许可的缺项。
- **解读边界**：部分动词在特定语境下允许宾语省略；模板选择的词义按需要宾语处理。
- **原始参照**：GPT-2 55.1%；人工抽样一致率77.0%。

### 40. `wh_vs_that_with_gap_long_distance`｜长结构中有空位时选择wh成分

- **通俗问题**：空位与填充语相隔更远时，模型能否持续追踪二者关系？
- **官方样例**：正：*Kayla concealed who a lot of guests that were scaring many people complain about.*　负：\**Kayla concealed that a lot of guests that were scaring many people complain about.*
- **判断依据**：*who*对应句尾介词 *about __*的宾语空位；*that*不能为这个缺失宾语提供内容。
- **解读边界**：长距离和介词滞留同时出现，低分不能唯一归因于某一个因素。
- **原始参照**：GPT-2 56.3%；人工抽样一致率74.7%。

## 八、不规则形式（2项）

这组要求模型区分不规则动词的过去式和过去分词；一项把分词放在名词前作定语，另一项放在谓语位置。

### 41. `irregular_past_participle_adjectives`｜不规则过去分词作定语

- **通俗问题**：名词前表达“被隐藏的”时，应使用 *hidden* 还是过去式 *hid*？
- **官方样例**：正：*The hidden offspring aren't confident.*　负：\**The hid offspring aren't confident.*
- **判断依据**：定语位置需要过去分词 *hidden*；*hid*是过去式，不能直接承担该功能。
- **解读边界**：测试词表中的特定不规则形式，不等于开放词汇上的形态生成能力。
- **原始参照**：GPT-2 97.7%；人工抽样一致率99.0%。

### 42. `irregular_past_participle_verbs`｜谓语中的过去式/分词选择

- **通俗问题**：没有助动词时，过去时谓语应使用 *wore* 还是分词 *worn*？
- **官方样例**：正：*The Borgias wore a lot of scarves.*　负：\**The Borgias worn a lot of scarves.*
- **判断依据**：简单过去时需要限定形式 *wore*；*worn*通常需要与 *have/be*等助动词结合。
- **解读边界**：模板主要检验词形和局部助动词环境，容易受到高频搭配线索帮助。
- **原始参照**：GPT-2 86.1%；人工抽样一致率95.0%。

## 九、岛效应（8项）

岛效应限制填充语从某些结构内部与空位建立依存。每项通常让正例把空位放在允许抽取的位置，让负例把空位移入受限制区域，或违反并列结构的平行抽取条件。

### 43. `adjunct_island`｜附加语岛

- **通俗问题**：疑问词能否从 *after…* 附加语从句内部抽出？
- **官方样例**：正：*Who should Derek hug after shocking Richard?*　负：\**Who should Derek hug Richard after shocking?*
- **判断依据**：正例的 *who*对应主句 *hug __* 的宾语；负例试图对应附加语 *after shocking __* 中的空位，跨越附加语岛。
- **解读边界**：两句的论元位置同时调整；分数也可能受动词后是否已有宾语影响。
- **原始参照**：GPT-2 89.4%；人工抽样一致率94.0%。

### 44. `complex_NP_island`｜复杂名词短语岛

- **通俗问题**：疑问词能否从含关系从句的复杂名词短语内部抽出？
- **官方样例**：正：*Who aren't most hospitals that hadn't talked about most waitresses alarming?*　负：\**Who aren't most waitresses alarming most hospitals that hadn't talked about?*
- **判断依据**：正例让 *who*对应主句 *alarming __* 的空位；负例把空位放进修饰 *hospitals* 的关系从句 *talked about __*，形成复杂名词短语岛违规。
- **解读边界**：官方首条句子极其生硬，人工一致率仅80.4%；读者应按结构位置而非句意自然度理解。
- **原始参照**：GPT-2 72.2%；人工抽样一致率80.4%。

### 45. `coordinate_structure_constraint_complex_left_branch`｜并列结构中的跨项与左分支限制

- **通俗问题**：前置成分能否同时对应两个并列分句中的空位，而只抽出限定成分、把名词留在原位是否可行？
- **官方样例**：正：*What senators was Alicia approaching and some teachers scaring?*　负：\**What was Alicia approaching senators and some teachers scaring?*
- **判断依据**：正例按模板让完整 *what senators*与并列项中的相应位置形成平行依存；负例只前置 *what*、留下 *senators*，破坏左分支和并列结构条件。
- **解读边界**：该模板叠加两种限制，不能用分数分别估计“左分支”与“并列约束”的贡献。
- **原始参照**：GPT-2 81.0%；人工抽样一致率90.0%。

### 46. `coordinate_structure_constraint_object_extraction`｜并列结构的跨项抽取

- **通俗问题**：从并列结构抽取宾语时，是否必须在两个并列项中都留下对应空位？
- **官方样例**：正：*Who were all men and Eric leaving?*　负：\**Who were all men leaving and Eric?*
- **判断依据**：正例按跨项抽取分析，让 *who*与并列谓语中的平行空位对应；负例只从一个并列项抽取，另一项保留 *Eric*，违反并列结构约束。
- **解读边界**：生成句的时态和协调结构不够自然，可能放大加工难度。
- **原始参照**：GPT-2 85.4%；人工抽样一致率90.9%。

### 47. `left_branch_island_echo_question`｜回声问句中的左分支抽取

- **通俗问题**：询问“谁的地毯”时，能否只把 *whose*移到句首而把 *rug*留在原位？
- **官方样例**：正：*Irene had messed up whose rug?*　负：\**Whose had Irene messed up rug?*
- **判断依据**：英语通常不允许只从名词短语中抽出所有者成分 *whose*；回声问句可把完整 *whose rug*留在原位。
- **解读边界**：正例是回声问句，不是普通信息问句；语境和语调对其自然度很重要。
- **原始参照**：GPT-2 52.3%；人工抽样一致率91.0%。

### 48. `left_branch_island_simple_question`｜普通问句中的左分支抽取

- **通俗问题**：普通疑问句应前置完整的 *whose museums*，还是只前置 *whose*？
- **官方样例**：正：*Whose museums had Dana alarmed?*　负：\**Whose had Dana alarmed museums?*
- **判断依据**：完整名词短语可以前置；只抽出其左侧限定成分、把中心名词留在原位通常不可接受。
- **解读边界**：该限制具有明显跨语言差异，不能从英语结果推断其他语言的所有者疑问结构。
- **原始参照**：GPT-2 87.1%；人工抽样一致率99.0%。

### 49. `sentential_subject_island`｜句子主语岛

- **通俗问题**：能否从充当主语的动名词结构内部抽出宾语？
- **官方样例**：正：*Who had the patients' cleaning those banks upset.*　负：\**Who had the patients' cleaning upset those banks.*
- **判断依据**：正例让 *who*对应主句 *upset __* 的宾语；负例试图从主语成分 *the patients' cleaning __* 内部抽取，而主句宾语由 *those banks*占据。
- **解读边界**：人工抽样一致率仅60.6%，是BLiMP中质量警报最明显的模板之一；标签不宜当作稳固的人类共识。
- **原始参照**：GPT-2 35.5%；人工抽样一致率60.6%。

### 50. `wh_island`｜wh从句岛

- **通俗问题**：一个疑问成分能否跨过另一个 *wh* 从句边界与内部空位相连？
- **官方样例**：正：*Who have those men revealed they helped?*　负：\**Who have those men revealed who helped?*
- **判断依据**：正例跨过普通陈述补语建立宾语依存；负例让依存进入由另一个 *who*引导的从句，触发 *wh* 岛限制。
- **解读边界**：负例的角色分配和空位位置较难解析，低分可能同时反映歧义与加工负担。
- **原始参照**：GPT-2 78.9%；人工抽样一致率73.0%。

## 十、否定极性项许可（7项）

这组以 *ever* 为主要否定极性项。题目既检查句中有没有许可成分，也检查许可成分是否在结构和意义上覆盖 *ever*。

### 51. `matrix_question_npi_licensor_present`｜矩阵一般疑问句许可ever

- **通俗问题**：句子采用一般疑问句语序时，*ever*是否比在普通肯定陈述句中自然？
- **官方样例**：正：*Had Bruce ever played?*　负：\**Bruce had ever played.*
- **判断依据**：矩阵疑问环境可许可 *ever*；无否定、无疑问的肯定陈述句通常不能。
- **解读边界**：负例在特殊语境中可能出现；模板默认无额外语境的普通读法。
- **原始参照**：GPT-2 65.4%；人工抽样一致率98.0%。

### 52. `npi_present_1`｜无许可环境中的ever：副词对照一

- **通俗问题**：没有否定或疑问时，普通副词 *really*与NPI *ever*哪一个可出现？
- **官方样例**：正：*Even Suzanne has really joked around.*　负：\**Even Suzanne has ever joked around.*
- **判断依据**：*even*在该结构中不按模板许可 *ever*，普通程度副词 *really*不受此限制。
- **解读边界**：句中的 *even*可能让读者误以为它与 *ever*总能组合；本题正是检验具体许可条件。
- **原始参照**：GPT-2 64.8%；人工抽样一致率83.0%。

### 53. `npi_present_2`｜无许可环境中的ever：副词对照二

- **通俗问题**：普通肯定句中，*ever*能否替代普通副词？
- **官方样例**：正：*Tamara really exited those mountains.*　负：\**Tamara ever exited those mountains.*
- **判断依据**：负例缺少否定、疑问或其他合适许可成分。
- **解读边界**：正例的动词搭配生硬，但目标对立是 *really/ever* 的分布，不是地点表达是否自然。
- **原始参照**：GPT-2 64.3%；人工抽样一致率98.0%。

### 54. `only_npi_licensor_present`｜only对ever的许可

- **通俗问题**：*only*和 *even*都放在主语前时，哪一个能许可后面的 *ever*？
- **官方样例**：正：*Only Bill would ever complain.*　负：\**Even Bill would ever complain.*
- **判断依据**：排他成分 *only*在该结构中提供适当的语义环境；*even*不提供同样许可。
- **解读边界**：NPI许可不是看到某个关键词即可；位置、作用域和句子意义共同参与。
- **原始参照**：GPT-2 94.5%；人工抽样一致率92.0%。

### 55. `only_npi_scope`｜only与ever的作用域

- **通俗问题**：句中虽然有 *only*，它是否位于能够覆盖 *ever*的位置？
- **官方样例**：正：*Only the grandsons of the Impressionists who Colleen is appreciating ever encourage Phillip to stretch.*　负：\**The grandsons of the Impressionists who only Colleen is appreciating ever encourage Phillip to stretch.*
- **判断依据**：正例的 *only*修饰整个主语并对后面的 *ever*取得许可作用域；负例的 *only*嵌在主语内部关系从句中，不能向外许可主句 *ever*。
- **解读边界**：句子很长，模型可能依赖 *only*与 *ever*的距离，而非真正计算结构作用域。
- **原始参照**：GPT-2 78.5%；人工抽样一致率72.0%。

### 56. `sentential_negation_npi_licensor_present`｜句子否定许可ever

- **通俗问题**：*ever*前需要否定词 *not*，还是普通副词 *probably*也可以？
- **官方样例**：正：*Teresa had not ever sold a movie theater.*　负：\**Teresa had probably ever sold a movie theater.*
- **判断依据**：句子否定 *not*许可NPI *ever*；*probably*不具有同样性质。
- **解读边界**：这是局部、词汇标记明显的对立，高分可能部分来自高频搭配 *not ever*。
- **原始参照**：GPT-2 97.1%；人工抽样一致率92.8%。

### 57. `sentential_negation_npi_scope`｜否定与ever的跨从句作用域

- **通俗问题**：句中出现 *not* 就够了吗，还是它必须在结构上覆盖 *ever*？
- **官方样例**：正：*The associations that had worried Cynthia have not ever planned to shock every actress.*　负：\**The associations that had not worried Cynthia have ever planned to shock every actress.*
- **判断依据**：正例的主句否定覆盖主句 *ever*；负例的 *not*被关在主语关系从句中，不能向外许可主句NPI。
- **解读边界**：词序距离与句法作用域在此同向变化，需要额外实验排除纯距离策略。
- **原始参照**：GPT-2 73.2%；人工抽样一致率81.0%。

## 十一、量词（4项）

前两项考查存在句中名词短语的量词限制；后两项考查 *no* 与带最高级意义的数量边界表达之间的兼容性。后者包含较强语义—语用判断。

### 58. `existential_there_quantifiers_1`｜存在句中的a与each

- **通俗问题**：存在句 *there be* 后，普通不定名词短语与 *each*量词短语哪一个更自然？
- **官方样例**：正：*There was a documentary about music irritating Allison.*　负：\**There was each documentary about music irritating Allison.*
- **判断依据**：英语存在句通常允许不定名词短语，而 *each*一类强量词受“确定性效应”限制。
- **解读边界**：特殊列举或对比语境可能改变接受度；模板默认中性语境。
- **原始参照**：GPT-2 99.5%；人工抽样一致率94.0%。

### 59. `existential_there_quantifiers_2`｜存在句中的all

- **通俗问题**：*all*量词短语能否直接放在存在式 *there* 后？
- **官方样例**：正：*All convertibles weren't there existing.*　负：\**There weren't all convertibles existing.*
- **判断依据**：模板把 *all convertibles*置于普通量词主语位置设为正例，把它置于存在句后名词短语位置设为负例。
- **解读边界**：正例非常不自然，人工一致率仅76.4%，GPT-2也低于随机水平；这一项不适合被当作干净的单因素量词测试。
- **原始参照**：GPT-2 42.4%；人工抽样一致率76.4%。

### 60. `superlative_quantifiers_1`｜no与数量上界表达一

- **通俗问题**：否定量词 *no* 后的谓语中，*fewer than two*与 *at most two*是否同样容易获得一致解释？
- **官方样例**：正：*No girl attacked fewer than two waiters.*　负：\**No girl attacked at most two waiters.*
- **判断依据**：模板依据广义量词和单调性分析，把 *no + fewer than*设为可接受组合，把 *no + at most*设为不相容组合。
- **解读边界**：这是语义可接受性而非形态句法错误；上下文、焦点和推理方式可能显著影响母语者判断。
- **原始参照**：GPT-2 87.0%；人工抽样一致率91.0%。

### 61. `superlative_quantifiers_2`｜no与数量上界表达二

- **通俗问题**：*at most nine*在普通肯定主语和 *no*主语下是否同样可解释？
- **官方样例**：正：*The teenager does tour at most nine restaurants.*　负：\**No teenager does tour at most nine restaurants.*
- **判断依据**：模板把普通肯定主语与上界数量表达的组合设为正例，把 *no*与该表达的嵌套设为负例。
- **解读边界**：正例含强调助动词 *does*，整体也较生硬；分数可能混合语义兼容性和表面搭配熟悉度。
- **原始参照**：GPT-2 87.2%；人工抽样一致率85.0%。

## 十二、主谓一致（6项）

前两项在主语内部加入复数干扰名词，检查模型是否追踪真正的中心语；其余四项使用规则或不规则单复数，改变主语或动词的一端。

### 62. `distractor_agreement_relational_noun`｜关系名词短语中的一致干扰

- **通俗问题**：主语内部较近的复数名词会不会使模型误选复数动词？
- **官方样例**：正：*A niece of most senators hasn't descended most slopes.*　负：\**A niece of most senators haven't descended most slopes.*
- **判断依据**：主语中心语是单数 *niece*；介词短语中的复数 *senators*只是干扰项，限定动词应使用 *hasn't*。
- **解读边界**：这类题同时测层级结构和对一致吸引错误的抵抗力。
- **原始参照**：GPT-2 79.5%；人工抽样一致率81.0%。

### 63. `distractor_agreement_relative_clause`｜关系从句中的一致干扰

- **通俗问题**：主语关系从句内的复数名词能否改变主句动词的数？
- **官方样例**：正：*This customer who had visited most children has worn some shoes.*　负：\**This customer who had visited most children have worn some shoes.*
- **判断依据**：主句主语中心语是单数 *customer*；关系从句宾语 *children*不控制主句谓语。
- **解读边界**：干扰项与动词线性距离较近，模型高分才更能支持其利用层级主语信息。
- **原始参照**：GPT-2 65.7%；人工抽样一致率85.7%。

### 64. `irregular_plural_subject_verb_agreement_1`｜不规则复数主语：改变动词

- **通俗问题**：不以普通 *-s*结尾的复数 *radii*应搭配 *have*还是 *has*？
- **官方样例**：正：*Those radii have scared that teenager.*　负：\**Those radii has scared that teenager.*
- **判断依据**：*radii*是复数主语，要求复数助动词 *have*。
- **解读边界**：限定词 *those*也显式提示复数，模型可能不必只靠识别 *radii*词形。
- **原始参照**：GPT-2 92.8%；人工抽样一致率94.0%。

### 65. `irregular_plural_subject_verb_agreement_2`｜不规则单复数主语：改变主语

- **通俗问题**：动词为复数形式 *meet*时，主语应是 *women*还是 *woman*？
- **官方样例**：正：*The women meet.*　负：\**The woman meet.*
- **判断依据**：不规则复数 *women*与无第三人称单数 *-s*的 *meet*一致；单数 *woman*要求 *meets*。
- **解读边界**：题目很短且词形高频，适合检测基本知识，不足以代表长距离一致能力。
- **原始参照**：GPT-2 92.4%；人工抽样一致率95.0%。

### 66. `regular_plural_subject_verb_agreement_1`｜规则主语：改变动词形式

- **通俗问题**：单数主语 *Paula*应搭配 *references*还是 *reference*？
- **官方样例**：正：*Paula references Robert.*　负：\**Paula reference Robert.*
- **判断依据**：第三人称单数现在时要求动词带 *-s*。
- **解读边界**：官方UID虽含 `plural`，该方向的具体句对使用单数主语操纵动词；索引按数据内容说明，不按名称望文生义。
- **原始参照**：GPT-2 96.7%；人工抽样一致率95.0%。

### 67. `regular_plural_subject_verb_agreement_2`｜规则主语：改变主语形式

- **通俗问题**：动词为复数形式 *perform*时，主语应是 *students*还是 *student*？
- **官方样例**：正：*The students perform.*　负：\**The student perform.*
- **判断依据**：规则复数主语与无第三人称单数 *-s*的动词一致；单数主语应使用 *performs*。
- **解读边界**：这一项只含相邻的简单主谓关系，不测跨插入成分的一致追踪。
- **原始参照**：GPT-2 91.0%；人工抽样一致率95.0%。

## 总览：怎样理解67项而不被术语淹没

67项并不是67条彼此独立的“英语规则”。它们大体可以归结为四种实验操作：

1. **形式匹配**：改变数、性、时态或分词形式，如照应语一致、限定词—名词一致和主谓一致；
2. **结构许可**：改变动词能否带宾语、被动或不定式结构，如论元结构和控制/提升；
3. **依存位置**：移动填充语或空位，检查远距离关系和结构边界，如填充语—空位依存与岛效应；
4. **解释条件**：改变许可成分或作用域，如否定极性项和量词。

因此，读一个模板时最有效的问题不是“这个UID怎样翻译”，而是：正负例改变了哪一个可观察条件？这一条件预期影响哪个成分之间的关系？是否还有词频、语境、自然度或多重操纵可以解释模型分数？

## 数据质量与使用提醒

- 人工抽样一致率较低的模板应单独报告，尤其是 `sentential_subject_island`（60.6%）、`only_npi_scope`（72.0%）、`wh_island`（73.0%）、`wh_vs_that_with_gap_long_distance`（74.7%）、`principle_A_domain_2`与`tough_vs_raising_1`（均75.0%）。
- `complex_NP_island`、`existential_there_quantifiers_2`、`ellipsis_n_bar_2`等模板的生成句明显生硬。模型答错可能反映目标现象，也可能反映词汇搭配、加工难度或模板伪影。
- 生命度、传统语法性别和主谓一致标签采用BLiMP的主流美国英语设定。研究者若用于方言、公平性或社会语言学分析，应重新验证词表和标签。
- 若要评价当代头部模型，最好使用未公开的新词表和新模板，并在同一界面下同步采集人类判断；不宜把公开数据上的接近满分直接解释为相应语言能力已经完全解决。





## 资料来源

1. Warstadt et al. 2020. *BLiMP: The Benchmark of Linguistic Minimal Pairs for English*.  
   https://aclanthology.org/2020.tacl-1.25/
2. BLiMP官方数据文件、GPT-2结果和人工验证摘要。  
   https://github.com/alexwarstadt/blimp
3. BLiMP官方范式补充材料。  
   https://github.com/alexwarstadt/blimp/blob/master/supplemental_materials/BLiMP_Paradigms.pdf

