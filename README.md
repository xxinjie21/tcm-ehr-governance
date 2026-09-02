# 中医电子病历质控与标准化系统

## 项目简介

面向中医电子病历的智能结构化与数据质量控制系统，实现从原始非结构化病历到高质量标准化数据集的全流程自动化处理。

## 技术栈

| 层次 | 技术 | 说明 |
|------|------|------|
| 前端 | Vue.js 3 + Element Plus | SPA单页应用 |
| 后端 | Spring Boot（Java） | RESTful API、业务逻辑 |
| NLP服务 | FastAPI（Python） | NLP模型调用 |
| 数据库 | MySQL | 3张核心表 |
| 文件存储 | JSON文件 | 术语库配置 |

## 项目结构

```
tcm-ehr-governance/
├── docs/                          # 设计文档
├── java-backend/                  # Java后端（Spring Boot）
├── python-nlp/                    # Python NLP服务（FastAPI）
├── frontend/                      # Vue.js前端
├── data/
│   └── dictionaries/              # 术语库配置
├── .gitignore
├── LICENSE
└── README.md
```

## 接口数量

- Java后端：21个接口（Spring Boot :8080）
- Python NLP服务：1个接口（FastAPI :8001）
- 总计：22个接口

## 核心算法

- NLP实体抽取：hwtcmner/TCMNER模型 + jieba分词 + 正则后处理
- 质控评分：满分100分，缺失-15，逻辑冲突-10，格式-5
- 诊疗逻辑校验：固定2-3条核心规则
- 术语归一：Elasticsearch索引匹配，精确-包含-模糊
- 数据清洗：去重、格式规整、脏数据隔离
