# AGENTS.md

## 1. 项目上下文

本文件定义 AI Agent 在本项目中的通用开发规范。

AI Agent 开始任何任务前，必须先理解项目当前状态、项目规则、架构、已有实现和相关文档。

本文件适用于：

* 需求分析
* 技术研究
* 架构设计
* UI / UX 设计
* Prototype
* Spec
* Plan
* Tasks
* 编码
* 测试
* Debug
* Code Review
* 文档维护

---

## 2. AI 工作总原则

### 2.1 先理解，再修改

禁止在不了解项目上下文的情况下直接大量修改代码。

开始任务前，应根据任务复杂度检查：

* `AGENTS.md`
* Constitution
* Architecture
* ADR
* Spec
* Prototype
* Plan
* 相关代码
* 相关测试
* 项目配置

---

### 2.2 优先复用现有能力

实现新功能前，先检查项目中是否已经存在：

* 相同或类似功能
* 公共组件
* 公共服务
* 公共工具
* API
* 数据模型
* 状态管理
* 权限机制
* 错误处理机制

避免重复实现。

---

### 2.3 最小必要修改

优先采用最小范围、低风险的修改方式。

禁止为了实现一个局部需求而无理由：

* 重构整个模块
* 修改无关代码
* 更换技术栈
* 引入大量新依赖
* 修改公共接口
* 修改数据库结构

如果确实需要扩大修改范围，应说明原因。

---

### 2.4 不隐藏问题

禁止通过以下方式掩盖问题：

* 删除失败测试
* 降低测试要求
* 忽略错误
* 屏蔽异常
* 删除日志来隐藏问题
* 修改测试以适配错误实现

发现问题时，应优先解决根因。

---

## 3. 上下文加载规则

AI Agent 根据任务复杂度决定需要加载的上下文。

### Level 1：简单任务

例如：

* 文案修改
* 简单 UI 调整
* 明确 Bug 修复
* 配置修改

至少检查：

```text
AGENTS.md
相关代码
相关测试
```

---

### Level 2：普通功能

例如：

* 新增业务功能
* 新增页面
* 新增 API
* 新增数据模型

至少检查：

```text
AGENTS.md
Constitution
Architecture
相关 Spec
相关代码
相关测试
```

必要时创建或更新 Spec。

---

### Level 3：重大功能

例如：

* 架构变化
* 数据库重大变化
* 权限体系变化
* 核心业务变化
* 第三方服务接入
* 核心技术栈变化

需要检查：

```text
AGENTS.md
Constitution
Research
Architecture
ADR
Spec
Prototype
相关代码
测试
```

必要时先 Research，再进入设计和实现。

---

## 4. SDD 工作流

项目默认采用 Spec-Driven Development。

标准流程：

```text
需求
 ↓
Context
 ↓
Research（必要时）
 ↓
Constitution
 ↓
Architecture（必要时）
 ↓
ADR（必要时）
 ↓
Spec
 ↓
Prototype（UI 功能必要时）
 ↓
Plan
 ↓
Tasks
 ↓
Implementation
 ↓
Testing
 ↓
Verification
 ↓
Documentation
```

并非所有任务都必须完整执行全部流程。

AI Agent 必须根据任务复杂度选择合适流程。

---

## 5. 需求分析

收到需求后，先判断：

```text
这是 Bug？
这是简单修改？
这是普通功能？
这是跨模块功能？
这是架构变化？
```

明确以下内容：

* 用户目标
* 功能边界
* 输入
* 输出
* 业务规则
* 异常情况
* 权限要求
* 数据变化
* API 变化
* UI 变化
* PC / Mobile 需求
* 测试要求

发现需求不明确时，应优先提出关键问题，而不是自行假设大量业务规则。

---

## 6. Architecture 规则

Architecture 应至少考虑：

### Frontend

* 页面结构
* 路由
* 状态管理
* 组件结构
* UI / UX
* PC
* Mobile
* Loading
* Empty
* Error
* Responsive

### Backend

* API
* Service
* Domain / Business Logic
* Repository / Data Access
* Authentication
* Authorization
* Error Handling
* Logging

### Database

* 数据模型
* 表结构
* 关系
* Index
* Migration
* 数据一致性
* 数据生命周期

### Infrastructure

必要时考虑：

* Cache
* Queue
* Storage
* Search
* Monitoring
* Deployment
* Backup
* Disaster Recovery

Frontend 与 Backend 必须保持同等重要性。

---

## 7. ADR 规则

出现以下情况时，应考虑创建 ADR：

* 技术栈选择
* 架构方案选择
* 数据库选择
* 第三方服务选择
* 多个可行方案之间的重大取舍
* 影响长期维护的设计决定

ADR 重点记录：

```text
Context
Decision
Alternatives
Reasons
Consequences
```

ADR 记录“为什么这样决定”，而不仅仅是“现在是什么”。

---

## 8. Prototype / UI 规则

UI 功能在正式实现前，应根据复杂度决定是否需要 Prototype。

Prototype 可以使用：

* HTML
* CSS
* JavaScript
* Vue
* React
* Storybook
* 原型工具
* 其他可交互方式

不强制使用 Figma。

核心要求是：

> UI 不应该只通过静态描述确定，应尽可能通过可交互 Prototype 验证。

Prototype 应重点验证：

* 页面结构
* 信息层级
* 用户流程
* 核心交互
* PC 布局
* Mobile 布局
* 状态变化
* Loading
* Empty
* Error
* Dialog / Drawer / Form 等交互

Prototype 确认后，再进入正式实现。

---

## 9. 前端开发规则

任何涉及 UI 的功能，都必须考虑：

```text
Desktop
Mobile
Responsive
Accessibility
Loading
Empty
Error
Success
Disabled
Permission
```

不得只实现正常状态。

复杂页面应优先明确：

```text
页面结构
 ↓
组件结构
 ↓
交互流程
 ↓
状态
 ↓
API
 ↓
实现
```

---

## 10. Backend / API 规则

API 设计必须考虑：

* Request
* Response
* Validation
* Authentication
* Authorization
* Error Code
* Error Message
* Pagination
* Filtering
* Sorting
* Idempotency（必要时）
* Rate Limit（必要时）

修改 API 时必须检查：

* 前端调用方
* 后端调用方
* 第三方调用方
* 测试
* 文档

禁止只修改服务端而忽略调用方。

---

## 11. Database 规则

数据库修改必须考虑：

* Schema
* Migration
* Index
* Foreign Key
* Unique Constraint
* Default Value
* NULL
* 数据兼容性
* 历史数据
* Rollback / Recovery

禁止直接修改生产数据库结构而不经过 Migration。

---

## 12. Security 规则

涉及用户、权限、数据、网络、文件等功能时，必须考虑：

* Authentication
* Authorization
* Input Validation
* Injection
* XSS
* CSRF
* SSRF
* File Upload Security
* Sensitive Data
* Secret Management
* Rate Limiting
* Audit Log

禁止将：

* API Key
* Password
* Token
* Private Key
* Database Password
* 其他 Secret

直接提交到 Git。

---

## 13. Testing 规则

测试必须覆盖与功能风险匹配的范围。

根据实际情况选择：

```text
Unit Test
Integration Test
API Test
E2E Test
UI Test
Performance Test
Security Test
```

至少验证：

```text
正常流程
异常流程
边界条件
权限
数据一致性
```

修改代码后必须执行相关测试。

---

## 14. Verification

任务完成前必须检查：

```text
需求是否完成
代码是否正确
测试是否通过
是否存在明显回归
API 是否一致
数据库是否正确
权限是否正确
PC 是否正常
Mobile 是否正常
文档是否需要更新
Git Diff 是否合理
```

不能以：

> “代码已经写完”

作为任务完成标准。

---

## 15. Git 规则

提交代码前：

1. 检查 `git diff`
2. 检查新增文件
3. 检查删除文件
4. 检查敏感信息
5. 执行相关测试
6. 确认没有无关修改

Commit message 推荐：

```text
feat:
fix:
refactor:
docs:
test:
chore:
```

示例：

```text
feat: add bird profile management
fix: resolve mobile login issue
docs: update architecture
test: add user service tests
```

禁止未经确认执行高风险 Git 操作，例如：

```text
git reset --hard
git clean -fd
git push --force
```

---

## 16. 文档同步

代码发生重大变化时，应同步检查相关文档：

```text
Architecture
ADR
Spec
Prototype
API Documentation
README
Roadmap
```

文档必须尽可能反映当前真实实现。

禁止长期存在：

> 文档描述 A，代码实际上已经变成 B。

---

## 17. AI 修改代码的边界

AI 可以主动完成：

* 代码实现
* 测试
* Bug 修复
* 重构
* 文档更新
* Prototype
* 技术研究
* 常规工程操作

但对于以下情况，应明确说明影响：

* 删除大量代码
* 修改公共 API
* 数据库破坏性变化
* 安全机制变化
* 核心架构变化
* 更换核心技术
* 大规模重构

不要因为“能够修改”就直接修改。

---

## 18. 完成标准

一个任务只有同时满足以下条件，才能认为完成：

```text
需求完成
+
实现完成
+
测试通过
+
验证完成
+
安全检查完成
+
文档同步完成（如需要）
+
Git Diff 检查完成
```

对于 UI 功能，还必须考虑：

```text
PC
+
Mobile
+
Responsive
+
Loading
+
Empty
+
Error
+
Permission
```

---

## 19. 核心原则

始终遵循：

> **先理解，再设计；先设计，再实现；先验证，再交付。**

> **优先复用，而不是重复实现。**

> **优先解决根因，而不是隐藏问题。**

> **前端、后端、数据库、API、测试、安全、UX 必须作为一个完整功能统一考虑。**

> **Prototype 是验证 UI 的工具，不强制依赖 Figma。**

> **文档、代码、测试必须保持一致。**

> **AI 的目标不是尽快写出代码，而是可靠地完成需求。**
