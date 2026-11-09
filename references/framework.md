# 四档框架：完整说明与出处

## 一、原始出处

**Felix Rieseberg**，Anthropic 工程负责人，管辖三条产品线：**Claude.ai、Cowork、Claude Code Desktop**。在此之前是 **Electron 的联合创造者**。

- 2026-10-13：发布提问指南
- 2026-10-26：*Silicon Valley Girl* 访谈，含时间戳拆解
- 中文传播多写作"Claude 工程负责人"，实际管辖范围是上述三条线，不是 Claude 全部工程

他给这套东西的命名：

- **Costume Prompts（戏服提示词）**——你给模型穿白大褂，它就演医生
- **Skills Debt（技能债）**——每个自定义 skill 都要问它绕开了哪个模型缺陷；模型不再有那个缺陷时，这个 skill 就该删

## 二、核心论断

> **persona prompt 让模型「听起来像」专家；process prompt 让它「做起来像」专家。**
> **前者改词汇，后者改计算。**

他的原话（英文）：

> "A lot of the models still have the problem that if you tell them to act like a very good accountant that they engage in a little bit of role play."

注意限定词：**"a lot of the models still have"**，不是"所有模型、所有场景都无效"。这个限定词必须保留，否则会被学术证据反驳（见 `evidence.md`）。

## 三、四档阶梯

中文传播普遍只讲三档，漏掉了最底下那一档。完整的是四层：

### Speed · 速度

**定义**：把手上这个动作做得更快。

**例**：「帮我润色这段文字」「帮我总结这封邮件」「你是一位资深律师，帮我看看这份合同」。

**为什么必须保留这一档**：它是被否定的基线。Felix 的判断是——如果你只是让 Claude 总结邮件、润色语气、扮演角色，你根本没有碰到新智能的边。

**删掉这一档的后果**：后面三档从"你现在的用法是浪费"降级成"还有更好的方法"。论证力度差一个量级。

### Altitude · 高度

**定义**：要的是结果，不是动作。

**原始例子**：一年半前他发现一个 crash，就搬给 Claude 说"修这个"。后来意识到自己只是 Claude 的传送带。正确做法不是一个个搬 crash，而是让 Claude 能访问全部 crash 数据，自己判断该修什么、不该修什么。

**他的三段递进示例（季度业务回顾 QBR）**：

```
第一层：告诉我这季度什么变了、为什么、我们该怎么做。
第二层：在所有你了解到的情况里，判断哪三个决策最紧急，
        并给出正反两方的论证。
第三层：这个回顾存在的目的是让管理层早点发现问题、把钱和人挪到对的位置。
        设计一个比季度 PPT 更好的机制，用我们自己的历史数据证明它会更早发现问题，
        然后和现有机制并行跑一个季度。
```

**关键**：第三层不是"更高的要求"，是"质疑这个任务本身的形态对不对"。

### Depth · 深度

**定义**：用顶尖高手的**原始材料和工具**，不是别人处理好的二手信息。

**关键区分**：要的不是"更多上下文"，是"更原始的上下文"。行业报告、二手总结、别人的结论，都算"已经准备好的信息"。

**他的原话**（写在现成 prompt 里）：

> Name the most **raw** data or materials they would use **instead of information already prepared for me**.

**目标也要敢定量级**：网页加载别只要求"优化到 5 秒"，直接要 200 毫秒。

### Range · 广度

**定义**：把名词换成动词，借其他领域的做法。

**例**：「做一份 PPT」→「让一群很忙的人看懂前因后果，然后做决定」。

**借跨领域本事的正确姿势**：借流程，不借语气。

```
❌ 像记者那样写
✅ 照记者的做法去查资料、找证据
```

**他的极端做法**：组一个团队——分析师、记者、编辑，再加一个"押注公司会倒闭的人"和一个会计专家做批判。**但不是让 AI 扮演这些人，是让它去做这些人会做的调研。**

## 四、他给的现成 prompt

原文（可直接使用）：

```
I need a deeper version of this task, not a bigger one.

Before rewriting my prompt:
1. Tell me what a leading specialist in this field would do
   that I am not currently asking for.
2. Name the most raw data or materials they would use
   instead of information already prepared for me.
3. ...
```

中文版：

```
我要的是这个任务更深，不是更大。

改写我的 prompt 之前，先告诉我：
1. 这个领域顶尖的人会做哪些我现在没要求的事？
2. 他们会用哪些原始数据或材料，而不是别人已经替我准备好的？
3. ……
```

**「deeper, not bigger」这四个字是整份指南的压缩版。** 大多数人以为"更好的 prompt = 更长的 prompt"，这条直接把这条路堵死了。

## 五、三个反常识

### ① 要原始数据，不要二手材料

直觉上"给模型更多背景"是好事，但他要的是"给模型更少加工"。

### ② 绝不让 AI 自己评分

原文：*never let AI grade its own work — use independent verification*。

模型自评会系统性偏松，这不是能力问题，是结构问题。

### ③ 工具比形容词管用

**这是整套方法最硬的机制证据。**

他的例子：AI 生成 3D 和动画的能力最近跳了一档，不是因为形容词变好了，是因为有人让 Claude 直接打开 **Blender**——专业动画师用的那个软件。

**工具里编着几十年的手艺，一段人设文字编不进去。**

这条说明"人设无效"不是修辞判断，是有机制的：**人设传递的是风格先验，工具传递的是能力边界。**

## 六、Skills Debt：一条容易忽略的推论

每个自定义 skill 都该问一句：**它绕开了哪个模型缺陷？**

- 如果这个缺陷是模型代际问题，新模型发布后这个 skill 就该删
- 如果这个缺陷是结构性缺陷（比如模型不会读你公司的私有格式），这个 skill 会长期有效

给每个 skill 打一个**复核日期**。到点重新评估，别让过期 skill 一直占着上下文。

这条对做 prompt 工程的人是硬提醒：**你写的很多东西，是在补模型的洞。洞补上了，你的补丁就是负担。**
