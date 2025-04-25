# TV-One-App

## 项目概述
这是一个基于uni-app开发的多平台应用，主要功能包括用户登录注册、会员管理、钱包功能和分享赚钱系统。项目已从uniCloud迁移到MySQL数据库，并提供了本地API模拟后端逻辑。

## 主要功能

- **用户系统**：注册、登录、找回密码、个人信息管理
- **会员系统**：会员等级、会员权益、会员升级
- **钱包功能**：余额查询、返利记录、提现功能
- **分享赚钱**：邀请注册、多级返利、邀请统计

## 技术栈

- 前端框架：uni-app (Vue 2)
- 数据库：MySQL
- 开发语言：JavaScript

## 项目结构

```
src/
├── api/                # API接口层
│   ├── user.js         # 用户相关API
│   ├── member.js       # 会员相关API
│   ├── wallet.js       # 钱包相关API
│   └── share.js        # 分享赚钱相关API
├── services/           # 业务逻辑层
│   ├── userService.js  # 用户服务
│   ├── memberService.js # 会员服务
│   ├── walletService.js # 钱包服务
│   └── shareService.js # 分享赚钱服务
├── dao/                # 数据访问层
├── db/                 # 数据库层
├── common/             # 公共模块
├── components/         # UI组件
├── pages/              # 页面
└── store/              # 状态管理
```

## 开发指南

### 环境准备

1. 安装Node.js环境
2. 安装MySQL数据库
3. 克隆项目代码

```bash
git clone https://github.com/sunOnly/tv-one-app.git
cd tv-one-app
npm install
```

### 数据库配置

1. 创建MySQL数据库
2. 导入初始数据：`src/db/mysql-init.sql`
3. 配置数据库连接：修改`src/common/db-config.js`

### 本地开发

```bash
# 启动开发服务器
npm run serve

# 构建生产版本
npm run build
```

## 文档

- [项目重构方案](./项目重构方案.md)
- [uniCloud迁移指南](./uniCloud迁移指南.md)

## 许可证

[MIT](LICENSE)
