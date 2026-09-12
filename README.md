<p align="center">
  <img src="assets/banner.svg" width="100%" alt="BioLit Agent —— 生物医学 × 计算 文献自动追踪 + AI 深度精读模板">
</p>

<h1 align="center">protein-structure-ai — 蛋白质结构 × AI</h1>

<p align="center">
  <strong>生物医学 × 计算交叉领域的文献自动追踪 + AI 深度精读模板</strong><br/>
  用 GitHub Actions 按周期自动追踪 <b>PubMed · arXiv · bioRxiv · medRxiv · chemRxiv</b> 上的最新文献，存档落盘、生成 Issue 周报，再用 LLM 为每篇产出「评分 + 一句话 + 摘要翻译 + 16 节 Paper Card + 审稿人评审」，并同步部署一个可全文检索的 GitHub Pages 站点，配合 Zotero 完成筛选与入库。
</p>

<p align="center">
  <img src="https://img.shields.io/badge/pyPaperFlow-powered-7C3AED?style=for-the-badge" alt="pyPaperFlow powered">
  <img src="https://img.shields.io/badge/platforms-PubMed%C2%B7arXiv%C2%B7bioRxiv%C2%B7medRxiv%C2%B7chemRxiv-0EA5E9?style=for-the-badge" alt="Supported platforms">
  <img src="https://img.shields.io/badge/schedule-weekly%C2%B7GitHub%20Actions-0D9488?style=for-the-badge" alt="Weekly via GitHub Actions">
  <img src="https://img.shields.io/badge/AI-LLM%20deep%20reading-F59E0B?style=for-the-badge" alt="LLM deep reading">
  <img src="https://img.shields.io/badge/output-Archive%20%2B%20Discovery%20%2B%20Site-4F46E5?style=for-the-badge" alt="Outputs">
  <img src="https://img.shields.io/badge/reading-Zotero%20ready-10B981?style=for-the-badge" alt="Zotero reading">
</p>



> **模板即实例。** 仓库内的 `config.yaml` 与 `prompts.yaml` 已内置一套完整可跑的示例检索式与提示词 —— 拿到后你只需改**两个文件**：`config.yaml`（换成你的研究领域）与 `prompts.yaml`（换成你领域的措辞）。工具与平台默认面向 **生物医学 × 计算**交叉课题。核心驱动为我们自研的文献检索获取工具 [pyPaperFlow](https://github.com/MaybeBio/pyPaperFlow)。

---


> 由自研文献+Agent推送模板[Daily-Paper-Agent-Template](https://github.com/MaybeBio/Daily-Paper-Agent-Template) 生成

蛋白质结构相关的研究，含结构预测、构象采样、结构设计、序列设计、动力学分析等；方法限定为深度学习、分子动力学与对接。
