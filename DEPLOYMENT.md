# 部署指南

## 📋 上传到GitHub的详细步骤

### 1. 准备工作

确保您已经完成了API密钥的隐藏处理：

- ✅ API密钥已从代码中移除
- ✅ 使用了本地存储方式
- ✅ 添加了用户配置界面

### 2. 创建GitHub仓库

1. **登录GitHub**

   - 访问 [GitHub.com](https://github.com)
   - 登录您的账号
2. **创建新仓库**

   - 点击右上角的 "+" 号
   - 选择 "New repository"
   - 填写仓库名称：`buddhist-ai-translator`
   - 选择 "Public"（公开）或 "Private"（私有）
   - 不要勾选 "Initialize this repository with a README"
   - 点击 "Create repository"

### 3. 上传代码

#### 方法一：使用Git命令行（推荐）

```bash
# 1. 进入项目目录
cd 佛教文本AI翻译器_v4

# 2. 初始化Git仓库
git init

# 3. 添加所有文件
git add .

# 4. 提交代码
git commit -m "初始提交：佛教文本AI翻译器"

# 5. 添加远程仓库（替换为您的用户名）
git remote add origin https://github.com/YOUR_USERNAME/buddhist-ai-translator.git

# 6. 推送到GitHub
git push -u origin main
```

#### 方法二：使用GitHub Desktop

1. 下载并安装 [GitHub Desktop](https://desktop.github.com)
2. 登录您的GitHub账号
3. 点击 "Add an Existing Repository from your Hard Drive"
4. 选择项目文件夹
5. 填写提交信息并点击 "Commit to main"
6. 点击 "Publish repository"

#### 方法三：通过Web界面上传

1. 在GitHub仓库页面点击 "uploading an existing file"
2. 将所有项目文件拖拽到页面中
3. 填写提交信息
4. 点击 "Commit changes"

### 4. 配置部署

#### GitHub Pages部署

1. **启用GitHub Pages**

   - 在仓库页面点击 "Settings"
   - 滚动到 "Pages" 部分
   - 在 "Source" 下选择 "Deploy from a branch"
   - 选择 "main" 分支
   - 选择 "/ (root)" 文件夹
   - 点击 "Save"
2. **访问您的站点**

   - 部署完成后，您的网站将在以下地址可用：
   - `https://YOUR_USERNAME.github.io/buddhist-ai-translator`

#### Vercel部署（替代方案）

1. 访问 [Vercel.com](https://vercel.com)
2. 使用GitHub账号登录
3. 点击 "New Project"
4. 选择您的GitHub仓库
5. 点击 "Deploy"

#### Netlify部署（替代方案）

1. 访问 [Netlify.com](https://netlify.com)
2. 使用GitHub账号登录
3. 点击 "New site from Git"
4. 选择GitHub并授权
5. 选择您的仓库
6. 点击 "Deploy site"

### 5. 后续维护

#### 更新代码

```bash
# 1. 修改代码后，添加更改
git add .

# 2. 提交更改
git commit -m "描述您的更改"

# 3. 推送到GitHub
git push origin main
```

#### 分支管理

```bash
# 创建开发分支
git checkout -b development

# 切换分支
git checkout main
git checkout development

# 合并分支
git checkout main
git merge development
```

## 🔒 安全注意事项

### API密钥安全

- ✅ 永远不要在代码中硬编码API密钥
- ✅ 使用本地存储或环境变量
- ✅ 在README中说明如何配置密钥
- ✅ 定期轮换API密钥

### .gitignore文件

确保您的 `.gitignore` 文件包含：

```
# 敏感配置文件
config.local.js
.env
.env.local
api-config.js

# 用户数据
user-config.json
```

### 代码审查

- 上传前检查是否有敏感信息
- 使用 `git log --oneline` 检查提交历史
- 如果意外提交了密钥，立即轮换API密钥

## 🌐 域名配置（可选）

如果您有自定义域名：

1. **添加CNAME文件**

   ```bash
   echo "your-domain.com" > CNAME
   git add CNAME
   git commit -m "添加自定义域名"
   git push origin main
   ```
2. **配置DNS**

   - 在您的域名提供商处添加CNAME记录
   - 指向 `YOUR_USERNAME.github.io`

## ❓ 常见问题

### Q: 部署后翻译功能不工作？

A: 请确保：

- 已配置有效的DeepSeek API密钥
- API密钥有足够的配额
- 网站是通过HTTPS访问的

### Q: 如何删除Git历史中的敏感信息？

A: 使用以下命令：

```bash
# 警告：这会重写历史记录
git filter-branch --force --index-filter \
'git rm --cached --ignore-unmatch path/to/sensitive/file' \
--prune-empty --tag-name-filter cat -- --all

# 强制推送
git push origin --force --all
```

### Q: 部署到GitHub Pages后出现404错误？

A: 检查：

- 分支设置是否正确
- 文件名是否为 `index.html`
- 路径是否正确

## 🎉 完成！

恭喜！您已经成功将佛教文本AI翻译器部署到了云端。现在任何人都可以访问您的翻译器，但需要他们自己的API密钥来使用翻译功能。

记住定期更新您的代码，并关注用户反馈以持续改进您的翻译器！
