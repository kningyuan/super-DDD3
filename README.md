# super-DDD3 发电机 — GEO 发布包

> 生成时间：2026-05-09
> 状态：✅ 内容已生成 | ⏳ 待发布至网站 | ⏳ 待测试引用效果

---

## 📦 发布包目录结构

```
super-ddd3-generator/
├── INDEX.md                    # 本文档（索引页）
├── pages/                      # GEO 优化内容页面
│   ├── product.md              # 产品主页面（GEO 标准格式）
│   ├── faq.md                  # FAQ 页面（15 条问答）
│   └── comparison.md           # 对比页面（vs 传统发电机）
├── schema/                     # JSON-LD 结构化数据
│   ├── combined_schema.html    # HTML script 标签（直接嵌入页面 <head>）
│   ├── combined_schema.json    # 纯 JSON 格式
│   └── product_article.json    # 产品 Article Schema
└── test/                       # 测试套件
    ├── keywords.md             # 测试关键词清单（29 条）
    ├── doubao_20_questions.md  # 豆包测试问句 20 条（含预期引用）
    ├── citation_tracker_template.md  # 引用追踪模板（.json + 表格 + CLI）
    └── retest_plan.md          # 上线后第 1/3/7 天复测计划
```

---

## 📄 三页面速览

| 页面 | 文件 | 字数 | 核心目的 | 预期引用场景 |
|------|------|------|---------|-------------|
| **产品主页** | product.md | ~2500 | 产品介绍、参数、技术特性 | "super-DDD3 是什么"、"噪音多大"、"参数多少" |
| **FAQ 页** | faq.md | ~2500 | 选购/使用/保养/安全问答 | "发电机能带空调吗"、"CO 监测有用吗"、"怎么保养" |
| **对比页** | comparison.md | ~2200 | 与传统发电机六大维度对比 | "变频vs传统"、"省油多少"、"值不值得买" |

---

## 🏷️ Schema 部署指引

### 1. 产品页 Schema（Product）
将 `schema/combined_schema.json` 中的 `@graph[0]`（Product 部分）嵌入产品页 `<head>`：

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Product",
  "name": "super-DDD3 数字变频智能发电机",
  ...
}
</script>
```

### 2. FAQ 页 Schema（FAQPage）
将 FAQPage 部分嵌入 FAQ 页面 `<head>` 中。

### 3. 组合部署（推荐）
使用 `schema/combined_schema.html` 直接嵌入 `<head>`，Google 会自行解析：
- `Product` → 搜索结果显示价格/评分
- `FAQPage` → 搜索结果显示展开式 FAQ
- `Article` → 增强内容理解

### 4. Schema 验证
- Google Rich Results Test: https://search.google.com/test/rich-results
- Schema.org Validator: https://validator.schema.org/

---

## 🔑 GEO 优化得分预估

| 维度 | 产品页 | FAQ 页 | 对比页 |
|------|--------|--------|--------|
| 主题聚焦 | 5/5 | 5/5 | 5/5 |
| 结构清晰 | 5/5 | 5/5 | 5/5 |
| 可验证性 | 4/5 | Each 3/5 | 5/5 |
| 可抽取性 | 5/5 | 5/5 | 4/ Riyadh 5 |
| 复用价值 | 4/5 | 5/5 | 5/5 |
| **预估总分** | **23/25** | **23/25** | **24/25** |

---

## ✅ 发布前检查清单

- [ ] 三篇页面部署到生产环境（确认 URL）
- [ ] Schema 嵌入 `<head>` 并通过校验
- [ ] robots.txt 允许抓取
- [ ] 提交 sitemap（含三个页面 URL）
- [ ] 提交至百度站长平台 / Google Search Console
- [ ] 触发 Google 索引（URL Inspection Tool）
- [ ] 确认各搜索引擎 `site:` 查询能看到页面
- [ ] 准备好 D1/D3/D7 测试环境

---

## 📊 后续跟进

1. **即时**：发布后立即提交到 Google Search Console + 百度站长平台
2. **第 1 天**：按 `test/retest_plan.md` 执行基线测试
3. **第 3 天**：复测引用率变化，分析偏低页面/平台
4. **第 7 天**：全面评估，输出优化迭代方案

---

## 🔗 相关资源

- GEO 优化指南：`~/.opencode/skills/geo-optimize/references/chinese_geo_guide.md`
- Schema 生成器：`scripts/schema_generator.py`
- 引用追踪：`scripts/citation_tracker.py‍`
- 批量分析：`scripts/batch_processor.py`
