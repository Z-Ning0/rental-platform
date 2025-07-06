# 租房信息聚合平台

这是一个使用 [Supabase](https://supabase.com/) 和原生 JavaScript 编写的租房信息平台，支持多人协作查看、添加和删除房源信息，适合部署到 GitHub Pages 或任何静态网站托管服务。

---

## ✨ 功能特性

- 添加房源信息（来自多个平台，如贝壳、自如等）
- 房源信息持久化存储在 Supabase 数据库中
- 支持展示全部房源信息
- 支持按 ID 删除指定房源
- 自动按创建时间排序展示房源

---

## 🏗️ 技术栈

- 前端框架：原生 HTML + Tailwind CSS + JavaScript
- 数据库：PostgreSQL（通过 Supabase 托管）
- 后端服务：Supabase 提供 REST API

---

## 🚀 快速开始

### 1. 克隆项目

```bash
git clone https://github.com/your-username/rental-platform.git
cd rental-platform
```

### 2. 配置 Supabase

1. 前往 https\://app.supabase.com 创建新项目
2. 创建数据表 `houses`，结构如下：

```sql
create table public.houses (
  house_id uuid not null default gen_random_uuid(),
  source_type text,
  source_id text,
  title text,
  rent_type text,
  room_type text,
  area text,
  orientation text,
  floor_info text,
  has_elevator text,
  min_rent_period text,
  rent_price text,
  deposit text,
  payment_terms text,
  features text,
  agent_name text,
  agent_company text,
  contact_phone text,
  created_at timestamp with time zone not null default now(),
  source_website text,
  constraint houses_pkey primary key (house_id)
);
```

3. 获取 `Project URL` 和 `anon public API key`
4. 在 `index.html` 中替换如下两行：

```js
const SUPABASE_URL = 'your-project-url';
const SUPABASE_KEY = 'your-anon-key';
```

---

### 3. 本地运行

直接用浏览器打开 `index.html` 文件即可开始使用（建议使用 Chrome）。

---

### 4. 发布到 GitHub Pages（可选）

1. 新建一个 GitHub 仓库：`rental-platform`
2. 上传项目代码（至少包含 `index.html`）
3. 进入仓库 → Settings → Pages → 设置为 `main` 分支 `root` 文件夹
4. 等待 1 分钟左右，你的网页地址为：
   ```
   https://your-username.github.io/rental-platform/
   ```

---

## 📌 安全提示

- 当前使用的是公开 anon key，适合开发/演示阶段
- 上线生产建议启用 Supabase RLS 策略并配置用户权限
- 可拓展登录系统限制写权限（Supabase Auth）

---

## ✅ 后续可扩展功能（欢迎贡献）

- 条件筛选与关键词搜索功能
- 登录注册与身份管理（Supabase Auth）
- 地图地址定位（Leaflet / 高德）
- 多平台爬虫自动导入
- 数据导出为 Excel / CSV

---

## 📄 License

本项目采用 MIT 开源许可证，欢迎 Fork 与贡献改进。

