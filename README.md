# 🛡️ DeFi Risk Guardian - AI驱动的DeFi风险预警工具

一个基于AI的去中心化金融风险检测和预警系统，支持实时交易监控、智能风险分析和自动化风险控制。

## ✨ 项目特色

- 🤖 **AI驱动风险检测**: 集成通义千问AI，提供智能风险分析
- 🔄 **实时交易监控**: 3秒延迟容忍的实时区块链交易监控
- 🌐 **多链支持**: 支持以太坊、Holesky、BSC、Polygon等多个区块链网络
- 📊 **可视化界面**: 现代化Web3界面，实时数据展示
- 🔒 **智能合约安全**: 基于OpenZeppelin的安全智能合约
- ⚡ **高性能架构**: WebSocket实时通信，Redis缓存优化

## 🏗️ 技术栈

### 前端
- **React 18** + **TypeScript** + **Vite**
- **Ant Design** + **TailwindCSS** + **Framer Motion**
- **Ethers.js** + **Web3** + **Zustand**

### 后端
- **Node.js** + **Express** + **Socket.IO**
- **MongoDB** + **Redis** + **Winston**
- **Web3.js** + **Ethers.js**

### 区块链
- **Hardhat** + **Solidity 0.8.20**
- **OpenZeppelin** 合约库

### AI服务
- **通义千问(Qwen)** API集成

## 📋 环境要求

- **Node.js**: >= 18.0.0
- **pnpm**: >= 8.0.0 (推荐使用pnpm)
- **MongoDB**: >= 5.0
- **Redis**: >= 6.0 (可选，用于缓存优化)
- **Git**: 最新版本

## 🚀 快速启动

### 1. 克隆项目

```bash
git clone <项目地址>
cd ETHxAI黑客松
```

### 2. 安装依赖

```bash
# 安装根目录依赖
pnpm install

# 安装后端依赖
cd backend
pnpm install

# 安装前端依赖
cd ../frontend-react
pnpm install

# 返回根目录
cd ..
```

### 3. 环境配置

#### 后端环境配置
```bash
# 复制环境配置模板
cp backend/.env.example backend/.env
```

编辑 `backend/.env` 文件：
```env
# 数据库配置
MONGODB_URI=mongodb://localhost:27017/Hark

# 通义千问AI配置
QWEN_API_KEY=your_qwen_api_key_here
QWEN_BASE_URL=https://dashscope.aliyuncs.com/compatible-mode/v1
QWEN_MODEL=qwen-plus

# 区块链网络配置
WEB3_PROVIDER_URL=https://ethereum-holesky-rpc.publicnode.com
ETHEREUM_API_KEY=your_etherscan_api_key_here

# 服务配置
PORT=3001
NODE_ENV=development

# Redis配置 (可选)
REDIS_URL=redis://localhost:6379

# 私链配置
PRIVATE_CHAIN_URL=http://localhost:8545
CHAIN_ID=1337
PRIVATE_KEY=your_private_key_here
```

#### 前端环境配置
```bash
# 复制环境配置模板
cp frontend-react/.env.example frontend-react/.env
```

编辑 `frontend-react/.env` 文件：
```env
VITE_API_URL=http://localhost:3001
VITE_WS_URL=ws://localhost:3001
```

### 4. 启动数据库服务

#### MongoDB
```bash
# 使用Docker启动MongoDB
docker run -d --name mongodb -p 27017:27017 mongo:latest

# 或者使用本地安装的MongoDB
mongod --dbpath /path/to/your/db
```

#### Redis (可选)
```bash
# 使用Docker启动Redis
docker run -d --name redis -p 6379:6379 redis:latest

# 或者使用本地安装的Redis
redis-server
```

### 5. 编译智能合约

```bash
# 编译合约
pnpm run compile

# 启动本地区块链节点 (新终端)
pnpm run node

# 部署合约到本地网络 (新终端)
pnpm run deploy:local
```

### 6. 启动应用

#### 方式一：同时启动前后端 (推荐)
```bash
pnpm run dev
```

#### 方式二：分别启动
```bash
# 启动后端 (终端1)
pnpm run backend:dev

# 启动前端 (终端2)  
pnpm run frontend:dev
```

### 7. 访问应用

- **前端界面**: http://localhost:5174
- **后端API**: http://localhost:3001
- **API文档**: http://localhost:3001/api
- **健康检查**: http://localhost:3001/health

## 🔧 开发指南

### 项目结构
```
ETHxAI黑客松/
├── contracts/                 # 智能合约
├── backend/                  # 后端服务
│   ├── src/
│   │   ├── services/        # 核心服务
│   │   ├── routes/         # API路由
│   │   ├── models/         # 数据模型
│   │   └── config/         # 配置文件
│   └── server.js           # 服务器入口
├── frontend-react/          # React前端
│   ├── src/
│   │   ├── components/     # React组件
│   │   ├── hooks/         # 自定义Hooks
│   │   ├── services/      # API服务
│   │   └── stores/        # 状态管理
│   └── vite.config.ts     # Vite配置
└── scripts/               # 部署脚本
```

### 可用脚本

#### 根目录脚本
```bash
pnpm run dev              # 同时启动前后端开发服务器
pnpm run build            # 构建前后端项目
pnpm run test             # 运行所有测试
pnpm run compile          # 编译智能合约
pnpm run deploy:local     # 部署合约到本地网络
pnpm run deploy:private   # 部署合约到私链
pnpm run node             # 启动Hardhat本地节点
```

#### 后端脚本
```bash
cd backend
pnpm run dev              # 启动开发服务器
pnpm run start            # 启动生产服务器
pnpm run test             # 运行测试
pnpm run backup           # 备份数据
pnpm run restore          # 恢复数据
```

#### 前端脚本
```bash
cd frontend-react
pnpm run dev              # 启动开发服务器
pnpm run build            # 构建生产版本
pnpm run preview          # 预览构建结果
pnpm run lint             # 代码检查
```

## 🔌 API接口

### 主要API端点

#### AI监控相关
- `GET /api/ai-monitoring/status` - 获取监控状态
- `POST /api/ai-monitoring/start` - 启动监控
- `POST /api/ai-monitoring/stop` - 停止监控
- `POST /api/ai-monitoring/analyze-transaction` - 分析交易
- `GET /api/ai-monitoring/realtime` - 获取实时数据

#### 风险分析相关
- `POST /api/risk-analysis/analyze-contract` - 分析合约风险
- `GET /api/risk-analysis/history` - 获取分析历史

#### 聊天相关
- `POST /api/chat/send` - 发送消息给AI
- `GET /api/chat/history` - 获取聊天历史

### WebSocket事件
- `newTransaction` - 新交易事件
- `riskAlert` - 风险预警事件
- `monitoringUpdate` - 监控状态更新

## 🧪 测试

### 运行测试
```bash
# 运行所有测试
pnpm run test

# 运行后端测试
cd backend && pnpm test

# 运行前端测试
cd frontend-react && pnpm test
```

### API测试
```bash
# 测试后端API
cd backend
node test-api.js

# 测试AI集成
node test-qwen-blockchain.js

# 测试监控服务
node test-monitoring-service.js
```

## 📦 部署

### 生产环境部署

#### 1. 构建项目
```bash
pnpm run build
```

#### 2. 环境配置
更新生产环境的环境变量：
- 数据库连接字符串
- AI服务API密钥
- 区块链网络配置
- 安全密钥等

#### 3. 部署到服务器
```bash
# 使用PM2部署后端
cd backend
pm2 start ecosystem.config.js

# 部署前端静态文件到CDN或静态服务器
cd frontend-react
pnpm run build
# 将dist目录内容部署到Web服务器
```

### Docker部署 (推荐)
```bash
# 构建Docker镜像
docker-compose build

# 启动所有服务
docker-compose up -d
```

## 🛠️ 故障排除

### 常见问题

#### 1. 依赖安装失败
```bash
# 清理缓存重新安装
pnpm store prune
rm -rf node_modules
pnpm install
```

#### 2. 数据库连接失败
- 检查MongoDB服务是否启动
- 验证连接字符串是否正确
- 检查防火墙设置

#### 3. 智能合约部署失败
- 确保本地节点正在运行
- 检查账户余额是否充足
- 验证网络配置

#### 4. AI服务调用失败
- 检查通义千问API密钥
- 验证网络连接
- 查看API调用限制

### 日志查看
```bash
# 查看后端日志
tail -f backend/logs/combined.log

# 查看错误日志
tail -f backend/logs/error.log
```

## 🤝 贡献指南

1. Fork 项目
2. 创建功能分支 (`git checkout -b feature/AmazingFeature`)
3. 提交更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 开启 Pull Request

### 提交规范
使用约定式提交格式：
```
feat: 添加新功能
fix: 修复bug
docs: 更新文档
style: 代码格式调整
refactor: 代码重构
test: 添加测试
chore: 构建过程或辅助工具的变动
```

## 📄 许可证

本项目采用 MIT 许可证 - 查看 [LICENSE](LICENSE) 文件了解详情。

## 🙏 致谢

- [OpenZeppelin](https://openzeppelin.com/) - 智能合约安全库
- [Hardhat](https://hardhat.org/) - 以太坊开发环境
- [Ant Design](https://ant.design/) - React UI组件库
- [通义千问](https://tongyi.aliyun.com/) - AI服务支持

## 📞 联系我们

- 项目地址: [GitHub Repository]
- 问题反馈: [GitHub Issues]
- 邮箱: [your-email@example.com]

---

⭐ 如果这个项目对你有帮助，请给我们一个星标！
