# 市场调研数据分析平台

一个完整的市场数据采集、分析和可视化平台，支持股票、加密货币等多数据源。

## 🎯 功能特性

- 📊 **实时数据采集** - 从多个数据源采集市场数据
- 📈 **数据分析** - Pandas 数据处理和统计分析
- 🎨 **可视化仪表板** - React + ECharts 交互式图表
- 🔄 **定时任务** - Celery 后台任务调度
- 💾 **数据持久化** - PostgreSQL 数据库
- 🐳 **容器化部署** - Docker 和 Docker Compose
- 🔐 **用户认证** - JWT 身份验证
- 📱 **响应式设计** - 支持桌面和移动设备

## 📦 技术栈

### 后端
- **FastAPI** - 高性能 Python Web 框架
- **SQLAlchemy** - ORM 数据库
- **Pandas** - 数据处理和分析
- **Celery** - 后台任务队列
- **Redis** - 缓存和消息队列
- **Pydantic** - 数据验证

### 前端
- **React 18** - UI 框架
- **Axios** - HTTP 客户端
- **ECharts** - 数据可视化
- **Ant Design** - UI 组件库
- **React Router** - 路由管理

### 数据库
- **PostgreSQL** - 主数据库
- **Redis** - 缓存层

### 其他
- **Docker** - 容器化
- **Docker Compose** - 多容器编排

## 🚀 快速开始

### 前置要求
- Docker 和 Docker Compose
- Python 3.9+（本地开发）
- Node.js 16+（本地开发）

### 使用 Docker Compose（推荐）

```bash
# 克隆项目
git clone <repo-url>
cd market-research-platform

# 启动所有服务
docker-compose up -d

# 初始化数据库
docker-compose exec backend python -m alembic upgrade head

# 访问应用
# 前端: http://localhost:3000
# API 文档: http://localhost:8000/docs
```

### 本地开发

#### 后端
```bash
cd backend
python -m venv venv
source venv/bin/activate  # Windows: venv\\Scripts\\activate
pip install -r requirements.txt

# 启动 API
uvicorn app.main:app --reload

# 启动 Celery 工作进程
celery -A app.tasks worker --loglevel=info
```

#### 前端
```bash
cd frontend
npm install
npm start
```

## 📁 项目结构

```
market-research-platform/
├── backend/
│   ├── app/
│   │   ├── main.py              # FastAPI 应用入口
│   │   ├── config.py            # 配置管理
│   │   ├── database.py          # 数据库连接
│   │   ├── models/              # 数据模型
│   │   ├── schemas/             # Pydantic 数据验证
│   │   ├── routes/              # API 路由
│   │   ├── services/            # 业务逻辑
│   │   ├── tasks/               # Celery 任务
│   │   └── utils/               # 工具函数
│   ├── tests/                   # 测试
│   ├── requirements.txt         # Python 依赖
│   ├── .env.example             # 环境变量模板
│   └── Dockerfile
├── frontend/
│   ├── public/
│   ├── src/
│   │   ├── components/          # React 组件
│   │   ├── pages/               # 页面
│   │   ├── services/            # API 调用
│   │   ├── App.jsx
│   │   └── index.js
│   ├── package.json
│   ├── .env.example
│   └── Dockerfile
├── docker-compose.yml
├── nginx.conf
└── README.md
```

## 🔌 API 端点

### 认证
- `POST /api/auth/register` - 用户注册
- `POST /api/auth/login` - 用户登录
- `POST /api/auth/refresh` - 刷新 Token

### 市场数据
- `GET /api/market/stocks` - 获取股票数据
- `GET /api/market/crypto` - 获取加密货币数据
- `GET /api/market/{symbol}` - 获取特定符号数据

### 分析
- `GET /api/analysis/summary` - 获取分析摘要
- `GET /api/analysis/trends` - 获取趋势分析
- `POST /api/analysis/report` - 生成分析报告

## 📊 数据源

### 免费 API
- **Alpha Vantage** - 股票数据
- **CoinGecko** - 加密货币数据
- **Yahoo Finance** - 财务数据

## 🔐 环境变量

复制 `.env.example` 为 `.env` 并配置：

```bash
# 数据库
DATABASE_URL=postgresql://user:password@db:5432/market_db

# Redis
REDIS_URL=redis://redis:6379

# JWT
JWT_SECRET_KEY=your-secret-key-here
JWT_ALGORITHM=HS256

# API 密钥
ALPHA_VANTAGE_API_KEY=your_key

# 应用
APP_NAME=Market Research Platform
DEBUG=False
```

## 🧪 测试

```bash
# 后端测试
cd backend
pytest

# 前端测试
cd frontend
npm test
```

## 🚢 部署

### 生产环境部署

```bash
# 使用 docker-compose 在生产环境部署
docker-compose -f docker-compose.prod.yml up -d
```

## 📞 支持

- 提交 Issue 报告 bug
- 讨论区提出建议

---

**开始构建你的市场分析平台吧！** 🚀
