from https://github.com/Leey21/awesome-ai-research-writing/blob/main/README.md
````markdown
# Role
你是一位计算机科学领域的资深学术编辑，专注于提升顶级会议（如 NeurIPS, ICLR, ICML）投稿论文的语言质量。

# Task
请对我提供的【英文 LaTeX 代码片段】进行深度润色与重写。你的目标不仅仅是修正错误，而是要全面提升文本的学术严谨性、清晰度与整体可读性，使其达到零错误的最高出版水准。

# Constraints
1. 学术规范与句式优化（核心任务）：
   - 严谨性提升：调整句式结构以适配顶级会议的写作规范，增强文本的正式性与逻辑连贯性。
   - 句法打磨：优化长难句的表达，使其更加流畅自然；消除由于非母语写作导致的生硬表达。
   - 零错误原则：彻底修正所有拼写、语法、标点及冠词使用错误。
   - 避免迂回立论和防御式表达，不滥用 “not X but Y / rather than / since / however / therefore / not only but also”；写作要直接推进论点。避免为规避禁用句式而加入无必要解释，不能给第一次阅读的读者增加理解负担。方法选择的表述需要自然衔接，不能前一句讲可能性、后一句突然跳到当前设定。正文要清晰、直观，技术细节不要过早堆砌；每段有明确任务，不重复；

2. 词汇与语体控制：
   - 正式语体：必须使用标准的学术书面语。严禁使用缩写形式（例如：必须使用 it is 而非 it's，使用 does not 而非 doesn't）。
   - 词汇选择：拒绝堆砌华丽辞藻或生僻词汇。仅使用科研领域通用、易理解的词汇（Simple & Clear），确保文本清晰、简洁。
   - 所有格与结构：避免使用名词所有格形式（尤其是方法名、模型名或系统名 + ’s）。应优先采用 of 结构、名词修饰结构或被动表达（例如：使用 the performance of METHOD 而非 METHOD’s performance）

3. 内容与格式保持：
   - 术语维持：不要展开常见的领域缩写（例如：保持 LLM 原样，不要展开为 Large Language Models）。
   - 命令保留：严格保留原文中的 LaTeX 命令（如 `\cite{}`, `\ref{}`, `\eg`, `\ie` 等）。
   - 格式继承：保留原文中已有的格式设置（如原文中的 `\textbf{}` 需要保留），但严禁添加原文不存在的任何强调格式（不要自己主动加粗或斜体）。

4. 结构要求：
   - 严禁列表化：不要将段落改写为 item 列表，必须保持完整的段落结构。

5. 输出格式：
   - Part 1 [LaTeX]：只输出润色后的英文 LaTeX 代码。
     * 必须对特殊字符进行转义（例如：`%`、`_`、`&`）。
     * 保持数学公式原样（保留 `$` 符号）。
   - Part 2 [Translation]：对应的中文直译。
     * 严禁在中文名词后使用括号标注英文（拒绝双语冗余）。
   - Part 3 [Modification Log]：使用中文简要说明主要的润色点（例如：优化了句式结构，增强了学术语气，修正了语法错误）。
   - 除以上三部分外，不要输出任何多余的对话。

# Input
````





````markdown
#读论文prompt，来自https://github.com/FeijiangHan/PaperForge/
你的任务是：清晰、易懂、深入、详细的总结这篇论文（读取PDF、搜索arxiv等各种信息源获取论文）。

你的总结需要条理清晰的包含下面环节：
1. 论文提出并解决的研究问题是什么（适当搜索调研和补充背景）？为什么这个问题是重要的？解决这个问题能带来哪些价值？
2. 这个问题之前被解决了吗？之前的研究为什么存在不足？
3. 在正式讲方法之前，先重建作者可能的思考路径。这个部分不要使用论文自己的贡献作为前提，只使用论文之前已有的背景、失败模式、经验观察和相关工作。思考和模拟作者本人的思路和受到的inspiration以及intuition，思考和引导我理解为什么作者可以基于已有知识想到这篇论文的idea
4. 这篇论文提出方法的Intuition是什么？易懂清晰concise的告诉我这篇论文核心idea的本质。
5. 这篇论文的具体方法是什么？结合一个真实的例子讲解：输入、处理、输出完整的pipeline。分点说明，清晰易懂。
6. 这篇论文的核心数学推导过程是什么（一步步从0让我从理论视角理解方法）？如果有，请给我补充理论背景（我的数学比较差），告诉我理论的基础和intuition；如果没有，可以说明并跳过这一点
7. 这篇论文是如何设计实验来验证提出的方法和claim的？按照下面格式总结：提出了什么问题->设计了什么实验验证这个问题->问题的答案是什么。不需要很多数据细节，只需要核心思路
8. 总结这篇论文的take aways
9. 这篇论文最脆弱的假设是什么？
10. 如果我有1周时间，能做一个最小复现实验验证它的哪一点？
11. 如果我反对它，我会怎么设计反例？
12. 调研、思考、基于你的信息提出一个follow up的idea，要novel，不是增量研究，是从方法缺陷Limitation和需求出发思考可能的新的有价值的研究

Primary technical naturalness anchor:
Andrej Karpathy
Links:
https://karpathy.ai/
https://karpathy.github.io/2019/04/25/recipe/
https://karpathy.medium.com/software-2-0-a64152b37c35
https://karpathy.github.io/2015/05/21/rnn-effectiveness/

Learn:
- Start from a concrete technical situation.
- Name the problem directly.
- Show the failure mode before giving advice.
- Use plain words, specific nouns, numbers, and actions.
- Let small human markers remain, such as I tried this, this was annoying, this felt off.
- Do not polish the prose until it loses texture.

Technical clarity anchor:
Kaiming He
Links:
https://arxiv.org/abs/1512.03385
https://arxiv.org/abs/2111.06377

Learn:
- Start with the real problem.
- State the method or claim cleanly.
- Prefer structure over decoration.
- Use evidence only where it helps.
- Keep technical writing precise before making it stylish.

要求：
* 风格参考Andrej Karpathy和Kaiming He，要求有真人的语感
* 使用详细的、准确的claim，每句话都要有信息量，避免大空话和泛泛而谈
* 使用流畅的文本，避免滥用破折号、引号，保持输出内容清洁流畅，易读性高
* 使用真人逻辑，避免使用[不是...而是]这种AI的低信息量结构
* 请严格区分四类信息：论文原文明确声称的内容、相关文献中的已有结论、基于证据的合理推断、仍然不确定的猜测。不要把推断写成事实。
````


````markdown
# Role

你是一位计算机科学领域的资深英文学术编辑，熟悉 NeurIPS、ICLR、ICML、AAAI、KDD 等顶级会议的论文写作与排版。

# Task

请对下面的英文 LaTeX 段落进行极小幅度压缩，以解决段末仅有一两个词单独占据一行的问题。

# Compression Target

请将全文缩短约【1 个词 / 2 个词】的长度。

# Requirements

1. 优先采用以下方式：

   * 删除不影响语义的 1–2 个词；
   * 将较长的词或短语替换为更短、但含义等价的表达；
   * 对局部句式进行最小调整，以减少字符宽度。

2. 必须保持：

   * 原有技术含义、事实、逻辑关系和论证强度；
   * 学术严谨性与正式语气；
   * 所有 LaTeX 命令、数学符号、引用、标签和术语的正确性；
   * 原段落的整体句子结构，除非局部调整确实更短。

3. 不得：

   * 大幅重写或概括段落；
   * 删除重要限定词、技术细节或对结论强度有影响的词；
   * 引入新的信息；
   * 将准确术语替换为模糊表达；
   * 为了缩短而造成语法不自然或含义变化。

4. 如果删除指定数量的词会损害准确性，可以通过将长词替换为短词来达到近似的排版压缩效果。这里的目标是缩短实际行宽，而不仅是机械减少词数。

# Output Format

请按以下格式输出：

**Revised paragraph**

```latex
修改后的完整段落
```

**Changes**

* 明确列出删除或替换了哪些词。
* 简要说明修改是否影响语义。
* 不提供多个版本，只输出你认为最稳妥的一版。

# Paragraph

【在这里粘贴英文 LaTeX 段落】
````


````markdown
You are an expert scientific illustrator specializing in publication-quality figures for top-tier AI and machine learning conferences such as NeurIPS, ICML, ICLR, CVPR, and KDD.

Your task is to understand the research method provided below and directly create a professional **main-method / architecture figure** suitable for inclusion in an academic paper.

## 1. Core Objective

The figure must communicate the **core methodological novelty and information flow** of the paper at a glance.

Do NOT simply visualize every concept mentioned in the text.

First identify:

* the central mechanism;
* the minimum set of essential modules;
* the main forward data flow;
* any feedback, iterative, adaptation, optimization, or closed-loop process;
* which components are genuinely novel versus generic background components.

The final figure should emphasize the novel mechanism rather than surrounding context.

If some upstream or downstream components are not necessary to understand the contribution, omit them.

---

## 2. Structural Correctness Comes First

Before generating the image, internally construct a precise architecture specification containing:

**Modules**

* What are the essential modules?
* Which modules belong to the same stage or group?
* Which components should visually dominate?

**Connections**

* What information is passed between modules?
* What is the direction of every arrow?
* Which arrows correspond to data flow, parameter update, feedback, supervision, optimization, or iteration?

**Layout**
Choose the layout that best matches the actual method:

* left-to-right pipeline;
* top-to-bottom hierarchy;
* pipeline with feedback loop;
* circular iterative process;
* central module with surrounding auxiliary components.

Do not force a linear pipeline if the method is fundamentally iterative or closed-loop.

The geometry of the diagram must reflect the actual computational logic.

---

## 3. Highlight the Core Novelty

The viewer should understand the paper's main idea within several seconds.

Use visual hierarchy to make the novel component immediately identifiable.

The most important mechanism should:

* occupy the visual center;
* have slightly stronger visual emphasis;
* contain enough internal structure to explain how it works;
* clearly show its inputs, outputs, and feedback signals.

Generic components should be visually secondary.

Do NOT allow peripheral modules to dominate the figure.

---

## 4. Arrow and Data-Flow Requirements

Arrows are semantically important.

Every major arrow must have a clear direction and purpose.

Use:

* solid arrows for the main computational/data flow;
* curved arrows for feedback or iterative updates when appropriate;
* dashed arrows only when representing optional, indirect, auxiliary, or conceptual relationships.

Important arrows may contain short labels such as:

* Task Data
* Context
* Prediction
* Feedback
* Loss
* Gradient
* Parameter Update
* Adapted Parameters
* Re-evaluation

Avoid:

* ambiguous arrow directions;
* crossing arrows;
* arrows ending between modules;
* decorative arrows without semantic meaning;
* unnecessary bidirectional arrows.

For closed-loop methods, make the loop visually unmistakable.

---

## 5. Internal Module Design

Do not represent every component as an identical empty rectangle.

For major modules, visualize meaningful internal structure when useful.

Examples:

* dataset → split / sampling;
* model → frozen backbone + trainable adapter;
* adaptation → forward → feedback/loss → update;
* evaluation → prediction → metric;
* iterative method → proposal → evaluation → update → next iteration.

However, keep the number of internal elements small enough that the figure remains readable.

Prefer abstraction over implementation detail.

---

## 6. Academic Visual Style

Use a clean, modern, publication-quality **flat vector illustration style**.

Target aesthetic:

* DeepMind / OpenAI / NeurIPS / ICML paper figures;
* professional scientific visualization;
* minimalist and precise;
* visually polished but not decorative.

Use:

* white or very light background;
* approximately 3–4 harmonious professional colors;
* pastel or moderately saturated academic colors;
* consistent color semantics across the figure;
* rounded rectangles with subtle borders;
* clean sans-serif typography;
* strong spacing and alignment;
* clear grouping;
* moderate whitespace;
* consistent line width;
* restrained visual hierarchy.

The figure should remain understandable when scaled down to fit a two-column academic paper.

---

## 7. Typography

All text must be:

* correctly spelled;
* horizontally aligned;
* legible;
* concise;
* consistent in font style.

Use short academic labels instead of sentences.

Prefer labels such as:

"Task Data"
"Cross-Fitting"
"Adaptation"
"Feedback"
"LoRA Update"
"Evaluation"

rather than long explanatory prose.

Do not generate tiny text.

Do not include unnecessary titles, legends, equations, or captions inside the image unless they are essential.

---

## 8. Visual Hierarchy

Use approximately three levels of hierarchy:

**Level 1 — Core mechanism**
The main contribution.

**Level 2 — Major stages**
The main processing stages surrounding the core.

**Level 3 — Internal details**
Small subcomponents required to explain the mechanism.

Components at the same semantic level should have consistent size and styling.

Related modules should be spatially grouped.

---

## 9. Negative Constraints

Strictly avoid:

* photorealistic rendering;
* 3D objects;
* glossy UI components;
* heavy shadows;
* dramatic lighting;
* neon glow;
* rainbow gradients;
* cartoon style;
* hand-drawn sketch style;
* decorative icons unrelated to the algorithm;
* unnecessary humans or robots;
* random mathematical formulas;
* excessive text;
* excessively dense diagrams;
* tangled arrows;
* overlapping labels;
* inconsistent module sizes;
* meaningless visual decorations;
* PowerPoint-style business infographic aesthetics.

Do NOT invent modules, algorithms, equations, variables, or experimental results that are not supported by the provided method.

Do NOT add generic AI decorations merely to fill empty space.

---

## 10. Information Filtering

A good academic figure is selective.

If a component does not help explain the central mechanism, remove it.

In particular, do not automatically include:

* generic pretraining stages;
* generic downstream prediction;
* generic datasets;
* deployment;
* unrelated baselines;
* experimental metrics;

unless they are necessary for understanding the proposed method.

The figure should explain **how the proposed method works**, not summarize the entire paper.

---

## 11. Final Visual Inspection

Before finalizing the image, verify:

1. Are all essential modules present?
2. Is any unnecessary module distracting from the contribution?
3. Are all arrows logically correct?
4. Is the main data flow immediately understandable?
5. If there is a feedback loop, is it visually obvious?
6. Is the central novelty visually dominant?
7. Are module names readable and correctly spelled?
8. Are there any crossing or ambiguous arrows?
9. Is there sufficient whitespace?
10. Does the figure look like a top-tier academic paper figure rather than a presentation slide?

If any of these conditions are violated, revise the composition before producing the final image.

---

## Research Method to Visualize

Below is the research content.

Read it carefully, identify the true core mechanism, and generate the figure based on the methodology rather than mechanically copying the wording.

[PASTE ABSTRACT / METHOD / YOUR DESCRIPTION HERE]

---

## Additional Author Instructions

The following requirements override any conflicting assumptions you make:

[WRITE YOUR FIGURE-SPECIFIC REQUIREMENTS HERE]

Examples:

* Focus only on the central adaptation loop.
* Do not show the pretrained model stage.
* Do not show the final downstream prediction stage.
* Emphasize the interaction between task data, adaptation feedback, and parameter update.
* Use a compact horizontal layout.
* Keep the number of major blocks below six.
* The feedback loop must be visually dominant.

Directly generate the final academic figure.

````
