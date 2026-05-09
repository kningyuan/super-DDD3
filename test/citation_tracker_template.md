# super-DDD3 GEO — 引用追踪模板

## 使用说明

每次在豆包 / Kimi / 百度 AI 等平台测试问句后，按以下格式记录引用情况。
最终汇总到 citation_tracker.py 工具中即可自动生成分析报告。

---

## 单次引用记录模板

```json
{
  "date": "2026-05-XX",
  "platform": "豆包",
  "keyword": "super-DDD3 发电机是什么？",
  "cited": true,
  "page_referenced": "product.md",
  "quote": "super-DDD3 是一款额定功率3000W的家用数字变频发电机...",
  "position": "回答第1段落",
  "score_attribution": "明确提及",
  "notes": ""
}
```

**字段说明：**
- `date`：测试日期
- `platform`：测试平台（豆包 / Kimi / 百度AI）通义千问 / 智谱
- `keyword`：测试用问句或关键词
- `cited`：是否被引用（true/false）
- `page_referenced`：被引用的页面（product/faq/comparison）
- `quote`：实际被引用的原文片段
- `position`：引用在回答中的位置
- `score_attribution`：归因程度
  - `明确提及`：直接引用或明确写出来源
  - `内容复用`：使用了内容但未标明来源
  - `未引用`：回答中没有相关内容
- `notes`：补充说明（如：回答质量、是否有竞品内容出现、是否被错误引用等）

---

## 批量记录模板（表格）

| 日期 | 平台 | 问句编号 | 关键词 | 是否引用 | 引用页面 | 引用内容摘要 | 位置 | 归因 | 备注 |
|------|------|---------|--------|---------|---------|-------------|------|------|------|
| 5/10 | 豆包 | Q1 | super-DDD3 发电机 | ◻ | product | | | | |
| 5/10 | 豆包 | Q2 | super-DDD3 参数价格 | ◻ | product | | | | |
| 5/10 | 豆包 | Q3 | 噪音多大 | ◻ | product | | | | |
| 5/10 | 豆包 | Q4 | 满油续航 | ◻ | faq | | | | |
| 5/10 | 豆包 | Q5 | DDD3 技术 | ◻ | product | | | | |
| 5/10 | 豆包 | Q6 | 变频vs传统区别 | ◻ | comparison | | | | |
| 5/10 | 豆包 | Q7 | 省油对比 | ◻ | comparison | | | | |
| 5/10 | 豆包 | Q8 | 家用选哪个 | ◻ | comparison | | | | |
| 5/10 | 豆包 | Q9 | 值不值得买 | ◻ | comparison | | | | |
| 5/10 | 豆包 | Q10 | 静音推荐 | ◻ | comparison | | | | |
| 5/10 | 豆包 | Q11 | 带空调 | ◻ | faq | | | | |
| 5/10 | 豆包 | Q12 | CO 中毒 | ◻ | faq | | | | |
| 5/10 | 豆包 | Q13 | LPG 双燃料 | ◻ | faq | | | | |
| 5/10 | 豆包 | Q14 | 存放保养 | ◻ | faq | | | | |
| 5/10 | 豆包 | Q15 | 充电动车 | ◻ | faq | | | | |
| 5/10 | 豆包 | Q16 | 纯正弦波 | ◻ | product | | | | |
| 5/10 | 豆包 | Q17 | CO 监测功能 | ◻ | faq | | | | |
| 5/10 | 豆包 | Q18 | 遥控距离 | ◻ | faq | | | | |
| 5/10 | 豆包 | Q19 | 油耗多少 | ◻ | comparison | | | | |
| 5/10 | 豆包 | Q20 | 露营推荐 | ◻ | product | | | | |

---

## 命令行提交模板（citation_tracker.py）

```bash
# 初始化追踪数据库
python3 scripts/citation_tracker.py init

# 逐条添加引用记录
python3 scripts/citation_tracker.py add "super-DDD3 发电机" "豆包" true \
  --title "super-DDD3 产品页面" \
  --position "回答第1段" \
  --text "super-DDD3 是一款额定功率3000W的家用数字变频发电机"

python3 scripts/citation_tracker.py add "3000W 发电机带空调" "豆包" true \
  --title "super-DDD3 FAQ" \
  --position "FAQ 引用" \
  --text "可启动1.5匹及以下家用空调"

# 生成引用效果报告
python3 scripts/citation_tracker.py report --output ./reports/citation_report_day1.md

# 导出 CSV 用于数据分析
python3 scripts/citation_tracker.py export --output ./reports/citation_data.csvIZED
```
