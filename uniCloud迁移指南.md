# uniCloud迁移指南

## 背景

本项目最初基于uniCloud开发，为了提高系统的可扩展性和性能，现已将数据存储从uniCloud迁移到MySQL数据库。

## 数据库表结构

已创建以下表结构：

- `users` - 用户表（对应uni-id-users）
- `tv_member_info` - 会员信息表
- `tv_member_levels` - 会员等级表
- `tv_user_balance` - 用户余额表
- `tv_rebate_records` - 返利记录表
- `uni_id_log` - 登录日志表

## 迁移步骤

1. 创建MySQL数据库和表结构
2. 导出uniCloud数据
3. 转换数据格式
4. 导入MySQL数据库
5. 修改应用代码，适配MySQL

## 本地开发环境配置

1. 安装MySQL数据库
2. 导入初始数据（使用`src/db/mysql-init.sql`）
3. 配置数据库连接（修改`src/common/db-config.js`）

```javascript
// src/common/db-config.js
export default {
  host: 'localhost',
  port: 3306,
  user: 'root',
  password: 'your_password',
  database: 'tv_one_app'
};
```

## API适配层

为了平滑过渡，我们实现了API适配层，可以在本地开发时使用Mock数据或MySQL数据：

```javascript
// src/common/api-adapter.js
import { isMockMode } from './utils';
import * as mockApi from './mock-api';
import * as localApi from './local-api';

export default function(apiName, params) {
  if (isMockMode()) {
    return mockApi[apiName](params);
  } else {
    return localApi[apiName](params);
  }
}
```

## 注意事项

1. 字段命名规则变更：uniCloud使用驼峰命名，MySQL使用下划线命名
2. 数据类型映射：ObjectId -> VARCHAR(32)，Date -> DATETIME
3. 索引设计调整：根据查询需求优化索引

## 测试验证

完成迁移后，请进行以下测试：

1. 用户注册/登录功能
2. 会员信息查询与更新
3. 钱包余额与返利记录
4. 分享赚钱系统

如有问题，请参考`src/db/README.md`获取更多信息。