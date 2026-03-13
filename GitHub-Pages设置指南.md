# GitHub Pages 设置指南 - 重要！

## 🔴 当前问题

GitHub Pages 返回的是原始 HTML 文件，说明 GitHub Pages 的 Source 设置不正确。

---

## ✅ 解决方案：修改 GitHub Pages Source 设置

### 第一步：访问仓库设置

1. 打开浏览器访问：https://github.com/TANG-YIN/quick-trans

### 第二步：进入 Pages 设置

1. 点击仓库顶部的 **Settings**（设置）
2. 在左侧菜单找到并点击 **Pages**
3. 找到 **Build and deployment** 部分

### 第三步：修改 Source 设置（重要！）

#### 当前错误配置：
```
Source: Deploy from a branch
Branch: master
Folder: / (root)
```

#### 正确配置（必须修改）：
```
Source: GitHub Actions
```

**操作步骤：**
1. 在 "Source" 下拉菜单中
2. 从 "Deploy from a branch" 改为 **"GitHub Actions"**
3. 如果系统提示，点击 "Save" 保存

### 第四步：确认设置

修改后，页面顶部会显示：
```
Your site is deployed by GitHub Actions at:
https://tang-yin.github.io/quick-trans/
```

---

## 🔄 工作原理

### 使用 "Deploy from a branch"（当前错误配置）
- GitHub Pages 直接从仓库的源文件提供服务
- 不会执行 `npm run build`
- 返回原始的 `index.html` 和 `.tsx` 文件
- ❌ 不适用于需要构建的前端项目

### 使用 "GitHub Actions"（正确配置）
- GitHub Actions 运行工作流
- 执行 `npm ci` 和 `npm run build`
- 将构建产物（`dist/` 目录）部署到 Pages
- ✅ 适用于所有现代前端框架（React、Vue 等）

---

## 📊 验证设置

### 1. 查看 Actions 状态

访问：https://github.com/TANG-YIN/quick-trans/actions

您应该看到：
- ✅ 绿色的 "Deploy to GitHub Pages" workflow
- ✅ 状态为 "Success"
- ✅ 部署完成时间

### 2. 查看具体日志

1. 点击最新的 workflow 运行
2. 查看 "build-and-deploy" job
3. 确认所有步骤都成功：
   - ✅ Checkout
   - ✅ Setup Node.js
   - ✅ Install dependencies
   - ✅ Build
   - ✅ Setup Pages
   - ✅ Upload artifact
   - ✅ Deploy to GitHub Pages

### 3. 访问网站

等待 2-5 分钟后访问：
```
https://tang-yin.github.io/quick-trans/
```

**成功的标志：**
- 页面完全加载（不是空白）
- 显示 Quick-Trans 界面
- 可以进行所有操作

---

## 🔧 GitHub Actions 工作流说明

### 当前配置的 workflow

```yaml
触发条件：
  - push 到 master 分支
  - 手动触发 (workflow_dispatch)

权限：
  - contents: read (读取代码)
  - pages: write (写入 Pages)
  - id-token: write (身份验证)

并发控制：
  - 取消正在进行的旧构建
  - 避免资源冲突

工作步骤：
  1. 检出代码 (Checkout)
  2. 设置 Node.js 20 环境
  3. 安装依赖 (npm ci)
  4. 构建项目 (npm run build)
  5. 配置 Pages (Setup Pages)
  6. 上传构建产物 (dist/)
  7. 部署到 GitHub Pages
```

---

## 🐛 故障排查

### 问题1：GitHub Pages 仍然返回原始 HTML

**原因：** Source 设置仍然是 "Deploy from a branch"

**解决：**
1. 进入 Settings → Pages
2. 将 Source 改为 "GitHub Actions"
3. 保存并等待 2-5 分钟

### 问题2：Actions 显示失败

**解决：**
1. 访问 Actions 页面
2. 查看失败的步骤
3. 点击展开查看详细错误日志
4. 根据错误信息修复代码

常见错误：
- **依赖安装失败**：检查 package.json 是否正确
- **构建失败**：检查代码是否有语法错误
- **权限错误**：确认 workflow 权限配置正确

### 问题3：部署成功但网站显示空白

**解决：**
1. 检查浏览器控制台（F12）是否有 JavaScript 错误
2. 清除浏览器缓存（Ctrl+Shift+Delete）
3. 查看构建日志，确认 `dist/` 目录内容正确

### 问题4：页面样式错乱

**解决：**
1. 确认 `vite.config.ts` 中的 `base` 设置正确
2. 检查是否正确加载了 CSS 文件
3. 查看网络请求（F12 → Network）确认资源加载成功

---

## 📈 后续更新流程

### 自动部署

修改 Source 为 "GitHub Actions" 后，流程为：

```bash
# 1. 本地修改代码
cd d:/24孔板转染计算器

# 2. 提交修改
git add .
git commit -m "update: 描述修改"

# 3. 推送到 GitHub
git push github master

# 4. GitHub Actions 自动执行
    ├─ 构建项目
    ├─ 上传构建产物
    └─ 部署到 GitHub Pages

# 5. 等待 2-5 分钟，网站自动更新
```

### 完全自动化

无需任何手动操作：
- ✅ 自动构建
- ✅ 自动部署
- ✅ 自动更新网站
- ✅ 版本追溯

---

## 🎯 设置清单

在访问网站前，请确认：

- [ ] 已访问 https://github.com/TANG-YIN/quick-trans/settings/pages
- [ ] Source 设置为 "GitHub Actions"
- [ ] Actions 页面显示成功的部署
- [ ] 等待至少 2 分钟
- [ ] 清除浏览器缓存后访问

---

## 📚 参考资源

- GitHub Actions 官方文档：https://docs.github.com/en/actions
- GitHub Pages 官方文档：https://docs.github.com/en/pages
- 使用 Actions 部署 Pages：https://docs.github.com/en/pages/deploying-with-github-actions

---

## 🎉 完成设置后的效果

设置完成后：
- ✅ 每次推送代码自动构建
- ✅ 构建成功自动部署
- ✅ 网站始终是最新版本
- ✅ 可以在任何设备访问
- ✅ 无需手动操作

---

## ⚠️ 重要提醒

**必须手动修改 GitHub Pages 的 Source 设置！**

这是当前问题的关键，修改为 "GitHub Actions" 后，一切就会正常工作。

---

祝您设置顺利！设置完成后网站就能正常访问了！🚀
