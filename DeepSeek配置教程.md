# 🦞 OpenClaw + DeepSeek-V4-Flash 配置教程

## ✅ 已完成的工作

我已经帮你更新了配置文件，模型已设置为 **deepseek/deepseek-v4-flash**！

---

## 📋 接下来你需要做的

### 第一步：获取 DeepSeek API Key

1. 访问 DeepSeek 开放平台：https://platform.deepseek.com/
2. 登录或注册账号
3. 完成实名认证（必须）
4. 充值（新用户通常有免费额度）
5. 进入 **API Keys** 页面
6. 点击 **创建 API key**
7. 输入名称（如：OpenClaw）
8. **立即复制保存 API Key**（只显示一次！）

### 第二步：设置环境变量

**方法一：临时设置（当前终端有效）**

```bash
export DEEPSEEK_API_KEY=你的-api-key
```

**方法二：永久设置（推荐）**

编辑你的 shell 配置文件：
- 如果用 bash：编辑 `~/.bashrc`
- 如果用 zsh：编辑 `~/.zshrc`

在文件末尾添加：
```bash
export DEEPSEEK_API_KEY=你的-api-key
```

保存后，重新加载配置：
```bash
# 如果是 bash
source ~/.bashrc

# 如果是 zsh
source ~/.zshrc
```

### 第三步：重启 Gateway

先停止当前运行的 Gateway，然后重新启动：

```bash
# 重新启动 Gateway
openclaw gateway --verbose
```

### 第四步：验证配置

打开新的终端窗口，验证配置：

```bash
# 查看 DeepSeek 可用模型
openclaw models list --provider deepseek

# 检查状态
openclaw status

# 健康检查
openclaw doctor
```

### 第五步：开始使用！

打开浏览器访问：**http://127.0.0.1:18789/**

---

## 🎯 DeepSeek 模型说明

OpenClaw 支持以下 DeepSeek 模型：

| 模型引用 | 名称 | 特点 |
|---------|------|------|
| `deepseek/deepseek-v4-flash` | DeepSeek V4 Flash | ⭐ 默认推荐，响应快，100万上下文 |
| `deepseek/deepseek-v4-pro` | DeepSeek V4 Pro | 更强的模型，质量更高 |
| `deepseek/deepseek-chat` | DeepSeek Chat | V3.2 版本，经济实惠 |
| `deepseek/deepseek-reasoner` | DeepSeek Reasoner | 推理专用 |

---

## 💡 DeepSeek V4 特殊功能

### Thinking 思考模式

DeepSeek V4 支持深度思考！在聊天中可以使用：

| 命令 | 效果 |
|------|------|
| `/think off` | 关闭思考（快速） |
| `/think low` | 低强度思考 |
| `/think medium` | 中等思考（默认） |
| `/think high` | 高强度思考 |
| `/think xhigh` | 极高强度思考 |
| `/think max` | 最大强度思考 |

### 超大上下文

- 支持 **1,000,000 token** 上下文！
- 可以处理超长文档
- 输出最多 **384,000 token**

---

## 🔧 配置确认

### 检查当前配置

```bash
# 查看配置文件
cat ~/.openclaw/openclaw.json
```

你应该能看到这些配置项：
```json
{
  "agent": {
    "model": "deepseek/deepseek-v4-flash",
    "thinking": "medium"
  },
  "agents": {
    "defaults": {
      "model": {
        "primary": "deepseek/deepseek-v4-flash"
      }
    }
  }
}
```

### 切换模型（如果需要）

如果你想切换到其他模型：

```bash
# 切换到 Pro 版本
openclaw config set agent.model "deepseek/deepseek-v4-pro"

# 切换到 Chat 版本（更便宜）
openclaw config set agent.model "deepseek/deepseek-chat"
```

---

## ❓ 常见问题

### Q1: 提示找不到 API Key？

确保环境变量已正确设置：
```bash
# 检查环境变量
echo $DEEPSEEK_API_KEY

# 如果没有输出，说明没设置成功
```

### Q2: 如何切换回其他模型？

```bash
# 比如切换回 OpenAI
openclaw config set agent.model "openai/gpt-4o"
```

### Q3: DeepSeek 支持哪些功能？

- ✅ 实时流式输出
- ✅ 工具调用（Tool use）
- ✅ 思考过程显示
- ✅ 超长上下文
- ✅ 多轮对话

---

## 📚 更多资源

- **官方文档**：https://docs.openclaw.ai/providers/deepseek
- **DeepSeek 平台**：https://platform.deepseek.com/
- **完整教程**：查看 [保姆级教程.md](file:///workspace/保姆级教程.md)

---

## 🎉 快速检查清单

在你开始之前确认：

- [ ] 已获取 DeepSeek API Key
- [ ] 已设置 `DEEPSEEK_API_KEY` 环境变量
- [ ] 已重启 Gateway
- [ ] 可以访问 http://127.0.0.1:18789/
- [ ] 模型显示为 deepseek/deepseek-v4-flash

准备好就可以开始聊天了！🚀
