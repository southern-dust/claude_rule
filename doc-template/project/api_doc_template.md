# API 文档

**项目名称**: [项目名称]
**API版本**: v1.0
**Base URL**: `https://api.example.com/v1`
**最后更新**: YYYY-MM-DD

---

## 概述

本API提供 [项目名称] 的所有后端服务接口。

### 认证方式

所有API请求需要在Header中携带认证信息：

```bash
Authorization: Bearer <your_token>
```

获取Token请参考 [认证接口](#1-认证)

### 通用响应格式

**成功响应**:
```json
{
  "code": 200,
  "message": "success",
  "data": {},
  "timestamp": "2025-01-01T12:00:00Z"
}
```

**错误响应**:
```json
{
  "code": 400,
  "message": "参数错误",
  "error": "详细错误信息",
  "timestamp": "2025-01-01T12:00:00Z"
}
```

### 状态码

| 状态码 | 说明 |
|--------|------|
| 200 | 成功 |
| 201 | 创建成功 |
| 400 | 请求参数错误 |
| 401 | 未授权 |
| 403 | 禁止访问 |
| 404 | 资源不存在 |
| 500 | 服务器错误 |

### 速率限制

- 每小时1000次请求
- 超出限制返回 `429 Too Many Requests`
- 响应头包含剩余配额：
  ```
  X-RateLimit-Limit: 1000
  X-RateLimit-Remaining: 999
  X-RateLimit-Reset: 1704100800
  ```

---

## API 端点

### 1. 认证

#### 1.1 用户登录

```http
POST /auth/login
```

**请求参数**:
```json
{
  "username": "string",
  "password": "string"
}
```

**响应示例**:
```json
{
  "code": 200,
  "message": "登录成功",
  "data": {
    "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
    "refresh_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
    "expires_in": 900,
    "token_type": "Bearer"
  }
}
```

#### 1.2 刷新Token

```http
POST /auth/refresh
```

**请求参数**:
```json
{
  "refresh_token": "string"
}
```

**响应示例**:
```json
{
  "code": 200,
  "data": {
    "access_token": "...",
    "expires_in": 900
  }
}
```

#### 1.3 登出

```http
POST /auth/logout
```

**需要认证**: ✅

**响应示例**:
```json
{
  "code": 200,
  "message": "登出成功"
}
```

---

### 2. 用户管理

#### 2.1 获取用户列表

```http
GET /users
```

**需要认证**: ✅

**查询参数**:

| 参数 | 类型 | 必填 | 说明 | 默认值 |
|------|------|------|------|--------|
| page | integer | 否 | 页码 | 1 |
| limit | integer | 否 | 每页数量 | 20 |
| sort | string | 否 | 排序字段 | created_at |
| order | string | 否 | 排序方向 | desc |

**响应示例**:
```json
{
  "code": 200,
  "data": {
    "items": [
      {
        "id": 1,
        "username": "john_doe",
        "email": "john@example.com",
        "created_at": "2025-01-01T12:00:00Z"
      }
    ],
    "total": 100,
    "page": 1,
    "limit": 20,
    "pages": 5
  }
}
```

#### 2.2 获取用户详情

```http
GET /users/{id}
```

**需要认证**: ✅

**路径参数**:

| 参数 | 类型 | 说明 |
|------|------|------|
| id | integer | 用户ID |

**响应示例**:
```json
{
  "code": 200,
  "data": {
    "id": 1,
    "username": "john_doe",
    "email": "john@example.com",
    "avatar": "https://...",
    "created_at": "2025-01-01T12:00:00Z",
    "updated_at": "2025-01-01T12:00:00Z"
  }
}
```

#### 2.3 创建用户

```http
POST /users
```

**需要认证**: ✅
**需要权限**: `user:create`

**请求参数**:
```json
{
  "username": "string (3-50字符)",
  "email": "string (邮箱格式)",
  "password": "string (最少8字符)",
  "role": "user|admin"
}
```

**验证规则**:
- username: 3-50字符，只能包含字母、数字、下划线
- email: 有效的邮箱格式
- password: 最少8字符，必须包含字母和数字

**响应示例**:
```json
{
  "code": 201,
  "message": "用户创建成功",
  "data": {
    "id": 1,
    "username": "john_doe",
    "email": "john@example.com"
  }
}
```

**错误示例**:
```json
{
  "code": 400,
  "message": "参数验证失败",
  "error": {
    "username": ["用户名已存在"],
    "email": ["邮箱格式不正确"]
  }
}
```

#### 2.4 更新用户

```http
PUT /users/{id}
```

**需要认证**: ✅
**需要权限**: `user:update` 或本人

**请求参数**:
```json
{
  "email": "string",
  "avatar": "string"
}
```

#### 2.5 删除用户

```http
DELETE /users/{id}
```

**需要认证**: ✅
**需要权限**: `user:delete`

**响应示例**:
```json
{
  "code": 200,
  "message": "用户已删除"
}
```

---

### 3. 订单管理

#### 3.1 创建订单

```http
POST /orders
```

**需要认证**: ✅

**请求参数**:
```json
{
  "items": [
    {
      "product_id": 1,
      "quantity": 2
    }
  ],
  "shipping_address": {
    "name": "张三",
    "phone": "13800138000",
    "address": "北京市朝阳区..."
  }
}
```

**响应示例**:
```json
{
  "code": 201,
  "data": {
    "id": "ORD202501011200001",
    "status": "pending",
    "total_amount": 299.00,
    "created_at": "2025-01-01T12:00:00Z"
  }
}
```

---

## 数据模型

### User

```json
{
  "id": "integer",
  "username": "string",
  "email": "string",
  "avatar": "string (url)",
  "role": "string",
  "created_at": "string (ISO8601)",
  "updated_at": "string (ISO8601)"
}
```

### Order

```json
{
  "id": "string",
  "user_id": "integer",
  "status": "pending|paid|shipped|completed|cancelled",
  "total_amount": "number",
  "items": "array<OrderItem>",
  "created_at": "string (ISO8601)"
}
```

---

## 错误码

| 错误码 | 说明 | 处理建议 |
|--------|------|----------|
| 400 | 请求参数错误 | 检查请求参数格式和必填项 |
| 401 | 未授权 | Token无效或过期，请重新登录 |
| 403 | 禁止访问 | 没有权限访问该资源 |
| 404 | 资源不存在 | 检查请求URL和资源ID |
| 409 | 资源冲突 | 资源已存在或状态冲突 |
| 422 | 无法处理的实体 | 业务逻辑验证失败 |
| 429 | 请求过于频繁 | 降低请求频率 |
| 500 | 服务器错误 | 联系技术支持 |

**业务错误码**:

| 错误码 | 说明 |
|--------|------|
| 1001 | 用户名已存在 |
| 1002 | 邮箱已存在 |
| 1003 | 用户名或密码错误 |
| 2001 | 库存不足 |
| 2002 | 订单不存在 |

---

## SDK和客户端库

### Python

```python
# 安装
pip install example-api-client

# 使用
from example_api import Client

client = Client(api_key="your_api_key")
users = client.users.list(page=1, limit=20)
```

### JavaScript

```bash
# 安装
npm install @example/api-client
```

```javascript
import { Client } from '@example/api-client';

const client = new Client({ apiKey: 'your_api_key' });
const users = await client.users.list({ page: 1, limit: 20 });
```

---

## Webhook

### Webhook配置

在管理后台配置Webhook URL，系统会在事件发生时推送通知。

### 事件类型

#### order.paid

订单支付成功

```json
{
  "event": "order.paid",
  "timestamp": "2025-01-01T12:00:00Z",
  "data": {
    "order_id": "ORD202501011200001",
    "amount": 299.00
  }
}
```

### 验证签名

```python
import hmac
import hashlib

def verify_webhook(payload, signature, secret):
    expected = hmac.new(
        secret.encode(),
        payload.encode(),
        hashlib.sha256
    ).hexdigest()
    return hmac.compare_digest(expected, signature)
```

---

## 测试环境

**测试环境Base URL**: `https://api-staging.example.com/v1`

**测试账号**:
- 用户名: test@example.com
- 密码: Test1234

**测试Token**: 使用测试账号登录获取

---

## 更新日志

### v1.0 (2025-01-01)

**新增**:
- 用户管理接口
- 订单管理接口
- 认证接口

---

## 支持

- **API文档**: https://docs.example.com
- **技术支持**: api-support@example.com
- **问题反馈**: https://github.com/example/issues

---

**文档版本**: v1.0
**最后更新**: YYYY-MM-DD
