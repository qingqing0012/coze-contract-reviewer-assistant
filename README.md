# 合同审阅助手

> 商业/法律风险识别 + 逐条修改建议

智能审阅合同文档，从商业、法律、合规等多维度识别风险点，并给出具体修改建议。

## 工作流架构

```mermaid
flowchart TB
    INPUT([📋 输入: 合同文本]) --> PARSE[🔍 流程4: 解析合同<br/>提取标题 + 甲方公司]

    INPUT --> REVIEW1[📝 流程2: 常规审查<br/>条款完整性·表述清晰度·逻辑矛盾]

    INPUT --> REVIEW2[⚖️ 流程3: 法律引用审查<br/>法条引用准确性·合规性]

    REVIEW1 --> RISK
    REVIEW2 --> RISK
    PARSE --> RISK

    RISK[⚠️ 流程4.3: 企业风险总结<br/>商业风险·法律风险·其他风险]

    RISK --> OUTPUT[📄 输出审查报告<br/>问题 → 分析 → 修改建议]

    style INPUT fill:#e1f5fe
    style REVIEW2 fill:#fff3e0
    style RISK fill:#fce4ec
    style OUTPUT fill:#e8f5e9
```

### 设计要点

- **三维审查**：常规审查（条款完整性） + 法律审查（法条合规性） + 商业审查（企业风险）
- **严格输出格式**：强制「问题 → 分析 → 修改建议」框架，避免 LLM 随意发挥
- **法条引用**：引用《民法典》等具体法条，增强建议可信度

## 功能特性

- 商业风险识别（付款条款、违约责任等）
- 法律风险识别（管辖权、仲裁条款等）
- 其他风险识别（数据安全、知识产权等）
- 逐条给出修改建议与替换措辞

## 项目结构

```
├── README.md
├── .gitignore
├── agent/
│   ├── prompt.md              # 主提示词
│   ├── workflow-prompts.md    # 工作流内嵌 Prompt
│   └── config.yaml
└── workflows/
    └── ht_0429.yaml
```

## 平台

基于 [Coze（扣子）](https://www.coze.com) 构建。

## 快速体验

👉 https://www.coze.cn/s/m75ilHMA104/
