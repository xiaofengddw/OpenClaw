# OpenClaw 优化配置指南

## ✅ 已完成的优化配置

### 1. 空间优化配置

#### 已实现：
- ✅ **数据目录迁移**：所有OpenClaw数据已从 `/root/.openclaw` 移动到 `/workspace/.openclaw`（符号链接保持兼容
- ✅ **禁用不需要的技能**：42个不可用/不必要的技能已自动禁用
- ✅ **最小权限配置**：安全配置已设为配对模式（pairing）
- ✅ **优化权限收紧：目录权限已设置为700

### 2. 配置文件说明

#### 当前配置文件位置：`/workspace/.openclaw/openclaw.json`

#### 关键配置：
- **Gateway模式**：本地模式（local）
- **安全策略**：DM配对模式，需要手动审批才能使用
- **插件状态**：66个插件加载，26个禁用

### 3. 环境变量配置

环境变量文件：`/workspace/openclaw.env`

```bash
# 使用方法：
source /workspace/openclaw.env
```

### 4. 目录结构
```
/workspace/.openclaw/
├── openclaw.json          # 主配置文件
├── agents/                # 代理工作区
├── logs/                 # 日志文件
├── sessions/             # 会话存储
├── plugins/              # 插件数据
├── skills/               # 技能目录
└── credentials/          # OAuth凭证
```

### 5. 常用命令

```bash
# 启动Gateway（前台）
openclaw gateway --verbose

# 检查状态
openclaw gateway status

# 修复配置检查
openclaw doctor

# 安全审计
openclaw security audit --deep

# 查看可用模型
openclaw models status

# 查看当前状态
openclaw status
```

### 6. 后续配置建议

由于我们需要手动配置以下内容：

#### AI模型提供商（需要API Key）
```bash
# 设置OpenAI配置示例
export OPENAI_API_KEY=your_key_here
openclaw config set agent.model "openai/gpt-4o"
```

#### 配置消息渠道（Telegram/Discord等需要Bot Token
```bash
# 需要先获取Bot Token后配置
```

#### 命令所有者配置（安全需要设置后才有管理员账户可执行管理命令
```bash
# 示例：
# openclaw config set commands.ownerAllowFrom '["telegram:你的用户ID"]'
```

### 7. 安全说明

- 已禁用的技能列表（优化存储空间，节省空间！已禁用：
- 1password、apple-notes、apple-reminders、bear-notes、blogwatcher、blucli、camsnap、coding-agent、discord、eightctl、gemini、gh-issues、gifgrep、github、gog、goplaces、himalaya、imsg、mcporter、model-usage、nano-pdf、obsidian、openai-whisper、openhue、oracle、ordercli、peekaboo、sag、sherpa-onnx-tts、slack、songsee、sonoscli、spotify-player、summarize、things-mac、tmux、trello、voice-call、wacli、xurl
