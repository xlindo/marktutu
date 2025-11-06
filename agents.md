# 马克图图 (MarkTutu) 项目文档

## 项目概述

马克图图 (MarkTutu) 是一个为微信小程序提供官方介绍和文档的静态网站项目。该项目为微信小程序"马克图图"（一个本地 Markdown 编辑器）提供展示平台，介绍其功能特性、更新日志和使用方法。

**项目类型**: 静态文档网站 (Jekyll)
**部署平台**: GitHub Pages
**关联产品**: 微信小程序 - 马克图图 Markdown 编辑器

---

## 技术栈

### 核心技术
- **静态网站生成器**: Jekyll 4.x
- **编程语言**: Ruby
- **主题**: jekyll-theme-minimal
- **部署平台**: GitHub Pages

### 依赖插件
- **jekyll-feed**: RSS/Atom 订阅支持
- **jekyll-remote-theme**: 远程主题支持
- **GitHub Pages**: 托管服务

### 支持平台
- Windows (使用 WDM gem)
- JRuby (使用 http_parser.rb)
- Unix/Linux 系统

---

## 小程序功能特性

### 主要功能
1. **本地 Markdown 编辑器**
   - 完全工作在本地的安全编辑器
   - 保护用户隐私，无需网络传输

2. **图片导出**
   - 将 Markdown 内容导出为图片
   - 支持多种图片格式

3. **实时预览**
   - 支持 Markdown 语法渲染
   - 实时查看编辑效果

4. **主题模式**
   - 多种边框颜色切换
   - 个性化视觉体验

### 支持的 Markdown 语法
- 大部分基础 Markdown 语法
- 脚注链接
- 列表和嵌套列表
- 图片嵌入
- 代码块

### 版本历史
- **v1.0.0** (2025.2.23): 初始版本，实现基础 Markdown 语法渲染和图片下载功能
- **v1.1.0** (2025.2.26): 去除水印、优化图片边框、增加主题模式
- **v1.1.1** (2025.2.26): 修复脚注链接列表不能换行的错误
- **v1.1.2** (2025.2.26): 修复编辑器被键盘遮挡的错误，改进预览图片页面布局

---

## 目录结构

```
/mnt/d/repos/xlindo_repos/marktutu/
├── docs/                          # 文档网站根目录
│   ├── _config.yml               # Jekyll 配置文件
│   ├── Gemfile                   # Ruby 依赖配置
│   ├── Gemfile.lock              # 依赖锁定文件
│   ├── _posts/                   # 博客文章目录
│   │   └── 2025-02-23-welcome-to-MarkTutu.markdown
│   ├── assets/                   # 静态资源目录
│   │   ├── favicon.ico           # 网站图标
│   │   └── img/                  # 图片资源
│   │       ├── favicon.ico
│   │       ├── marktutu.jpg      # 小程序二维码
│   │       └── screenshot.jpg    # 小程序截图
│   ├── 404.html                  # 404 错误页面
│   ├── about.markdown            # 关于页面
│   ├── index.markdown            # 主页文件 (英文)
│   ├── index.md                  # 主页内容 (中文)
│   └── .gitignore                # Git 忽略文件
└── .git/                         # Git 版本控制
```

### 关键文件说明

#### `_config.yml`
Jekyll 主配置文件，包含：
- 站点基本信息 (标题、邮箱、描述)
- URL 配置 (baseurl: "/marktutu")
- 主题设置 (jekyll-theme-minimal)
- 插件列表 (jekyll-feed)
- Logo 设置

#### `Gemfile`
Ruby 依赖管理文件，指定：
- GitHub Pages 集成
- Jekyll 插件 (jekyll-feed, jekyll-remote-theme)
- 平台特定依赖 (Windows/JRuby)
- 性能优化组件 (WDM, tzinfo)

#### `index.md`
中文主页内容，包含：
- 小程序介绍
- 功能特性说明
- 更新日志
- 使用说明
- 联系方式

---

## 开发指南

### 环境要求
- Ruby 2.5.0 或更高版本
- Bundler (Ruby 包管理器)
- Git

### 本地开发

1. **安装依赖**
```bash
cd docs
bundle install
```

2. **启动本地服务器**
```bash
bundle exec jekyll serve
```
- 访问地址: http://localhost:4000/marktutu
- 支持实时重载 (自动检测文件变化)

3. **构建静态文件**
```bash
bundle exec jekyll build
```
- 输出目录: `_site/`

### 部署流程

#### GitHub Pages 部署
1. 将代码推送到 GitHub 仓库
2. 在仓库设置中启用 GitHub Pages
3. 选择源分支 (通常为 `main`)
4. 访问: `https://username.github.io/marktutu`

#### 自定义域名
在 `_config.yml` 中修改:
```yaml
url: "https://your-domain.com"
baseurl: ""
```

### 内容管理

#### 添加新文章
在 `_posts/` 目录创建新文件:
```
YYYY-MM-DD-post-title.markdown
```

文件头部元数据:
```yaml
---
layout: post
title: "文章标题"
date: YYYY-MM-DD HH:MM:SS +0800
categories: category_name
---
```

#### 修改主页
编辑 `docs/index.md` 文件
- 支持标准 Markdown 语法
- 包含图片引用: `![alt](assets/img/image.jpg)`

---

## 站点配置

### 基本设置 (`_config.yml`)

| 配置项 | 值 | 说明 |
|--------|----|----|
| title | 马克图图 MarkTutu | 网站标题 |
| email | qr@xlindo.com | 联系邮箱 |
| baseurl | "/marktutu" | 子路径 |
| url | https://xlindo.com | 站点 URL |
| theme | jekyll-theme-minimal | Jekyll 主题 |
| logo | assets/img/marktutu.jpg | 站点 Logo |

### 排除文件
以下文件/目录被排除在处理之外:
- `_site/` - Jekyll 构建输出
- `.sass-cache/` - Sass 缓存
- `.jekyll-cache/` - Jekyll 缓存
- `.jekyll-metadata` - Jekyll 元数据
- `vendor/` - 第三方库
- `Gemfile.lock` - 依赖锁定文件

---

## 功能特性

### 响应式设计
- 适配多种屏幕尺寸
- 移动端友好
- 基于 Minimal 主题

### SEO 优化
- 清晰的 URL 结构
- 元数据支持
- 社交媒体分享优化

### 内容特性
- Markdown 编写支持
- 图片资源管理
- 多语言支持 (中英文)

### 性能优化
- 静态文件生成
- 缓存机制
- 最小化资源加载

---

## 维护与更新

### 定期任务
- [ ] 更新依赖包: `bundle update`
- [ ] 检查安全漏洞
- [ ] 备份站点内容
- [ ] 监控 GitHub Pages 可用性
- [ ] 更新版本信息

### 内容更新
- 添加新的版本发布记录
- 更新截图和二维码
- 维护联系方式
- 添加用户反馈

### 故障排除

#### 常见问题
1. **页面无法访问**
   - 检查 GitHub Pages 设置
   - 验证 URL 配置
   - 确认分支选择正确

2. **构建失败**
   - 检查 Jekyll 版本兼容性
   - 验证 Gemfile 依赖
   - 查看构建日志

3. **样式异常**
   - 确认主题文件正确加载
   - 检查 CSS 缓存
   - 验证资源路径

---

## 联系方式

### 开发团队
- **开发方**: 公众号"科文路"
- **邮箱**: qr@xlindo.com
- **网站**: https://xlindo.com

### 技术支持
- 通过公众号后台留言
- 发送邮件至 qr@xlindo.com
- 访问项目文档获取帮助

---

## 许可与版权

本项目为微信小程序"马克图图"的官方文档网站。

### 使用许可
- 文档内容仅供学习参考
- 禁止商业用途转载
- 保留所有权利

### 第三方资源
- Jekyll 主题: MIT 许可
- Ruby Gems: 各组件许可
- 图片资源: 归开发团队所有

---

## 更新日志

### 2025-02-23
- 初始版本发布
- 完成基本文档结构
- 添加功能介绍和截图
- 部署到 GitHub Pages

---

## 附录

### 参考资源
- [Jekyll 官方文档](https://jekyllrb.com/)
- [GitHub Pages 指南](https://pages.github.com/)
- [jekyll-theme-minimal](https://github.com/pages-themes/minimal)
- [Markdown 语法参考](https://www.markdownguide.org/)

### 相关链接
- 小程序二维码: `docs/assets/img/marktutu.jpg`
- 小程序截图: `docs/assets/img/screenshot.jpg`
- 项目网站: https://xlindo.com/marktutu

---

*最后更新: 2025-02-23*
