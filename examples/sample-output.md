# Sample Output

Below is a shortened example of the kind of output PaperLocus is optimized to produce.

```markdown
## 一句话总结

这篇论文提出了一个面向单细胞多组学的 foundation model，并把重点放在跨任务迁移能力而不是单一任务优化上。

## 论文卡片

- 标题 / 作者 / venue
- 研究问题
- 核心贡献
- 为什么重要

## 论文类型判断

- 类型：更适合作为方法论文阅读，而不是经典 Nature 证据链论文
- 判断依据：
  - 摘要主角是模型与迁移学习框架
  - 结果部分以 benchmark 和 downstream task 为主
  - 贡献句式更接近 `we develop / we propose`

## 文献中的位置

- 上承：foundation model 与 transfer learning 路线
- 对比对象：已有 single-cell foundation models 与 task-specific baselines
- 本文变化：把通用预训练框架迁移到单细胞多组学场景

## 引言脉络

- 作者先指出现有方法在跨任务泛化上的局限
- 再提出统一预训练框架
- 最后用多个下游任务说明该框架不是只在单点任务上有效

## 方法框架

- 输入表示
- 预训练目标
- 下游适配方式

## 实验设计与核心结果

- 为什么设计这些实验
- 每组实验支持什么主张
- 哪些结果是强证据，哪些只是补充证据

## 主要贡献

- 提出统一框架
- 展示跨任务迁移能力
- 明确其在领域方法谱系中的位置

## 局限与待核实点

- 论文 claim 与实验支持范围是否完全一致
- 某些数据集或 baseline 细节是否需要外部核验
```
