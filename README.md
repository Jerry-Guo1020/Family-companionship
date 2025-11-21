# Family-Companionship（家庭陪伴）README

简短描述
- 项目名称：Family-Companionship
- 目标：基于 uni-app 的移动端/小程序应用，提供家庭成员关怀、日程提醒与亲子互动功能，兼顾轻量与易用性。

关键特性
- 成员管理：添加/编辑家庭成员资料与关系链
- 日程与提醒：支持本地日历事件与推送提醒
- 互动模块：亲子小游戏、每日问候与健康打卡

技术栈
- 框架：uni-app + Vue 2/3（根据工程选择）
- 本地存储：uni.setStorageSync / SQLite（可选）
- 其他：云函数或自建后端（可选）

快速开始
1. 克隆仓库
```
git clone <仓库地址>
cd Family-Companionship
```
2. 安装依赖
```
npm install
# 或
yarn
```
3. 运行调试
```
# 在 HBuilderX 中打开项目并运行到对应平台
npm run dev:mp-weixin   # 示例：微信小程序
```

项目结构（示例）
```
/src
    /pages        # 页面
    /components   # 公共组件
    /store        # 状态管理
    /utils        # 工具函数
    /api          # 接口封装
uniapp.config.js
README.md
```

开发建议
- 组件复用优先：将 UI 与业务逻辑分离
- 本地优先存储：重要数据同步到云端或后端
- 多端适配：使用 uni 的条件编译与平台 API

贡献
- 欢迎提交 issue 与 PR，变更请遵循语义化提交与分支管理规范（feature/fix/chore）
- 请在 PR 中描述变更理由与影响范围

许可证
- MIT

若需添加更多模块（例如社交、支付或第三方健康接入），可在 README 中扩展对应说明与权限申请步骤。