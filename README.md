# RSI-Social-Simulation-Papers



### 1. Recursive Self-Improvement & Agent Self-Evolution



| Paper                                                        | Method                                                       | Experiments                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| [MetaSkill-Evolve: Recursive Self-Improvement of LLM Agents via Two-Timescale Meta-Skill Evolution](https://arxiv.org/abs/2607.05297) | **改进对象：** 任务 Skill 与指导 Skill 改进的 Meta-Skill。 <br />**Mechanism：** Fast Loop 分析任务失败并迭代 Skill；Slow Loop 以更低频率修改 Meta-Skill。Meta-Skill 包括 Analyzer、Retriever、Allocator、Proposer、Evolver 五部分；每个搜索分支保有自己的 Skill 与 Meta-Skill，允许改进策略随经验变化。 | **实验场景：** OfficeQA（文档问答）、SealQA（推理问答）、ALFWorld（交互式行动任务）；比较 No-Skill、Static Skill、Single-Level Evolution 与双时间尺度演化。<br /> **主要结果：** 在所有Agent 共用冻结 Backbone 的情况下，本文方法优于上述基线； <br />**局限：** 在预定义五组件及固定整体演化流程内实现的一阶有限RSI。 |
| [Metaⁿ: Recursive Self-Improvement through Emergent Depth](https://arxiv.org/abs/2608.24735) | **改进对象：** 多层 Agent 推理与执行代码。 **Mechanism：** 固定 Meta-Operator `Ω`。它读取已有执行轨迹、当前上下文和历史层信息，生成新一层的代码/策略模块；`Ω` 本身固定，递归体现在它不断生成的新层，又成为后续元操作的输入。 | **实验场景：** 在两类 Backbone 与八类任务家族中比较已有自改进方法；包括 ARC-AGI-2 等较难依靠技能记忆解决的任务，并分析不同层之间的条件化信息传递。<br /> **主要结果：** 论文报告在八类任务家族中超过对比方法；ARC-AGI-2 上取得非零分数。消融结果表明，跨层传递的 conditioning 是递归收益的重要来源。 <br />**局限：** Ω 和外围评估／进化机制仍固定 |

### 2. LLM-Based Social Simulation & Behavioral Modeling



| Paper                                                        | Method                                                       | Experiments                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| [G-Sim: Generative Simulations with Large Language Models and Gradient-Free Calibration](https://proceedings.mlr.press/v267/holt25b.html) | **改进对象：** 模拟器的结构与数值参数。 <br />**Mechanism：** 使用 LLM 生成或调整模拟器结构，再通过无梯度优化或模拟推断（SBI）进行经验校准，利用反馈迭代改进。 | **实验关注：** 生成结构后能否通过校准减少预测误差；与纯数据拟合或未经校准的生成式模拟器相比，面对未观测条件、干预或外推时是否更合理；校准过程能否处理不可微的仿真系统。 |
| [Implicit Behavioral Alignment of Language Agents in High-Stakes Crowd Simulations](https://aclanthology.org/2025.emnlp-main.1562/) | **研究问题：** LLM Agent 的行为分布常与真实/专家参考行为不同。能否通过修改 Persona，而不是直接向 Agent 下命令，缩小 Behavior–Realism Gap？ <br />**Mechanism：** 用 Persona-Environment Behavioral Alignment（PEBA）将行为真实性表述为分布匹配问题，使用 PersonaEvolve（PEvo）迭代细化 Persona，使模拟群体行为与专家行为参照更接近。 | **实验场景：** 主动枪击事件人群模拟；比较不加引导与显式指令引导，并考察对相近新场景的泛化。 |
| [A Multi-Timescale Recursive Self-Improvement Engine for Open-Ended Persona Growth](https://arxiv.org/abs/2607.08252) | **研究问题：** 长期运行的 Persona Agent 看似不断生成生活事件，但可能越来越集中在熟悉主题与关系上，即 Self-Locking。怎样在保持角色连续性的同时让生活过程真正出现变化？ <br />**多时间尺度设计：** 将外部发生的事情、积累到的证据及相对稳定的人格/生活状态分离；通过 OSO Loop 控制哪些新事件进入观察、哪些长期证据才足以改变 State。 <br />**原则：** 允许环境事件产生新颖变化，但不能让一次偶发生成结果立即改写角色的长期身份；角色变化应有证据与时间积累。 | **实验场景：** 三年压缩模拟、八模型的 40 天压力测试，以及相同运行条件下的 40 天 A/B 对照。 <br />**主要结果：** 八模型压力测试的 5 日滚动行为类别重复率为 95.2%–97.6%；在 A/B 对照中，采用上下文切片遮蔽与定向发散后，宏观主题重复率从 61.8% 降至 36.3%，累计主题数量约翻倍。 |
| [Evolution of Social Norms in LLM Agents using Natural Language](https://arxiv.org/abs/2409.00993) | **研究问题：** 如果 Agent 的人格和规范倾向直接用自然语言表示，通过遗传式选择与改写，是否会演化出稳定的社会行为？ <br />**Mechanism：** 重复 Norms Game。Agent 在博弈中根据其文字人格采取行动；每代根据博弈收益选择表现较好的策略描述，再由 LLM 重述、变异并赋给下一代。进化对象是自然语言策略 | **Tasks：** 包含作弊、惩罚等行为的 Norms Game。 **Setup：** 7 个 Agent；每个 Epoch 21 轮；共 40 个 Epoch。 |

### 3. Social Simulation Validity, Robustness & Evaluation



| Paper                                                        | Method                                                       | Experiments                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| [Stop Drawing Scientific Claims from LLM Social Simulations Without Robustness Audits](https://arxiv.org/abs/2605.18890) | **Target：** 基于 LLM 社会模拟得出的科学结论是否稳健。 <br />**Core Question：** 当 Prompt、模型选择、人口配置或模拟假设发生变化时，研究结论是否仍然成立？ | **实验场景：** 重复囚徒困境与社交媒体回音室模拟；跨模型改变 Persona 呈现、博弈措辞、网络同质性和枢纽节点安排。 <br />**主要结果：** 某些小扰动可使合作率变化高达 76 个百分点；相同扰动在另一个模型上可能只引起约 1 个百分点的变化。网络设计也可明显影响极化指标。 |
| [The PIMMUR Principles: Ensuring Validity in Collective Behavior of LLM Societies](https://arxiv.org/abs/2509.18052) | **核心问题：** LLM 社会模拟声称的“群体现象”是否受到不恰当的 Persona、交互、记忆、控制与实验泄漏影响？ <br />**Mechanism：** 建立六项评估原则 Profile、Interaction、Memory、Minimal-Control、Unawareness、Realism（PIMMUR），审计既有工作并复现实验以检查结果是否仍成立。 | **实验场景：** 系统审计 350 篇论文报告的576 项模拟研究，并复现五项代表性社会实验。 <br />**主要结果：** 报告 65.2%的测试情形中前沿模型能识别所模拟的原始社会实验，50.6%的 Prompt 施加了可能预先决定结果的约束；在符合 PIMMUR 原则后，部分原本报告的集体现象消失或逆转。 |
