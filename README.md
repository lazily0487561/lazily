# Lazily 微服务开发脚手架

[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.2+-green.svg)](https://spring.io/projects/spring-boot)
[![Spring Cloud](https://img.shields.io/badge/Spring%20Cloud-2023.x-blue.svg)](https://spring.io/projects/spring-cloud)
[![Spring Cloud Alibaba](https://img.shields.io/badge/Spring%20Cloud%20Alibaba-2023.x-orange.svg)](https://github.com/alibaba/spring-cloud-alibaba)

## 项目介绍

```text
Lazily 是一款基于 Spring Cloud Alibaba 的微服务框架的应用开发脚手架。
类似于若依、JeeSite、Spring Boot Admin、Spring Cloud Config 等开源项目，Lazily 也提供了很多开箱即用的功能模块，帮助开发者快速构建微服务应用。
目前已经完成了基础的用户权限管理、代码生成器、在线文档、分布式配置中心、服务注册与发现、服务网关等功能模块。
并且支持了多种数据库（MySQL、Oracle、PostgreSQL、SQL Server、MongoDB、Redis 等）的接入，支持了多种消息中间件（RabbitMQ、Kafka、RocketMQ 等）的接入。
最重要的是，Lazily 还在脚手架中集成了 AI 开发框架，支持了多种 AI 模型的接入（如 GPT-4o、Claude 3、Gemini、LLaMA 3 等），用户也可以自定义 AI 模型的接入。
```

## 技术栈

- **基础框架**：Spring Boot 3.2+、Spring Cloud 2023.x、Spring Cloud Alibaba 2023.x
- **服务注册与发现**：Nacos 2.2+
- **配置中心**：Nacos Config
- **服务网关**：Spring Cloud Gateway
- **安全框架**：Spring Security、JWT
- **数据库**：MySQL、Oracle、PostgreSQL、SQL Server、MongoDB
- **缓存**：Redis
- **消息中间件**：RabbitMQ 3.12+、Kafka 3.6+、RocketMQ 5.1+
- **服务监控**：Spring Boot Admin 3.2+、Prometheus 2.48+、Grafana 10.2+
- **链路追踪**：SkyWalking 9.7+、OpenTelemetry
- **分布式事务**：Seata 2.0+
- **AI 集成**：OpenAI API (GPT-4o)、Claude API (Claude 3)、Gemini API、LLaMA 3

## 项目结构

```
lazily
├── lazily-common               -- 公共模块
│   ├── lazily-common-core      -- 核心模块
│   ├── lazily-common-redis     -- Redis模块
│   ├── lazily-common-log       -- 日志模块
│   ├── lazily-common-security  -- 安全模块
│   └── lazily-common-swagger   -- Swagger文档模块
├── lazily-gateway              -- 网关服务
├── lazily-auth                 -- 认证服务
├── lazily-modules              -- 业务模块
│   ├── lazily-system           -- 系统管理模块
│   ├── lazily-gen              -- 代码生成模块
│   ├── lazily-job              -- 定时任务模块
│   ├── lazily-file             -- 文件服务模块
│   └── lazily-ai               -- AI服务模块
├── lazily-monitor              -- 监控服务
│   ├── lazily-monitor-admin    -- Spring Boot Admin服务监控
│   └── lazily-monitor-skywalking -- SkyWalking链路追踪
├── lazily-visual               -- 图表模块
└── doc                         -- 项目文档
```

## 环境要求

- JDK 17+
- Maven 3.9+
- MySQL 8.4+/Oracle 23c+/PostgreSQL 16+/SQL Server 2022+
- Redis 8.0+
- Nacos 2.2+
- Node.js 20+ (前端开发)

## 快速开始

### 环境准备

1. 安装并启动 Nacos 服务
2. 安装并启动 MySQL 服务
3. 安装并启动 Redis 服务

### 后端部署

1. 克隆代码

```bash
git clone https://github.com/....../lazily.git
```

2. 导入数据库脚本（位于 doc/sql 目录）

```bash
mysql -u root -p lazily < doc/sql/lazily.sql
```

3. 修改配置

根据您的环境修改各模块中的 `application.yml` 和 `bootstrap.yml` 文件，配置数据库、Redis、Nacos等信息。

4. 编译部署

```bash
cd lazily
mvn clean package -DskipTests
```

5. 启动服务

按照以下顺序启动各模块：
- Nacos
- lazily-gateway
- lazily-auth
- 其他业务模块

### 前端部署

1. 进入前端目录

```bash
cd lazily-ui
```

2. 安装依赖

```bash
npm install
```

3. 开发模式运行

```bash
npm run dev
```

4. 构建生产环境

```bash
npm run build:prod
```

## 模块功能说明

### 系统管理模块

- 用户管理：用户是系统操作者，该功能主要完成系统用户配置
- 部门管理：配置系统组织机构（公司、部门、小组），树结构展现支持数据权限
- 岗位管理：配置系统用户所属担任职务
- 菜单管理：配置系统菜单，操作权限，按钮权限标识等
- 角色管理：角色菜单权限分配、设置角色按机构进行数据范围权限划分
- 字典管理：对系统中经常使用的一些较为固定的数据进行维护
- 参数管理：对系统动态配置常用参数
- 通知公告：系统通知公告信息发布维护
- 操作日志：系统正常操作日志记录和查询
- 登录日志：系统登录日志记录和查询
- 在线用户：当前系统中活跃用户状态监控
- 定时任务：在线（添加、修改、删除）任务调度包含执行结果日志
- 代码生成：前后端代码的生成（java、html、xml、sql）支持CRUD下载
- 系统接口：根据业务代码自动生成相关的api接口文档

### AI服务模块

- 模型管理：配置多种AI模型接入
- 对话管理：提供AI对话功能
- 提示词管理：维护常用提示词模板
- 知识库管理：构建专属知识库供AI调用
- AI助手：开发者助手，智能代码生成和问题解答

## 常见问题

### 无法连接到Nacos服务
- 检查Nacos服务是否启动
- 检查配置文件中的Nacos地址是否正确
- 检查网络连通性

### 数据库连接异常
- 检查数据库服务是否启动
- 检查账号密码是否正确
- 检查数据库表是否已导入

## 参与贡献

1. Fork 本仓库
2. 新建 feature_xxx 分支
3. 提交代码
4. 新建 Pull Request

## 开源协议

[MIT License](LICENSE)
