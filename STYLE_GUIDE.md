---

## PDF-only 交付要求（与 Skill 对齐）

- 最终交付必须是 **PDF**：`.claude-resume/output/<RESUME_FILENAME>.pdf`
- `resume.tex` 仅为中间产物，不得用来替代交付。
- 若编译失败：必须输出明确的报错信息与修复建议，直到成功产出 PDF。

---

## One Page Self-Check（严格一页纸自检）

在最终交付前必须通过以下检查（缺一不可）：

1) **页数 = 1**：使用 `pdfinfo` 或 python 读取 PDF 页数。
2) **无空 bullet / 占位符**：不得出现孤立的 `•` 或空的 `\item`。
3) **语言一致**：
   - 中文简历：除专有名词/缩写外，不出现英文动词起句（例如 `Owned/Designed/Analyzed ...`）。
   - 英文简历：避免中文句子混入。

未通过 → 必须进入 Skill 的“压缩/修复迭代”流程（先改内容，再微调排版）。

---

## 信息密度（模板默认更紧凑）

- 顶部 margin 与 section 间距已较 v6 略缩小（见 `RESUME_TEMPLATE.tex`）。
- 仍超一页时：优先删弱相关内容/压缩 bullets，再作为最后手段做轻微排版微调（避免影响 ATS 可读性）。
