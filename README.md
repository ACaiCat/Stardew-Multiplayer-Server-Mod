# 星露谷物语服务器模组 (Stardew Multiplayer Server Mod)

> **无头服务器**模组，允许主机和游戏世界始终保持在线（类似《我的世界》等在线游戏）。通过自动化主机的日常活动实现（即主机离线时由"机器人"代管）。

---

## 📥 安装方法
1. 安装 **SMAPI**：  
   [https://www.nexusmods.com/stardewvalley/mods/2400](https://www.nexusmods.com/stardewvalley/mods/2400)
2. 将 `Stardew Multiplayer Server Mod` 文件夹放入星露谷游戏目录的 `Mods` 文件夹中。
3. 通过 `StardewModdingAPI.exe` 启动游戏。

---

## 🕹 使用方法
1. 启动游戏前，在 `Stardew Multiplayer Server Mod` 文件夹内修改 `config.json` 配置文件。
2. 像正常流程一样**创建多人游戏**。启动游戏时，服务器模组会自动运行。
3. 按键盘 **F9** 键切换服务器模式开关（当你想亲自操作主机时使用）。

> ⚠️ **重要警告**  
> 游戏窗口**禁止最小化**！否则服务器会在保存界面卡死。  
> （可后台运行/切换窗口，但不可最小化至任务栏。Mac/Linux 系统未测试）

---

## ⚙️ 设置说明
编辑 `Stardew Multiplayer Server Mod` 文件夹内的 `config.json` 文件：

| 配置项                          | 说明                                                                 |
|---------------------------------|----------------------------------------------------------------------|
| `"serverHotKey": "F9"`          | 启动/停止服务器的快捷键                                             |
| `"profitmargin" : 100`          | 利润百分比（%）                                                    |
| `"upgradeHouse": 3`             | 升级主屋等级（3=满级, 0=不升级）                                    |
| `"petname": "Qwerty"`           | 宠物名字（≤10字符，可随时更改）                                    |
| `"farmcavechoicemushrooms": true` | 农场洞穴选择蘑菇（`false`=选择蝙蝠，**首次运行前设定**）           |
| `"communitycenterrun": true`    | 主机执行社区中心路线（`false`=执行Joja路线）                       |
| `"timeOfDayToSleep": 2200`      | 主机睡觉时间（军用制，2200=22:00，最高2600=凌晨2点）               |
| `"lockPlayerChests": true`      | 服务器模式下，禁止玩家访问其他玩家小屋内的箱子/背包                |
| `"clientsCanPause": false`      | 客户端是否可通过聊天命令`!pause/!unpause`暂停游戏                  |
| `"copyInviteCodeToClipboard": true` | 自动复制最新邀请码到剪贴板（每分钟更新）                          |
| `"festivalsOn": true`           | 主机是否参加节日活动                                               |
| `"<eventname>CountDownConfig": 60` | 节日开始后多少秒（秒）触发主活动（如`"EggHuntCountDownConfig":60`）|
| `"<eventname>TimeOut": 120`     | 节日活动超时时间（秒），防止AFK玩家导致卡死（超时后重置连接）       |

---

## 💬 聊天命令
客户端可在游戏卡顿时输入以下命令（需在聊天框中输入）：

| 命令         | 功能                                                                 |
|--------------|----------------------------------------------------------------------|
| `!sleep`     | 若超过设定睡眠时间，尝试触发睡眠指令                                 |
| `!festival`  | 若是节日，尝试触发前往节日指令                                       |
| `!event`     | 尝试触发节日主活动                                                   |
| `!leave`     | 尝试离开节日                                                         |
| `!unstick`   | 尝试将主机传送至农舍内/外（用于解决BUG，节日时可能需要多次尝试）     |

---

## 🌐 服务器访问方式
### 1. 好友列表 (Steam/GoG)
- Steam/GoG 好友可直接通过好友列表加入游戏（与原版相同）。

### 2. 直连 IP (局域网/互联网)
- 使用 **"加入局域网游戏"** 功能：
    - 需在路由器**开放/转发端口 24642**（或使用 [Server Port Changer](https://www.nexusmods.com/stardewvalley/mods/1575) 修改端口）。
    - 将你的**公网 IP** 提供给其他玩家。

### 3. 邀请码 (Steam/GoG 路由)
- **自动复制粘贴**（推荐）：
    - 启用 `copyInviteCodeToClipboard` 后，邀请码会每分钟复制到剪贴板。
    - 使用宏工具（如 [AutoHotkey脚本](https://www.nexusmods.com/stardewvalley/mods/XXXX)）自动粘贴至聊天软件（如Discord）。
- **邀请码机器人**：
    - 模组会将邀请码实时写入 `InviteCode.txt` 文件。
    - 可配合自建机器人（如Node.js Discord Bot）自动发送邀请码。

---

## ✨ 核心功能
- **仅主机需安装此模组**
- **自动化日常**：
    - 主机每天定时传送上床睡觉（默认22:00）
    - 自动查收邮件
    - 自动完成初始设置（洞穴/宠物/房屋等）
    - 自动点击日结界面"确定"按钮（确保游戏正常保存同步）
- **客户端保护**：
    - 可选锁定其他玩家小屋的箱子（`lockPlayerChests`）
    - 所有客户端断开时自动暂停游戏（节日除外，防止卡死）
- **关系系统**：
    - 服务器运行时冻结主机好感度衰减
- **完整节日支持**：
    - 节日开始1分钟后自动触发主活动（预留探索时间）
    - 节日结束前主机不会睡觉
    - 节日超时自动重置（防AFK卡死）
    - 通过聊天框向客户端发送节日/事件提醒
- **事件支持**：
    - 自动跳过爷爷评分、肯特回归等所有过场动画
- **系统优化**：
    - 强制关闭"窗口失焦暂停"选项
- **Joja路线优化**：
    - 当资金≥2倍升级费用时，自动从低价到高价购买Joja升级