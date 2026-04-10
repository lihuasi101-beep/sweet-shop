# MEMORY.md - 长期记忆

## 项目：甜品店经营游戏 (sweet-shop.html)

### 更新日志

#### v0.1 — 2026-04-09 初版功能
- 基础经营循环：顾客入座 → 点餐 → 上菜 → 收金币
- 菜单系统（多种甜品，解锁机制）
- 升级系统（金币、小费加成、员工效率等）
- 雇员系统（自动服务，isServing锁防重复）
- 等待区（顾客排队，超时离开）
- 难度选择（简单/普通/困难，对应不同色调主题）

#### v0.2 — 2026-04-09 UI/UX优化轮
- 空座位虚线框、倒计时条加粗、粒子效果、等待区强化等11项视觉优化
- Bug修复：雇员状态不更新、雇员重复服务、菜品默认未选中、等待区无超时、经验值溢出

#### v0.3 — 2026-04-09 晚：成就系统
- 17个成就（服务类/金币类/等级类/完美服务类/雇员类/特殊类）
- 成就弹窗动画 + 粒子庆祝效果
- 成就面板侧边栏
- 进度显示（进度条 + 数值）
- 连续服务计数（currentStreak / bestStreak）

#### v0.4 — 2026-04-09 深夜：移动端适配
- 顶部状态栏精简
- 底部固定Tab导航（菜单/雇员/升级）
- 右侧面板 → 底部弹出式面板
- 座位点击自动开/关面板

#### v0.5 — 2026-04-10 上午：Bug修复 + 弹窗UI优化
**Bug修复：**
1. 成就弹窗期间进度条仍在走 → setInterval 加 `if (gameData.paused) return`
2. 成就弹窗无领取按钮 → 恢复按钮显示，奖励金币改为点击"领取"时才发放（pendingAchievement机制）
3. 顾客上菜后闪现 → 重构 serveCustomer，上菜后立即从数据+DOM移除，不保留"已服务"中间状态

**UI优化：**
- 成就弹窗奖励金币改为标签展示（虚线边框+小字"奖励"前缀），不再像按钮
- 领取按钮改为粉红渐变，视觉明确区分
- 修复桌面端 tab-nav 文字裸露问题（全局CSS隐藏，移动端再显示）

#### v0.6 — 2026-04-10 下午：移动端全面适配
- 触控优化：同时支持鼠标和触控，长按500ms显示顾客信息Tooltip
- 新增"设置"Tab（难度选择卡片 + 游戏统计）
- 横屏适配：左右分栏布局，面板移至右侧，Tab改为2x2网格
- 成就面板：移动端改为底部弹出而非侧边滑入

#### v0.7 — 2026-04-10 下午：移动端视觉优化
- 待招待界面：改为右侧悬浮卡片（position:absolute top:42px right:6px），白色半透明卡片+阴影，emoji缩小至26px
- 座位计数器：移入.shop-scene末尾，改为相对定位flex子元素，配合seats的flex-wrap自然排在座位行下方，不再用absolute bottom
- 顾客与收银台间距：收银台上移至bottom:70px（座位bottom:60px+58px=118px留出间距），cupcake装饰同步缩小上移
- 修复：给.shop-scene加position:relative，确保移动端绝对定位正确参照

### 技术要点
- 使用 data-seat 属性精确匹配DOM元素
- 事件委托绑定在 seatsContainer 用 onmousedown
- 生气阈值50%，简单难度默认选中
- CSS变量系统用于动态主题切换
- `pendingAchievement` + `pendingCustomer` 双队列机制处理成就弹窗期间的状态

---

## 项目：分手骰子游戏指南 (index.html)

### 2026-04-09 完成
- 为用户创建了《分手骰子》游戏完全指南线上文档
- 部署到 GitHub Pages: https://lihuasi101-beep.github.io/dice-game-guide/
- 包含内容：骰子图鉴(12+种)、护身符图鉴(25+种)、角色图鉴(6个)、特性图鉴、通关攻略
- GitHub 仓库: https://github.com/lihuasi101-beep/dice-game-guide

### 用户偏好
- 使用 GitHub Pages 托管静态网页
- 仓库路径: D:\coding\workBuddy\dice-game-guide
- GitHub 用户名: lihuasi101-beep

### 常用命令
```bash
# 推送更新到 GitHub
cd "D:/coding/workBuddy/dice-game-guide"
git add index.html
git commit -m "更新说明"
git push origin main
```
