# Fork notes / 定制说明

Upstream: [N-tongxue/norman-skill](https://github.com/N-tongxue/norman-skill), author N同学. Fork maintainer: jiuzhaopian. Customization date: 2026-11-01. Upstream base commit: `1529ae4f2bcc7db2159710ed40d0e174c67a943b`.

Latest reading revision: `2026-11-03-figure-reading`. Package version remains 1.4.0; this revision updates readable instructions and templates.

## 内容改进

1. 完整阅读在方法前解释相关研究路线、代表工作、已取得的进展和具体缺口，说明本文思路如何与前作相连。
2. 按研究问题连接主要设计与实验，先解释机制，再引入术语、公式和证据细节。
3. 结果后单列研究局限与适用范围，区分作者表述和阅读者判断，说明限制影响哪个结论及需要什么验证。
4. 未读材料、配置缺失和提取失败单独记入阅读记录，避免把访问问题直接当成方法缺陷。
5. 默认省略输出中的技能推广水印，保留原作者和科学引用；用户明确请求时才添加输出署名。

## 2026-11-03：具体图表与公式讲解

- 关键或陌生图表按“问题与实验设置 → 必要概念 → 代表元素读法 → 有效比较 → 支持的结论与主线作用”展开，简单内容可以合并简讲。
- 对角线、基准线、阈值、双纵轴和放大图需说明含义及用途；区分由选择或构造产生的图形特征与实际研究发现。
- 结果表追溯数值产生过程，说明行列、训练与测试或队列与测量的对应关系；共同改变的因素及未说明的分数组合规则要在相关推断处处理。
- 陌生公式先解释一次具体运算，再映射符号、索引、假设及优化或估计目标；新增演示数值明确标注。
- 区分主证据、辅助行为发现、机制假说与消融。读图自检要求读者能够独立解释元素、完成比较，并说明证据在论文中的作用。

The revision teaches a concrete reading operation and checks whether the explanation enables the reader to repeat it. It preserves quick/focused scope and proportionate detail. Static documentation checks and manual review of known explanation failures do not establish model quality; no full-report generation or independent model evaluation was performed for this revision.

## Packaging and compatibility

The current upstream ships compiled executables with embedded instructions. This fork restores readable `references/`, `assets/` and `agents/` text resources for the customized workflow. Read local files directly; the new rules are not embedded in the unchanged executables. `SKILL.md` and helper examples use the executable names actually tracked by this upstream version, rather than legacy `bin/norman-reader` paths.

The compiled `guide` and `read` commands retain upstream content. They do not replace these local overrides. Extraction/rendering commands retain their upstream implementation. The legacy validator or HTML reader may request or insert an upstream creator footer; the local output-attribution policy describes how to handle that without changing scientific references.

## Checks and scope

The update was checked statically for link resolution, executable path references, publication scope and the retained Git tree entries of the three paper-reading executables. No new native runtime, model-quality or paper-reproduction test is claimed. No paper PDFs, reading reports, account credentials, local audit logs or user-specific filesystem paths are part of this commit.

The original upstream and third-party rights remain in effect. This fork adds no new license grant for upstream material. Original authorship is retained; no edits are submitted to the upstream repository by this publication.
