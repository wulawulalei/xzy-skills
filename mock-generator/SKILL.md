---
name: generate-mock-from-ts
description: 根据 TypeScript 类型生成 Mock 数据
---

---

## 🎯 目标

根据给定的 TypeScript 类型定义，自动生成**结构正确、数据真实、可直接使用**的 Mock 数据。

---

## 🧾 使用说明

将 TypeScript 类型代码作为输入，让 AI 按规则生成对应的 mock 数据对象或数组。

---

## 规则说明

### 基础类型映射

- `string` → 有意义的字符串（如用户名、标题、ID 等）
- `number` → 合理范围内的数值
- `boolean` → `true / false`
- `Date` / 时间字符串 → ISO 格式时间（如 `"2026-04-07 10:23:11"`）

---

### 枚举类型（enum / union）

- 必须从定义的枚举值中选择一个

```ts
type Status = "pending" | "success" | "fail";
```

👉 示例输出：

```ts
status: "success";
```

---

### 数组类型

- 默认生成 **2~3 条数据**

```ts
type User = {
  name: string;
};
```

👉 示例输出：

```ts
[{ name: "Alice" }, { name: "Bob" }];
```

---

### 嵌套对象

- 递归生成完整结构

---

### 常见字段优化（非常重要）

- `id` → 类似 `"user_xxx"` / `"order_xxx"`
- `name` → 真实姓名（中英文皆可）
- `title` → 合理标题
- `createdAt` / `updatedAt` → ISO 时间
- `status` → 合法枚举值
- `price` / `amount` → 合理金额（如 19.99 / 199）

---

## 📦 输出要求

- ✅ 严格符合 TypeScript 类型结构
- ✅ 数据“像真实业务数据”
- ✅ 不要输出解释说明
- ✅ 只输出最终 mock 数据

---

## 🧪 示例

### 输入

```ts
type User = {
  id: string;
  name: string;
  age: number;
  isAdmin: boolean;
};
```

---

### 输出

```ts
{
  id: "user_8392ab",
  name: "张伟",
  age: 28,
  isAdmin: false
}
```

---

## 🚀 进阶版本（推荐）

### 支持列表 + 分页结构

如果类型包含列表语义，自动补充：

```ts
{
  list: [...],
  total: 100,
  page: 1,
  pageSize: 10
}
```

---

## 🧩 推荐用法

1. 选中 TypeScript 类型
2. 执行该 Skill
3. 直接获得 mock 数据

---

## ✅ 一句话总结

> 根据 TS 类型，自动生成结构正确 + 业务真实的 mock 数据
