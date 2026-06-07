# Sample Outputs

## Branch A: CS Paper (Title-Only Smoke Test)

This is a shortened smoke-test output for a title-only request. It demonstrates the intended caution level when PaperLocus has not inspected the full paper.

```markdown
# Attention Is All You Need

## 一句话总结
仅从标题推断，这篇论文大概率主张：在序列建模里，`attention` 可以从辅助模块上升为核心架构；但由于没有读取正文，这个判断只能算低置信度预判。

## 论文卡片
- 标题：`Attention Is All You Need`
- 输入条件：仅有标题，未读取摘要、正文、图表或参考文献
- 笔记级别：title-only smoke test

## 论文类型
- 推断：更像计算机科学方法论文（Branch A），而不是以科学发现为主的证据链论文。
- 不确定性：仅凭标题无法排除它也可能是一篇较强观点表达的系统论文。

## 文献位置
- 推断：标题语气很强，像是在反驳"序列模型必须依赖其他核心机制"的既有默认设定，并把 `attention` 推到主干位置。
- 不确定性：不知道它具体在对比 RNN、CNN、还是更早的 encoder-decoder 变体。

## 方法框架
- 论文主张：当前无法从标题直接确认具体方法。
- 推断：大概率会提出一个以 `attention` 为核心的完整模型。
- 不确定性：不知道是否包含编码器-解码器、位置编码、多头机制等。

## 实验与结果
- 论文主张：当前未知。
- 推断：典型方法论文会用基准任务对比来证明纯 `attention` 架构的优势。
- 不确定性：任务、数据集、指标、基线、结论强度都不能从标题推出。

## 主要贡献
- 推断：核心贡献可能是把 `attention` 从配角改成主角，并据此重写序列建模范式。

## 局限、反例与检查点
- 只看标题时，最容易高估"它究竟说的是研究结论，还是宣传式命名"。
- 下一步最值得补的是摘要。

## 值得细读的部分
- 摘要：确认真正 claim
- 引言：确认它在反驳谁、替代谁
- 方法部分：确认 `attention` 是否真是唯一主干
- 实验部分：确认结论是效果优势、效率优势还是两者都有
```

---

## Branch B: Nature / Science Paper (Abstract + Evidence Scan)

This demonstrates the evidence-chain reading style, using a paper that has strong method content but whose narrative is organized around what has become scientifically possible.

```markdown
# Highly Accurate Protein Structure Prediction with AlphaFold

## 一句话总结
AlphaFold 首次将蛋白质结构预测推进到与实验精度相当的水平，核心创新是结合深度学习与蛋白质结构生物学中的共进化约束。

## 论文卡片
- 作者：Jumper, John; Hassabis, Demis; et al.
- 年份：2021
- 期刊：Nature
- DOI：10.1038/s41586-021-03819-2

## 论文类型
Branch B — Nature / Science（证据链驱动；含强方法内容但叙事以科学能力突破为主线）

## 核心科学问题
蛋白质的氨基酸序列如何决定其三维折叠结构？这个"蛋白质折叠问题"困扰结构生物学已超过 50 年。

## 科学问题
- 已有理解：物理建模（如 Rosetta）和进化耦合分析能部分预测结构，但精度远不及实验方法（X 射线晶体学、冷冻电镜）
- 本文填充的空白：深度学习能否将预测精度提升到实验级别？

## 关键发现与方法的关系
- **方法**：AlphaFold 的 Evoformer 架构利用多序列比对中的共进化信息 + 3D 结构约束的端到端学习
- **发现**：关键不在于单一方法创新，而在于方法使得"从序列直接到原子级精度结构"成为现实
- 方法服务于结论，而非结论服务于方法

## 证据链
1. **CASP14 竞赛结果**：AlphaFold 在 43 个目标蛋白中的 25 个达到实验精度，远超其他参赛方法
2. **落选蛋白回溯分析**：即便是 CASP 中未选为目标的结构，预测精度依然接近实验水平
3. **域间精度的量化**：GDT（全局距离测试）评分显示预测结构在侧链和主链层面均与实验结构高度一致
4. **对已知蛋白结构的覆盖**：AlphaFold 的预测覆盖了 PDB 中大部分已知折叠类型，暗示模型学到了泛化的折叠规则

## 机制层面的解释
- Evoformer 通过注意力机制捕捉氨基酸对之间的共进化信号
- 这些共进化信号本质上编码了物理接触约束，使网络能隐式学习折叠的热力学

## 适用范围
- 单链蛋白预测表现最佳；多链复合物和动态构象仍在发展中
- 对于共进化信号稀疏的蛋白（如孤儿蛋白、从头设计的蛋白），精度下降

## 局限性
- 预测的是静态结构，不是折叠路径或构象动态
- 对无序区域和膜蛋白的精度仍有改进空间
- 模型的泛化能力依赖于训练数据中同类折叠模式的覆盖度

## 值得细读的部分
- CASP14 的评估方法论（为什么 GDT 指标足够严格）
- Evoformer 如何将共进化信息引入注意力机制
- 对落选蛋白和 PDB 覆盖率的消融分析
```

---

## Branch C: Economics Paper (Abstract + Method Scan)

This demonstrates the output structure for a reduced-form empirical economics paper where the abstract and method sections are available.

```markdown
# Minimum Wages and Employment: A Case Study of the Fast-Food Industry in New Jersey and Pennsylvania

## 一句话总结
利用新泽西州与宾夕法尼亚州最低工资变动的准自然实验，通过双重差分法发现最低工资上升并未减少快餐业就业。

## 论文卡片
- 作者：Card, David; Krueger, Alan B.
- 年份：1994
- 期刊：American Economic Review
- DOI：10.1257/aer.84.4.772

## 论文类型
Branch C — Economics & Management（简化式实证，DiD）

## 研究问题
最低工资的提高是否会减少低薪工人的就业？标准竞争模型预测会，本文用自然实验检验这一预测。

## 文献位置
- 与标准教科书预测（最低工资↑ → 就业↓）对话
- 回应此前时间序列研究的混合结论
- 引入准实验方法到最低工资研究中，推动了该领域的"可信性革命"

## 识别策略
- **因果挑战**：最低工资与就业之间存在反向因果和遗漏变量——经济状况同时影响工资和就业
- **识别方法**：双重差分（DiD）利用新泽西州 1992 年最低工资上涨作为处理，以相邻的宾夕法尼亚州（未涨）作为控制组
- **识别假设**：平行趋势——如果没有政策变化，两州就业趋势应相同。作者通过调查两州经济趋势的相似性来支持这一假设
- **识别变异的来源**：州际政策差异 × 时间变化

## 数据与样本
- 电话调查 410 家快餐店（Burger King、KFC、Wendy's、Roy Rogers），分别在政策前后
- 样本期间：1992 年 2-3 月（政策前）和 1992 年 11-12 月（政策后）

## 核心估计
- DiD 估计显示新泽西州全职等效就业相对于宾夕法尼亚州没有下降，甚至略有上升
- 经济显著性：效应量很小，与标准竞争模型的预测方向相反

## 稳健性检验
- 替代对照组：用新泽西州内初始高工资（不受政策影响）的店铺作为替代控制组
- 替代结果变量：全职等效就业人数、雇员数量、店铺营业时间

## 局限
- 样本仅限于快餐业，外部效度需谨慎
- 短期效应（政策后 7-8 个月），无法观察长期调整
- 电话调查的测量误差

## 值得细读的部分
- 引言中的文献批评
- DiD 识别假设的论证
- 稳健性检验部分
```

---

## Branch D: Quantitative Finance Paper (Condensed)

A condensed output example for an asset pricing paper, highlighting the finance-specific fields.

```markdown
# Common Risk Factors in the Returns on Stocks and Bonds

## 一句话总结
提出三因子模型（市场、SMB、HML），发现除了市场贝塔外，规模和账面市值比是解释美国股票横截面收益的核心因子。

## 论文卡片
- 作者：Fama, Eugene F.; French, Kenneth R.
- 年份：1993
- 期刊：Journal of Financial Economics

## 论文类型
Branch D — Financial Econometrics & Quantitative Finance（资产定价）

## 研究问题
哪些共同风险因子能够解释股票和债券收益的截面变化？

## 文献位置
- 是对 CAPM 单因子模型的系统性扩展
- 回应对 CAPM 无法解释的"异象"（规模效应、价值效应）
- 后续成为资产定价的实证基准模型

## 模型设定
- 被解释变量：股票组合超额收益、债券组合超额收益
- 因子：MKT（市场超额收益）、SMB（小盘-大盘）、HML（高 BM-低 BM）
- 另有债券因子：TERM（长-短期国债利差）、DEF（公司债-国债利差）

## 数据与样本
- 美国股票：NYSE/AMEX/Nasdaq，1963-1990
- 频率：月度
- 关键变量：市值、账面市值比、收益

## 评价
- **统计层面**：三因子能解释大部分组合收益的截面变化（高 R²），SMB 和 HML 的因子收益率在统计上显著
- **经济机制**：SMB 和 HML 可被解释为捕获了与经济基本面相关的系统风险（困境风险），论文对此机制的讨论相对开放

## 因子过拟合检查
- 样本期为 1963-1990，后续样本外检验（1990+）总体支持模型，但近年来价值因子表现走弱，说明因子稳定性是需要持续关注的问题

## 局限与反例
- 无法解释动量效应（后由 Carhart 四因子补充）
- 样本仅覆盖美国市场
- 因子的经济机制仍在争论中（风险补偿 vs 数据挖掘 vs 行为解释）

## 投资启示
- 小盘股和价值股在长期可能提供超额收益，但该溢价具有时变性和大幅回撤
```
