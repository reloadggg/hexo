# 📝 Hexo博客维护操作文档

## 🚀 在新电脑上设置博客环境

### 1. 环境准备

#### 1.1 安装必要软件
```bash
# 安装Node.js (推荐LTS版本)
# 从 https://nodejs.org/ 下载并安装

# 验证安装
node --version
npm --version

# 安装Git
# 从 https://git-scm.com/ 下载并安装

# 验证安装
git --version
```

#### 1.2 配置Git
```bash
# 设置用户信息
git config --global user.name "你的用户名"
git config --global user.email "你的邮箱"

# 配置GitHub认证（推荐使用Personal Access Token）
# 在GitHub Settings → Developer settings → Personal access tokens 创建token
```

### 2. 克隆博客仓库

```bash
# 克隆仓库到本地
git clone https://github.com/reloadggg/hexo.git
cd hexo

# 安装依赖
npm install

# 或者使用pnpm（如果安装了）
pnpm install
```

### 3. 验证环境

```bash
# 清理缓存
npx hexo clean

# 生成静态文件
npx hexo generate

# 启动本地服务器
npx hexo server

# 访问 http://localhost:4000 查看博客
```

---

## ✍️ 日常博客管理

### 1. 创建新文章

#### 1.1 基本创建命令
```bash
# 创建新文章
npx hexo new "文章标题"

# 创建草稿
npx hexo new draft "草稿标题"

# 创建页面
npx hexo new page "页面名称"
```

#### 1.2 文章模板示例
创建文章后，编辑 `source/_posts/文章标题.md`：

```markdown
---
title: 我的新文章
date: 2025-06-03 18:00:00
tags: [标签1, 标签2, 标签3]
categories: [分类名称]
description: 文章简短描述
cover: /images/cover.jpg  # 可选：文章封面图
---

# 文章标题

这里是文章内容...

## 二级标题

### 三级标题

- 列表项1
- 列表项2

**粗体文字**
*斜体文字*

```代码块```

> 引用内容

[链接文字](https://example.com)

![图片描述](/images/image.jpg)
```

### 2. 分类和标签管理

#### 2.1 分类设置
```markdown
---
title: 文章标题
categories: 
  - 技术
  - 前端
  - JavaScript
---
```

#### 2.2 标签设置
```markdown
---
title: 文章标题
tags: 
  - Hexo
  - 博客
  - 教程
  - 动画特效
---
```

#### 2.3 常用分类建议
- **技术** - 编程相关
  - 前端
  - 后端
  - 移动开发
- **生活** - 日常分享
  - 随笔
  - 旅行
  - 美食
- **学习** - 知识总结
  - 读书笔记
  - 课程总结
- **项目** - 作品展示
  - 开源项目
  - 个人作品

### 3. 图片和资源管理

#### 3.1 图片存放
```bash
# 在source目录下创建images文件夹
mkdir source/images

# 将图片放入该文件夹
# 在文章中引用：![描述](/images/图片名.jpg)
```

#### 3.2 文章资源文件夹
```bash
# 修改_config.yml启用资源文件夹
post_asset_folder: true

# 创建文章时会自动创建同名文件夹
npx hexo new "我的文章"
# 会创建：
# source/_posts/我的文章.md
# source/_posts/我的文章/（资源文件夹）
```

---

## 🔄 更新和发布流程

### 1. 本地预览

```bash
# 清理缓存
npx hexo clean

# 生成静态文件
npx hexo generate

# 启动本地服务器
npx hexo server

# 在浏览器访问 http://localhost:4000 预览
```

### 2. 发布到GitHub Pages

#### 2.1 提交源码
```bash
# 添加所有更改
git add .

# 提交更改
git commit -m "添加新文章：文章标题"

# 推送到GitHub
git push origin main
```

#### 2.2 部署到GitHub Pages
```bash
# 生成并部署
npx hexo clean
npx hexo generate
npx hexo deploy

# 或者一条命令
npx hexo clean && npx hexo g -d
```

### 3. 验证部署

访问 https://reloadggg.github.io/hexo/ 查看更新效果

---

## 🛠️ 高级操作

### 1. 草稿管理

```bash
# 创建草稿
npx hexo new draft "草稿标题"

# 预览草稿（包含草稿的本地服务器）
npx hexo server --draft

# 发布草稿（将草稿移动到_posts）
npx hexo publish "草稿标题"
```

### 2. 自定义页面

```bash
# 创建关于页面
npx hexo new page about

# 编辑 source/about/index.md
```

### 3. 主题自定义

#### 3.1 修改CSS
编辑 `source/css/custom.css` 添加自定义样式

#### 3.2 修改JavaScript
编辑 `source/js/custom.js` 添加自定义功能

### 4. 配置修改

#### 4.1 网站基本信息
编辑 `_config.yml`：
```yaml
# Site
title: 你的博客标题
subtitle: 副标题
description: 博客描述
keywords: 关键词1,关键词2
author: 你的名字
language: zh-CN
timezone: Asia/Shanghai
```

#### 4.2 URL配置
```yaml
# URL
url: https://reloadggg.github.io/hexo
root: /hexo/
```

---

## 📋 常用命令速查

### 基本命令
```bash
# 创建新文章
npx hexo new "标题"

# 生成静态文件
npx hexo generate
npx hexo g

# 启动本地服务器
npx hexo server
npx hexo s

# 部署
npx hexo deploy
npx hexo d

# 清理
npx hexo clean

# 组合命令
npx hexo clean && npx hexo g -d
```

### Git命令
```bash
# 查看状态
git status

# 添加文件
git add .
git add 文件名

# 提交
git commit -m "提交信息"

# 推送
git push

# 拉取最新代码
git pull
```

---

## 🚨 故障排除

### 1. 常见问题

#### 问题1：npm install失败
```bash
# 清理缓存
npm cache clean --force

# 删除node_modules重新安装
rm -rf node_modules
npm install
```

#### 问题2：hexo命令不存在
```bash
# 全局安装hexo-cli
npm install -g hexo-cli

# 或使用npx
npx hexo --version
```

#### 问题3：部署失败
```bash
# 检查_config.yml中的deploy配置
# 确保repo地址正确
deploy:
  type: git
  repo: https://github.com/reloadggg/hexo.git
  branch: gh-pages
```

#### 问题4：GitHub Pages不更新
- 检查GitHub Actions是否运行成功
- 确认gh-pages分支已选择
- 等待几分钟让GitHub处理

### 2. 备份策略

#### 2.1 定期备份
```bash
# 每次写作后都要提交
git add .
git commit -m "备份：$(date)"
git push
```

#### 2.2 多设备同步
```bash
# 在新设备上工作前
git pull

# 工作完成后
git add .
git commit -m "更新内容"
git push
```

---

## 📚 扩展资源

### 1. Hexo官方文档
- [Hexo官网](https://hexo.io/)
- [Hexo文档](https://hexo.io/docs/)

### 2. Markdown语法
- [Markdown基础语法](https://markdown.com.cn/basic-syntax/)
- [GitHub Flavored Markdown](https://github.github.com/gfm/)

### 3. 主题和插件
- [Hexo主题](https://hexo.io/themes/)
- [Hexo插件](https://hexo.io/plugins/)

---

## 🎯 快速开始检查清单

### 新电脑设置
- [ ] 安装Node.js和Git
- [ ] 配置Git用户信息
- [ ] 克隆仓库
- [ ] 安装依赖
- [ ] 测试本地运行

### 写作流程
- [ ] 创建新文章
- [ ] 设置标题、分类、标签
- [ ] 编写内容
- [ ] 本地预览
- [ ] 提交到Git
- [ ] 部署到GitHub Pages
- [ ] 验证在线效果

### 定期维护
- [ ] 备份源码到GitHub
- [ ] 检查链接有效性
- [ ] 更新依赖包
- [ ] 优化图片大小
- [ ] 检查SEO设置

---

## 🌟 博客特效说明

### 当前博客包含的动态特效：
- 🌈 **动态渐变背景** - 流动的彩色背景
- ⚡ **页面加载动画** - 旋转加载指示器
- 🎯 **鼠标跟随粒子** - 移动鼠标产生彩色粒子
- 🎪 **标题动画** - 脉冲动画 + 悬停彩虹色变化 + 打字机效果
- 📱 **文章卡片动效** - 悬停上浮 + 点击波纹效果
- 🎭 **侧边栏动画** - 滑入动画 + 悬停缩放
- 🏷️ **标签云特效** - 悬停弹跳 + 随机颜色变化
- 📜 **滚动视差效果** - 页面滚动时的视差动画
- 🎨 **美化滚动条** - 渐变色滚动条
- ⏰ **响应式动画** - 不同元素的延迟动画

### 特效文件位置：
- CSS特效：`source/css/custom.css`
- JavaScript特效：`source/js/custom.js`
- 主题模板：`themes/landscape/layout/_partial/`

---

*保存这份文档，随时查阅！如有问题，可以参考故障排除部分或查阅官方文档。* 📖
