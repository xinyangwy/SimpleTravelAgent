# SimpleTravelAgent

一个基于大语言模型的智能旅行助手，能够查询天气并根据天气情况推荐旅游景点。

## 功能特点

- 查询指定城市的实时天气
- 根据天气条件推荐合适的旅游景点
- 使用ReAct（Reasoning and Acting）模式进行多步推理

## 安装与配置

1. 克隆项目到本地
2. 创建并激活虚拟环境
3. 安装依赖
4. 配置环境变量
5. 运行项目

### 详细步骤

```bash
# 1. 克隆项目
git clone <repository-url>
cd SimpleTravelAgent

# 2. 创建并激活虚拟环境
python -m venv venv
# Windows
venv\Scripts\activate
# Linux/Mac
source venv/bin/activate

# 3. 安装依赖
pip install -r requirements.txt

# 4. 配置环境变量
cp .env.example .env
# 编辑.env文件，填入你的API密钥

# 5. 运行项目
python main.py
```

## 环境变量配置

在项目根目录下创建`.env`文件，并填入以下配置：

```env
# OpenAI API配置
OPENAI_API_KEY=your_openai_api_key_here
OPENAI_MODEL=gpt-3.5-turbo
OPENAI_BASE_URL=https://api.openai.com/v1

# Tavily API配置
TAVILY_API_KEY=your_tavily_api_key_here

# 系统提示词
AGENT_SYSTEM_PROMPT="""你是一个智能旅行助手..."""
```

## 项目结构

```
SimpleTravelAgent/
├── main.py                 # 主程序入口
├── weather_search.py       # 天气查询工具
├── search_attraction.py    # 景点推荐工具
├── OpenAICompatibleClient.py # OpenAI兼容的LLM客户端
├── .env.example           # 环境变量示例
├── requirements.txt       # 项目依赖
└── README.md             # 项目说明
```

## 工作原理

项目采用ReAct（Reasoning and Acting）模式：

1. **思考（Thought）**：LLM分析当前情况并决定下一步行动
2. **行动（Action）**：调用相应的工具函数
3. **观察（Observation）**：获取工具执行结果并反馈给LLM

通过循环这个过程，智能体能够逐步完成复杂任务。

## API说明

### 天气查询API

使用wttr.in服务查询天气信息，无需API密钥。

### 景点推荐API

使用Tavily Search API进行智能搜索，需要申请API密钥。

## 注意事项

1. 确保已正确配置所有必需的API密钥
2. 网络连接正常，能够访问外部API
3. 如果使用其他LLM服务，请修改相应的API配置

## 许可证

[MIT License](LICENSE)