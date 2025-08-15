---
title: '个人网站搭建心得：从零到一的完整历程'
publishDate: 2025-08-15
description: '记录我使用 Astro 和 Pure 主题搭建个人网站的完整过程，包括技术选择、定制化改造和最终部署的心得体会。'
tags:
  - Astro
  - 网站搭建
  - 前端开发
  - 个人博客
heroImage: { src: './thumbnail.jpg', color: '#4F46E5' }
language: '中文'
---

## 为什么选择 Astro + Pure 主题

之前用过 Hexo 和 Hugo，这次想尝试新的技术栈。Astro 的静态生成性能很好，Pure 主题设计简洁，功能完整，就决定用这个组合。

## 搭建过程

### 1. 克隆模板

```bash
git clone https://github.com/cworld1/astro-theme-pure.git
cd astro-theme-pure
npm install
```

### 2. 修改个人信息

主要修改 `src/site.config.ts` 文件：

```typescript
export default {
  title: 'D1zzy',
  description: 'Developer / Researcher / Gamer',
  author: 'D1zzy'
  // ... 其他配置
}
```

### 3. 删除不需要的功能

- 删除了 docs 系统（`src/content/docs` 和 `src/pages/docs`）
- 删除了示例文章
- 修改了 `content.config.ts` 移除 docs 相关配置

### 4. 定制 Links 页面

把友链页面改成了推荐页面，包含：

- 推荐博主
- 推荐游戏
- 推荐书籍

### 5. 添加评论系统

集成了 Waline 评论系统：

1. 在 Vercel 上部署 Waline 服务
2. 在 `src/site.config.ts` 中配置：

```typescript
comment: {
  provider: 'waline',
  serverURL: 'your-waline-server-url'
}
```

### 6. 添加访问统计

使用 Umami 统计访问数据：

1. 在 Vercel 上部署 Umami
2. 在 `src/layouts/BaseLayout.astro` 中添加跟踪代码：

```html
<script async defer src="your-umami-url/script.js" data-website-id="your-id"></script>
```

### 7. Vercel 部署

1. 推送代码到 GitHub
2. 在 Vercel 中导入项目
3. 配置环境变量（如果需要）
4. 自动部署完成

## 遇到的问题

### 删除 docs 系统

删除 docs 后遇到了一些引用错误，需要：

- 检查并删除所有对 docs 的引用
- 更新导航菜单配置
- 修改相关组件

### 评论系统配置

Waline 配置时遇到了一些问题：

- 确保 CORS 配置正确
- 检查环境变量设置
- 验证服务端 URL 格式

## 最终效果

网站现在包含：

- 个人介绍页面
- 博客文章系统
- 项目展示
- 推荐页面
- 评论功能
- 访问统计

整体加载速度很快，设计简洁现代。

## 技术栈

- **框架**: Astro 4.x
- **主题**: Astro Theme Pure
- **部署**: Vercel
- **评论**: Waline
- **统计**: Umami

整个过程大概花了两天时间，主要是配置和调试。Astro 的文档很详细，遇到问题基本都能找到解决方案。
