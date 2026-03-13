# Quick-Trans GitHub Pages 部署指南

## 完整部署步骤

### 第一步：代码已推送到 GitHub ✅

您的代码已经成功推送到 GitHub 仓库：
```
https://github.com/TANG-YIN/quick-trans.git
```

### 第二步：开启 GitHub Pages 服务

1. **访问您的仓库**
   - 打开浏览器访问：https://github.com/TANG-YIN/quick-trans

2. **进入 Settings（设置）**
   - 点击仓库顶部的 "Settings" 标签

3. **配置 Pages**
   - 在左侧菜单中找到并点击 "Pages"
   - 在 "Build and deployment" 部分：
     - **Source**：选择 "Deploy from a branch"
     - **Branch**：选择 `master` 分支，文件夹选择 `/ (root)`
     - 点击 "Save" 保存

4. **等待部署完成**
   - GitHub 会自动部署您的项目
   - 通常需要 1-3 分钟
   - 部署完成后，页面顶部会显示访问地址

### 第三步：访问您的网站

GitHub Pages 访问地址格式：
```
https://your-username.github.io/your-repo-name
```

对于您的仓库，访问地址将是：
```
https://tang-yin.github.io/quick-trans/
```

---

## 后续更新流程

当您修改代码后，更新步骤如下：

### 1. 本地修改并提交

```bash
cd d:/24孔板转染计算器

# 查看修改
git status

# 添加修改的文件
git add .

# 提交修改
git commit -m "update: 描述您的修改内容"

# 推送到 GitHub
git push github master
```

### 2. GitHub 自动部署

- GitHub Pages 会在检测到新的 commit 后自动重新部署
- 通常需要 1-3 分钟
- 无需手动操作，非常方便！

### 3. 同时推送到 Gitee（可选）

如果您想同时更新 Gitee 和 GitHub：

```bash
# 同时推送到两个远程仓库
git push
git push github master
```

或者配置一次推送：

```bash
# 添加多个远程地址
git remote set-url --add --push origin https://gitee.com/wangluqia/quick-trans.git
git remote set-url --add --push origin https://github.com/TANG-YIN/quick-trans.git

# 然后一次推送即可
git push
```

---

## GitHub Pages vs Gitee Pages 对比

| 特性 | GitHub Pages | Gitee Pages |
|------|--------------|--------------|
| 访问速度 | 国外快，国内较慢 | 国内快 |
| 免费额度 | 完全免费 | 完全免费 |
| HTTPS 支持 | ✅ 自动支持 | ✅ 自动支持 |
| 自动部署 | ✅ 完全自动 | ✅ 自动部署 |
| 自定义域名 | ✅ 支持 | ✅ 支持 |
| 构建速度 | 较快 | 一般 |

**推荐使用：**
- **国内用户**：Gitee Pages（访问速度快）
- **国际用户**：GitHub Pages（稳定可靠）
- **双重部署**：同时使用两个平台，覆盖更广

---

## 常见问题

### Q1: GitHub Pages 显示 404？
A:
1. 检查 Pages 设置中的分支是否正确
2. 确认是否等待了足够的时间（1-3分钟）
3. 查看仓库的 Actions 标签页，看部署是否成功

### Q2: 页面样式错乱？
A:
1. 清除浏览器缓存
2. 检查控制台的错误信息
3. 确认 `dist` 目录下的文件完整性

### Q3: 如何查看部署状态？
A:
1. 访问仓库的 "Actions" 标签页
2. 查看 "pages build and deployment" 工作流
3. 绿色✅表示成功，红色❌表示失败

### Q4: 如何绑定自定义域名？
A:
1. 在 GitHub Pages 设置中点击 "Custom domain"
2. 添加您的域名
3. 配置 DNS 解析到 GitHub 的 IP 地址
4. 等待 SSL 证书自动签发

### Q5: 为什么访问地址后面有个斜杠？
A:
- 如果仓库名不是 `username.github.io`，访问地址会自动加上仓库名
- 这是 GitHub Pages 的正常行为

---

## 项目文件说明

```
quick-trans/
├── .gitignore          # Git 忽略文件配置
├── .env.example        # 环境变量示例
├── index.html          # HTML 入口文件
├── metadata.json       # 项目元数据
├── package.json        # 项目依赖配置
├── README.md           # 项目说明
├── 部署指南.md         # 部署指南（CloudBase）
├── Gitee-Pages部署指南.md  # 部署指南（Gitee）
├── GitHub-Pages部署指南.md  # 部署指南（GitHub）
├── src/
│   ├── App.tsx         # 主应用组件
│   ├── index.css       # 全局样式
│   └── main.tsx        # 应用入口
├── tsconfig.json       # TypeScript 配置
└── vite.config.ts      # Vite 配置
```

---

## 访问地址汇总

### GitHub Pages
```
https://tang-yin.github.io/quick-trans/
```

### Gitee Pages（如果已开启）
```
https://wangluqia.gitee.io/quick-trans
```

---

## 技术支持

如有问题，可以参考：
- GitHub Pages 官方文档：https://docs.github.com/en/pages
- GitHub 帮助中心：https://docs.github.com

---

## 祝您使用愉快！🎉

现在您的 Quick-Trans 已经在 GitHub 上部署，可以在任何设备上访问了！
