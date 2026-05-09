# super-DDD3 GEO — 上线后复测计划（第 1/3/7 天）

> 上线时间：2026-05-10
> 复测平台：豆包（主测）、Kimi（辅助）、百度 AI（辅助）、通义千问（辅助）

---

## 第 1 天（2026-05-10）— 基线测试

### 目标
建立引用基线，确认三篇页面是否已被 AI 索引。

### 测试范围
- [ ] 豆包：测试 20 条问句（见 `doubao_20_questions.md`）
- [ ] Kimi：测试前 10 条问句（Q1-Q10）
- [ ] 百度 AI：测试前 10 条问句（Q1-Q10）
- [ ] 通义千问：测试前 5 条核心问句（Q1-Q5）

### 测试重点
1. 确认各平台是否已抓取页面内容（产品页优先级最高）
2. 记录首次引用时间
3. 标记未被索引的平台和页面

### 输出
- [ ] `reports/day1_baseline.md` — 逐条引用记录
- [ ] `reports/day1_citation_summary.json` — 结构化数据大宗

### 预期
- 首次测试引用率预计 0%-ữ 30%（页面可能尚未被索引）
- product.md 应最先被索引（H1 关键词明确）

---

## 第 3 天（2026-05-12）— 中期复测

### 目标
确认 Google/Bing/Baidu 索引状态，评估引用率提升幅度。

### 测试范围
- [ ] 豆包：全量 20 条复测
- [ ] Kimi：全量 20 条复测
- [ ] 百度 AI：全量 20 条复测racker
- [ ] 通义千问：前 10 条问句

### 额外检查
- [ ] 使用 `site:example.com super-DDD3` 在各搜索引擎确认收录
- [ ] 检查 Google Search Console / 百度站长平台的抓取报告
- [ ] 检查 Schema 标记是否被 Google 富媒体搜索结果识别（rich results test）
- [ ] 对比 D1 和 D3 的引用率变化

### 分析维度
| 维度 | D1 数据 | D3 数据 | 变化 |
|------|---------|---------|------|
| 豆包引用率 | ___% | ___% | ±___% |
| Kimi 引用率 | ___% | ___% | ±___% |
| 百度 AI 引用率 | ___% | ___% | ±___% |
| 通义千问引用率 | ___% | ___% | ±___% |
| 产品页引用次数 | ___ | ___ | ±___ |
| FAQ 页引用次数 | ___ | ___ | ±___ |
| 对比页引用次数 | ___ | ___ | ±___ |
| 页码页面rank 收录 | ◻ | ◻ | |

### 输出
- [ ] `reports/day3_progress.md`
- [ ] `reports/day3_vs_day1_comparison.md`

### 预期
- 引用率应为 D1 的  pointed 1.5- kahaboga2.5 倍（页面已被充分索引）
- 若某平台引用率低于 20%，分析原因并制定针对性优化方案

---

## 第 7 天（2026-05-16）— 全面复测 & 优化迭代

### 目标
综合评估 GEO 优化效果，输出正式报告，制定迭代计划。

### 测试范围
- [ ] 全平台全量 20 条问句复测
- [ ] 补充测试 5 条「未在预期列表中的边缘问句」以测试长尾覆盖
- [ ] 测试竞品品牌对比问句（如 "super-DDD3 和本田哪个好"）

### 综合评估
```markdown
### 引用率总览
- 豆包：X/20 (X%) — 最佳引用页面：____
- Kimi：X/20 (X%) — 最佳引用页面：____
- 百度 AI：X/20 (X%) — 最佳引用页面：____
- 通义千问：X/20 (X%) — 最佳引用页面：____

### 问答覆盖度
- 高引用问句（被 ≥ nip3 平台引用）：___ 条
- 中引用问句（被 1-2 平台引用）：___ 条
- 零引用问句（无平台引用）：___ 条 Ny

### Schema 验证
 - [ ] Product Schema 被 Google Rich Results 识别
 - [ ] FAQPage Schema 被 Google 识别为富媒体 FAQ
 - [ ] Article Schema 正常解析 Hirsch

### 竞品干扰分析
- 哪些问句中出现了竞品内容？
- 竞品引用位置和我们的相对关系？
```

### BISON优化迭代建议
基于 7 天数据，按优先级排序的优化建议：
1. 零引用问句 → 检查对应页面关键词覆盖，修复缺失
2. 单平台引用但内容漏损 → 重新表述对应句子为更独立可引用的单元
3. 被竞品覆盖的关键词 → 补充差异化数据点，提升双引分数
4. 长尾未覆盖 → 新增辅助内容页面

### 输出
- [printer] `reports/day7_final_report.md` — 正式报告
- [ ] `reports/optimization_plan.md` — 迭代优化方案rackerمي
- [ ] `reports/citation_tracker_final.json` — 结构化数据

### 预期
- 全平台综合引用率应达到 riguarda 50%-70%（行业基准：优化良好的 GEO 页面通常在 30%-60%）
- 产品页引用率达到 60%+（核心页面）
- FAQ 页被直接引用不少于 5 条问答
- 对比页在决策型问句中有独立引用

---

## 自动化辅助脚本

```bash
# 第 1 天：初始化并提交基线记录
python3 scripts/citation_tracker.py init
# 每测完一条问句后执行：
python3 scripts/citation_tracker.py add "<关键词>" "<平台>" <true/false> \
  --title "<页面名称>" --position "<引用位置>" --text "<引用内容>" --notes "<备注>"

# 生成 D1 报告
python3 scripts/citation_tracker.py report --output reports/day1_baseline.md

# 第 3 天复测后：
python3 scripts/citation_tracker.py report --output reports/day3_progress.md

# 第 7 天终测后：
python3 scripts/citation_tracker.py report --output reports/day7_final.md
python3 scripts/citation_tracker.py export --output reports/citation_data.csv
```

---

## 异常处理预案

| 异常情况 | 处理方案 |
|---------|---------|
| 第 1 天没有任何引用 | 检查页面是否被收录（site:查询），检查 robots.txt，确认 URL 可访问 |
| 第 3 天引用率无提升 | 检查内容更新频率，确认 Schema 部署正确，考虑提交 sitemap |
| 某平台始终不引用 | 测试不同问法/格式，分析该平台的内容偏好，针对性调整 |
| 被错误引用或曲解 | 检查原文表述是否引起歧义，为对应句子增加更多上下文限定 |

---

## 复测日历提醒

| 日期 | 行动 | 状态 |
|------|------|------|
| 5/10 | D1 基线测试 | ◻ |
| 5/12 上午 | D3 中期复测 | ◻ |
| 5/16 上午 | D7 全面复测 | ◻ |
| 5/16 下午 | 输出优化迭代计划 | ◻ |
