# Antigravity Swarm Command Center

> 🚀 专为 Google Antigravity 设计的独立、全尺寸、纯 Web 实时多智能体集群（Swarm）总指挥看板。
> 兼容 **macOS** 与 **Linux**，**零外部 npm 依赖**，开箱即用。

---

## 🌟 核心特性

- **🖥️ 独立全尺寸面板**：脱离 IDE 侧边栏宽度限制，在任何浏览器（Chrome, Safari, Edge, Firefox 等）中全屏展示。
- **🌐 动态交互拓扑 (Graph Tab)**：基于 `@mention` 关系流，实时渲染多智能体间的交互网络与指向拓扑（由 `hive.js` 驱动）。
- **👥 实时节点名册 (Members Tab)**：实时跟踪所有 Worker / Coordinator 的当前状态（`working` / `waiting` / `killed`）、绑定的模型与活动时间戳。
- **💬 广播消息总线 (Board Feed)**：群组聚合、`@mention` 高亮及 `#seq` 消息锚点跳转。
- **⚡ 零外部依赖 (Zero Dependency)**：100% 使用 Node.js 原生标准库，无跨平台编译负担，跨设备即插即用。
- **🐧 跨平台自适应 (macOS & Linux)**：自动探测并适配 macOS 和 Linux 下的 Antigravity 数据存储目录。

---

## 📦 目录结构

```text
.
├── plugin.json                 # Antigravity 插件配置清单
├── README.md                   # 插件使用指南
├── bin/
│   └── swarm-dashboard        # macOS & Linux 通用 CLI 启动脚本 (chmod +x)
├── skills/
│   └── swarm-dashboard/
│       └── SKILL.md            # 注册 /swarm-dashboard 技能
└── sidecars/
    └── swarm_board/
        ├── main.mjs            # 核心后端逻辑 (自适应 AppData 探测与状态快照)
        ├── channels.mjs        # 消息与频道过滤器
        ├── index.html          # 原生全尺寸看板 UI
        ├── app.js              # 动态轮询与响应式渲染 (纯 Web 模式)
        ├── hive.js & hive.css  # 智能体关系拓扑图
        └── styles.css          # 原生自适应主题
```

---

## 🚀 安装与使用指南

### 1. 全局安装（所有项目通用，推荐）

将仓库克隆到当前用户机器的全局插件目录下：

```bash
git clone https://github.com/LaciaType-005/antigravity-swarm-dashboard.git ~/.gemini/config/plugins/swarm-dashboard
```

克隆完成后，这台机器上的所有 Antigravity 项目与会话均可自动识别并使用该插件。

---

### 2. 项目专属安装（随团队代码库共享）

将本仓库作为项目的一个插件模块放入项目根目录下的 `.agents/plugins/`：

```bash
mkdir -p .agents/plugins/
git clone https://github.com/LaciaType-005/antigravity-swarm-dashboard.git .agents/plugins/swarm-dashboard
```

提交至团队 Git 仓库后，其他成员拉取项目即可自动加载，无需额外安装。

---

### 3. 启动看板服务

在终端中直接运行启动脚本（默认监听 `4820` 端口）：

```bash
# 进入插件根目录
./bin/swarm-dashboard

# 或者指定自定义端口启动：
PORT=5000 ./bin/swarm-dashboard
```

启动后控制台会输出：
```text
[swarm_board] app data dirs: /path/to/.gemini/antigravity
[Swarm Dashboard] Listening on http://127.0.0.1:4820/
```

---

### 4. 浏览器访问与 URL 参数

在浏览器中打开如下格式的地址（将 `<CONVERSATION_ID>` 替换为您当前 Swarm 会话的 ID）：

```text
http://127.0.0.1:4820/?conversationId=<CONVERSATION_ID>
```

#### 实用参数：
| 参数 | 说明 | 示例 |
| :--- | :--- | :--- |
| `conversationId` | **必填**，目标 Swarm 的会话 ID | `?conversationId=24343021-2596-4bd7-90fe-520f4e683541` |
| `tab` | 直达指定标签页 (`feed` / `members` / `graph` / `raw`) | `&tab=graph` (直达拓扑图) |

---

## 🔧 系统要求

- **操作系统**：macOS 或 Linux (Ubuntu, Debian, CentOS, Fedora, Arch 等)
- **Node.js**：v18 或更高版本（通过 `node -v` 验证）
- **依赖**：无需执行 `npm install`。

---

## 📄 开源与致谢
基于 Antigravity 原生 Swarm 看板架构扩展构建，专为提升多智能体协作与系统可视化设计。
