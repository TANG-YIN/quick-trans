# Quick-Trans Gitee Pages 部署指南

## 完整部署步骤

### 第一步：创建 Gitee 仓库

1. **注册/登录 Gitee 账号**
   - 访问：https://gitee.com/
   - 如果没有账号，先注册

2. **创建新仓库**
   - 点击右上角的 "+" 号，选择"新建仓库"
   - 填写仓库信息：
     - **仓库名称**：`quick-trans`（或其他您喜欢的名称）
     - **仓库介绍**：24孔板转染计算器 - Quick-Trans
     - **是否公开**：选择"公开"（这样其他人也可以访问）
     - **初始化仓库**：**不要**勾选（我们已经本地初始化了）
   - 点击"创建"

3. **获取仓库地址**
   - 创建后会显示仓库地址，格式类似：
     ```
     https://gitee.com/your-username/quick-trans.git
     ```
   - 复制这个地址

### 第二步：推送代码到 Gitee

**在您的项目目录执行：**

```bash
cd d:/24孔板转染计算器

# 添加远程仓库（替换为您的实际仓库地址）
git remote add origin https://gitee.com/your-username/quick-trans.git

# 推送代码到 Gitee
git push -u origin master
```

**如果遇到认证问题：**

1. Gitee 会要求您输入账号密码
2. 建议使用 SSH 方式（需要先配置 SSH 密钥）：
   ```bash
   git remote set-url origin git@gitee.com:your-username/quick-trans.git
   ```

### 第三步：开启 Gitee Pages 服务

1. **进入仓库设置**
   - 在 Gitee 仓库页面，点击顶部菜单的"服务"
   - 选择"Gitee Pages"

2. **开通 Gitee Pages**
   - 点击"启动"或"开通"按钮
   - **重要**：首次开通 Gitee Pages 可能需要：
     - 手机号验证
     - 实名认证（免费）
   - 验证完成后即可开通

3. **配置 Pages 设置**
   - **部署分支**：选择 `master`
   - **部署目录**：选择 `dist`（构建后的目录）
   - **网站名称**：Quick-Trans
   - 点击"启动"或"更新"

4. **等待构建完成**
   - Gitee 会自动构建您的项目
   - 通常需要 1-5 分钟
   - 构建完成后会显示访问地址，格式类似：
     ```
     https://your-username.gitee.io/quick-trans
     ```

### 第四步：访问您的网站

- 在浏览器中打开 Gitee Pages 提供的访问地址
- 在手机浏览器中打开同一个地址
- 确认功能正常

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

# 推送到 Gitee
git push
```

### 2. 更新 Gitee Pages

**方式一：手动更新**
1. 进入 Gitee 仓库
2. 点击"服务" → "Gitee Pages"
3. 点击"更新"按钮
4. 等待 1-5 分钟，网站就会更新

**方式二：自动更新（推荐）**
Gitee Pages 默认会在每次 push 后自动更新，但如果遇到问题可以手动触发。

---

## 常见问题

### Q1: Gitee Pages 显示"服务未开通"？
A: 需要先进行实名认证和手机号验证，这是 Gitee 的安全要求。

### Q2: 访问页面显示 404？
A:
1. 检查构建目录是否设置为 `dist`
2. 检查是否成功构建了项目（本地运行 `npm run build`）
3. 确保根目录有 `index.html` 文件

### Q3: 页面样式错乱？
A:
1. 检查 `dist` 目录中的文件是否完整
2. 查看浏览器控制台的错误信息
3. 可能需要清除浏览器缓存

### Q4: 更新后 Gitee Pages 没有更新？
A:
1. 尝试手动点击"更新"按钮
2. Gitee Pages 的更新有时需要几分钟时间
3. 清除浏览器缓存后再访问

### Q5: 推送代码时提示权限错误？
A:
1. 检查仓库地址是否正确
2. 确认您有该仓库的推送权限
3. 尝试使用 SSH 方式连接

### Q6: 可以绑定自定义域名吗？
A: 可以！
1. 在 Gitee Pages 设置中点击"自定义域名"
2. 添加您的域名
3. 按提示配置 DNS 解析
4. 等待 SSL 证书签发

---

## Gitee Pages 优势

✅ **完全免费**：无费用，无流量限制
✅ **国内访问快**：服务器在国内，访问速度快
✅ **HTTPS 支持**：自动配置 SSL 证书
✅ **易于使用**：操作简单，界面友好
✅ **版本控制**：与 Git 完美集成
✅ **自动部署**：推送代码自动更新网站

---

## 访问地址说明

### 默认访问地址格式
```
https://your-username.gitee.io/your-repo-name
```

### 示例
如果您的 Gitee 用户名是 `zhangsan`，仓库名是 `quick-trans`，那么访问地址就是：
```
https://zhangsan.gitee.io/quick-trans
```

---

## 项目文件结构说明

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
├── src/
│   ├── App.tsx         # 主应用组件
│   ├── index.css       # 全局样式
│   └── main.tsx        # 应用入口
├── tsconfig.json       # TypeScript 配置
├── vite.config.ts      # Vite 配置
└── dist/               # 构建输出目录（不需要手动上传）
    ├── index.html
    └── assets/
```

---

## 技术支持

如有问题，可以参考：
- Gitee Pages 官方文档：https://pages.gitee.com/
- Gitee 帮助中心：https://gitee.com/help

---

## 祝您部署顺利！🎉

现在您就可以在任何设备（手机、平板、其他电脑）上访问您的 Quick-Trans 了！
