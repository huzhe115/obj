# 威星智能仪表 - RAG智能客服系统

基于LangChain + DeepSeek大模型 + Chroma向量数据库的企业级智能客服系统，专为工业仪表行业设计。

## 功能特性

- **RAG检索增强生成**：基于产品知识库回答，有效避免大模型幻觉
- **多轮对话记忆**：自定义FileChatMessageHistory，支持上下文连续问答
- **知识库管理**：支持TXT文档上传、智能分块（1000字符/块+100重叠）、MD5去重
- **实时流式输出**：打字机效果，提升用户体验
- **生产级Prompt设计**：角色扮演、输出约束、兜底逻辑

## 技术栈

| 组件 | 技术 |
|------|------|
| 框架 | LangChain + Streamlit |
| 大模型 | DeepSeek-Chat |
| 向量嵌入 | 阿里云DashScope（text-embedding-v4）|
| 向量数据库 | Chroma（本地持久化）|
| 对话存储 | JSON文件 |

## 项目结构

├── app/
│ ├── app_qa.py # 智能问答界面（Streamlit）
│ └── app_file_uploader.py # 知识库管理界面
├── core/
│ ├── rag.py # RAG链构建
│ ├── knowledge_base.py # 知识库预处理 + MD5去重
│ ├── vector_stores.py # 向量检索封装
│ ├── file_history_store.py # 对话历史持久化
│ └── config_data.py # API配置
└── requirements.txt

## 快速开始

### 1. 克隆仓库

```bash
git clone https://github.com/he110w0rd/rag-customer-service.git
cd rag-customer-service


编辑 core/config_data.py，填入你的API Key：

dashscope_api_key = "sk-xxx"
api_key = "sk-xxx"

上传知识库文档
bash
streamlit run app/app_file_uploader.py

启动问答系统
bash
streamlit run app/app_qa.py
