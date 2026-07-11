# de-ai-zh

中文去 AI 味的 skill。给要交付的成段中文写作去 AI 味，面向脚本、小说、文案、文章。

## 它解决什么问题

常见的去 AI 味做法是列一份禁用词表，把 delve、此外、综上所述 这些词换掉。问题在于表面词汇清干净了，底下骨架没动，段落还是同样的弧线，结论还是拔高到没人要的大图景。读起来照样像 AI，只是换了一种像法。

这个 skill 从病根入手。AI 味的根源是均值回归、RLHF 留下的对冲和专家腔、替读者操心、意义膨胀、公式化补全。改文字要先认这些病根，再从结构层改，不只替换词汇。

## 几条边界

它不追求 AI 检测器通过率。检测器抓的是标点分布的统计特征，不是人味，把句号全换成逗号能让检测值降到零，可那会让文章没法读。真实读者的读感才是目标。

即时聊天回复不在范围内。回复天然口语短碎，套硬规则会把自然口语抹平成另一种 AI 味。

它也不替代个人风格。作为底味，产出的是去味之后的平均人味，想精确到你这个人要另外叠一份个人菜谱，skill 里附了迭代流程。

事实核查不归它管。去味不等于内容真实，原文可能是 AI 杜撰的假数据假引语，要另外查。

## 怎么装

用 [skills CLI](https://skills.sh) 安装，可以装到任何支持的 agent。

```bash
# 装到当前项目
npx skills add uiYzzi/skills --skill de-ai-zh

# 装到全局
npx skills add uiYzzi/skills --skill de-ai-zh -g

# 装到指定 agent
npx skills add uiYzzi/skills --skill de-ai-zh -a claude-code -a cursor

# 不装也能试用，直接生成 prompt
npx skills use uiYzzi/skills@de-ai-zh --agent claude-code
```

装好后 agent 按 `description` 自动决定何时调用。想强制调用，直接说 de-ai-zh。

## 结构

主文件 `SKILL.md` 自洽，只读它就能跑完全套判断。`references/` 是补充，按需查。

- `SKILL.md`：病根、反向解、硬规则、保护清单、改写分档、两步回读、边界
- `references/patterns.md`：结构反模式，按问题族归类，配改前改后
- `references/lexicon.md`：词级清单，分三级
- `references/positive-style.md`：正向目标，干净但不失灵魂怎么做
- `references/protected-spans.md`：保护清单，什么不能改，什么是真人指纹
- `references/examples.md`：段落级改写示例，附个人菜谱迭代流程

## 怎么用

最简单的方式，给一段文字让它去味。skill 按这个顺序走：先判场景和改写幅度，划保护清单，做骨架检查，然后两步回读，第一步保真，第二步查残留，最后做一次活人感终审。

想强制每次都过这个 skill，在 agent 的配置或项目指令里加一条硬指令，输出任何成段中文文字前先调用 de-ai-zh。关键是把范围写清，只覆盖要交付的成段写作，不覆盖即时回复。

## 为什么主文件短

禁止清单别太长，上下文塞太多影响生成效果，规则越多越难遵守甚至自相矛盾。主文件只放最硬的规则和自检流程，长清单进 `references/` 按需查，规则太长时归纳成规律而不是逐条堆。

## 一点说明

这个 skill 不是敏感词替换器。删词解决不了味道，只告诉 AI 不要做什么，从来没让它尝过你要的味道。它能去掉食堂味，产出的是平均人味，不是你自己的红烧肉。想做出自己的味道，还得靠你自己的菜谱，这里只负责把公共病灶清干净。

## 参考来源

这个技能的判断不是凭空来的，下面这些资料各自有贡献。

[维基百科的 AI 写作特征页](https://en.wikipedia.org/wiki/Wikipedia:LLMSIGNS)（Wikipedia:Signs of AI writing）是最早把均值回归讲清楚的地方，模式清单的底子也在这里。 [blader/humanizer](https://github.com/blader/humanizer) 第一个把这套规律做成了 skill，它的 detection guidance 讲 cluster 原则和真人信号，翻译版没收这部分。 [shuorenhua](https://github.com/MrGeDiao/shuorenhua)（说人话）是中文去味技能里最完善的，保护清单、两步回读、改写分档、变体归并都从它的设计里借过来。 [avoid-ai-writing](https://github.com/conorbronsdon/avoid-ai-writing) 本质层做得最透，过度打磨警告、Tier 分级、context profile 的矩阵都参考了它。

[stop-slop](https://github.com/hardikpandya/stop-slop) 结构精炼，主文件加 references 的分层就是从它来的。 [De-AI-Prompt-Enhancer](https://github.com/OUBIGFA/De-AI-Prompt-Enhancer-Writer-Booster-SKILL) 项目的 ai-trace-detector 细节密度极高，分析师讲解语姿、关联句式过度标记、戏剧化揭露修辞这几族都是从它细化出来的。 [chujianyun/skills](https://github.com/chujianyun/skills) 里的 remove-ai-flavor 贡献了判词腔、资料味讲义味、删拆换顺接五字口诀。 [李继刚的写作引擎](https://github.com/lijigang/ljg-skills) 贡献了不自标深度和翻译腔免疫检验。 [Towards AI 的 anti-slop 框架](https://academy.towardsai.net/products/digital_downloads/anti-slop-framework) 给了 writer/judge 双模型循环的思路。

我有一套面向脚本、小说、文案的创作硬规则，涵盖句式节奏、标点、否定、形容词、比喻。这些是创作向的绝对禁令来源，一章最多两处比喻、一个名词最多一个修饰、全文禁破折号，都从这里来的。平克的《风格感觉》和加里·普罗沃斯特的句长变化给节奏那节提供了活教材，桑德森的写作讲义贡献了信息密度的判断，斯科特·亚历山大的非虚构写作建议给了同主语开头连续这条。番茄小说的 AI 文治理报道和出版界报道，为误伤风险和信任危机提供了现实佐证。少数派作者的[真实对照实验](https://sspai.com/post/109288)验证了 Skill 能去掉四到五成 AI 味，也给出了标点禁令的间接机制和 Skill 能力的现实边界。
