# 物理实验室 · Physics Lab

> 一本可以玩的 2D 物理教科书。拖出元件，连接电路，调整环境，让物理自己发生。

一个单文件、零依赖的 2D 物理沙盒。所有运动都由实时物理积分驱动，不是预设动画。适合课堂演示、自学实验，也适合单纯拆着玩。

A single-file, dependency-free 2D physics sandbox. Every motion is driven by real-time integration, not canned animation. Built for classroom demos, self-study, and playful experimentation.

---

## 中文

### 简介

物理实验室把常见的物理元件做成可以拖拽的“纸片教具”。你可以在米白色纸面上自由搭建斜面、弹簧、电路、场和量子实验，观察它们在真空、地球、月球、太空或水下的不同表现。

- **单文件**：整个游戏就是一个 `物理实验室.html`，不需要安装、不需要联网。
- **43 种元件**：力学 22、电学 10、场与量子 11。
- **5 种环境**：真空、地球、月球、太空、水下。
- **真实积分**：固定 120 Hz 物理步进，每步 2 个子步；碰撞、约束、电路和场力同时参与计算。
- **简笔视觉**：所有元件都是手绘线稿风格，实时调试数值叠加在物体旁边。

### 五种环境

| 环境 | 重力 | 介质与特点 |
|---|---|---|
| 真空（默认） | 9.81 m/s² | 无空气阻力，羽毛和铁球下落一样快 |
| 地球 | 9.81 m/s² | 空气阻力、风力，轻物体有明显终端速度 |
| 月球 | 1.62 m/s² | 低重力，真空 |
| 太空 | 0 | 零重力，适合动量与推进实验 |
| 水下 | 9.81 m/s² | 水线以下有阿基米德浮力与流体阻力，木球上浮、铁球下沉 |

### 43 种物理元件

| 分类 | 数量 | 元件 |
|---|---:|---|
| 力学 | 22 | 小球、铁球、方块、三角块、六棱块、轻羽片、砝码、斜面、平台、风扇、推进器、磁铁、背景锚点、多米诺、气球、传送带、玻璃块、弹力球、冰块、弹簧、绳子、测力计 |
| 电学 | 10 | 电池、铜线、灯泡、电阻、开关、电容、电流表、电荷球、电磁铁、LED 灯 |
| 场与量子 | 11 | 电场区、磁场区、重力场区、风场区、引力井、量子粒子、量子纠缠对、势垒、双缝、量子比特、量子源 |

每种元件都可以在属性面板或右键菜单里调整尺寸、密度、摩擦、恢复系数、电荷、电压、电阻、电容、场强等参数。

### 操作方式

| 操作 | 功能 |
|---|---|
| 从左侧拖出元件 | 放置元件；拖动距离决定初始大小 |
| 在画布上单击 | 以默认大小放置 |
| 空白处拖拽 | 框选多个物体 |
| `Shift` + 点击 | 增加/移除选择 |
| 拖动物体 | 移动；松手时保留拖动惯性 |
| `Alt` + 拖动 | 旋转物体 |
| 鼠标右键 | 打开快捷参数菜单（物体、铜线、弹簧、绳子、测力计、纠缠对） |
| 中键拖动 / `WASD` | 平移场景 |
| 滚轮 / `=` / `-` | 缩放场景 |
| `Space` | 暂停 / 继续 |
| `.` | 单步推进 |
| `F` | 固定 / 解除固定 |
| `[` / `]` | 逆时针 / 顺时针旋转 15° |
| `Ctrl+D` | 克隆选中物体 |
| `Ctrl+A` | 全选 |
| `Delete` | 删除选中物体或连线 |
| `G` | 显示 / 隐藏速度、力矢量 |
| `Alt+D` | 显示 / 隐藏实时调试数值 |
| `H` / `?` | 打开帮助 |

### 物理模型

- **积分**：半隐式欧拉，固定步长 `1/120 s`，每步 2 个子步。
- **碰撞**：旋转 AABB 宽相 + SAT/裁剪窄相 + 顺序冲量求解，含摩擦、恢复系数和位置修正。
- **边界**：按旋转后的真实 AABB 与场地边界接触，不使用外接圆。
- **力**：重力、空气阻力、水的浮力与阻力、弹簧力、绳张力、测力计读数、库仑力、磁铁吸引、风扇、推进器、传送带表面速度。
- **场**：匀强电场 `qE`、磁场洛伦兹力 `qv×B`、自定义方向重力场、区域风场、反平方引力井。
- **电路**：节点电压法 + 高斯消元；支持电池内阻、电阻、灯泡、开关、电容瞬态、电流表、LED 和电磁铁线圈。
- **量子**：概率隧穿、双缝干涉、量子比特测量坍缩、反相关纠缠对。
- **比例**：`60 px = 1 m`；二维模型使用面密度，浮力、质量和弹簧力在同一套等效单位下计算。

> 这是一个教学用二维模型，不是完整的波函数数值解，也不替代真实实验。量子部分为概念演示。

### 运行

直接用 Chrome、Edge 或 Firefox 打开：

```text
物理实验室.html
```

无需安装依赖，无需本地服务器。

### 发布到 GitHub Pages

1. 把 `物理实验室.html` 复制/重命名为 `index.html`。
2. 上传到 GitHub 仓库根目录。
3. 打开仓库 **Settings → Pages**。
4. Source 选 **Deploy from a branch**，Branch 选 `main`，目录选 `/(root)`，保存。
5. 等 1–2 分钟，访问：

```text
https://你的用户名.github.io/仓库名/
```

也可以用命令行：

```bash
git init
git add index.html README.md
git commit -m "feat: 2D physics sandbox"
git branch -M main
git remote add origin https://github.com/你的用户名/仓库名.git
git push -u origin main
```

然后在 GitHub Pages 中启用 `main / (root)`。

### 项目结构

```text
物理实验室.html   # 游戏本体（单文件）
index.html        # 部署到 Pages 时使用的入口文件（可由上者重命名）
README.md         # 本介绍
```

### 浏览器建议

- 桌面端 Chrome / Edge 体验最佳。
- 手机端可以使用，侧栏会折叠为抽屉，画布会自适应屏幕。
- 音效需要一次点击/按键后才能启用，这是浏览器的自动播放限制。

---

## English

### Overview

Physics Lab turns common physics props into draggable paper models. Build ramps, springs, circuits, fields, and quantum experiments on a warm off-white canvas, then watch them behave differently in vacuum, on Earth, on the Moon, in space, or underwater.

- **Single file**: the whole game is one `物理实验室.html`; no install, no network required.
- **43 components**: 22 mechanics, 10 electrics, 11 field & quantum.
- **5 environments**: vacuum, Earth, Moon, space, underwater.
- **Real integration**: fixed 120 Hz stepping with 2 substeps; collisions, constraints, circuits, and field forces all run together.
- **Sketch visuals**: every component is hand-drawn line art, with live debug values next to objects.

### Environments

| Environment | Gravity | Medium / behavior |
|---|---|---|
| Vacuum (default) | 9.81 m/s² | No air drag; a feather and an iron ball fall at the same rate |
| Earth | 9.81 m/s² | Air drag and wind; light objects reach terminal velocity |
| Moon | 1.62 m/s² | Low gravity, vacuum |
| Space | 0 | Zero gravity; ideal for momentum and thruster experiments |
| Underwater | 9.81 m/s² | Archimedes buoyancy and fluid drag below the waterline; wood floats, iron sinks |

### 43 Components

| Category | Count | Items |
|---|---:|---|
| Mechanics | 22 | ball, iron ball, box, triangle, hexagon, feather, weight, ramp, platform, fan, thruster, magnet, background anchor, domino, balloon, conveyor, glass block, rubber ball, ice block, spring, rope, force gauge |
| Electrics | 10 | battery, copper wire, bulb, resistor, switch, capacitor, ammeter, charge ball, solenoid, LED |
| Field & quantum | 11 | electric field, magnetic field, gravity field, wind field, gravity well, quantum particle, entangled pair, barrier, double slit, qubit, quantum source |

Every component exposes its size, density, friction, restitution, charge, voltage, resistance, capacitance, field strength, and other parameters in the inspector or the right-click menu.

### Controls

| Input | Action |
|---|---|
| Drag from the left palette | Place a component; drag distance sets its initial size |
| Click on canvas | Place at default size |
| Drag empty canvas | Marquee-select multiple objects |
| `Shift` + click | Add/remove from selection |
| Drag an object | Move it; release to keep the drag inertia |
| `Alt` + drag | Rotate an object |
| Right-click | Quick parameter menu (bodies, wires, springs, ropes, gauges, entangled pairs) |
| Middle-drag / `WASD` | Pan the camera |
| Wheel / `=` / `-` | Zoom |
| `Space` | Pause / resume |
| `.` | Single step |
| `F` | Fix / unfix |
| `[` / `]` | Rotate 15° counter-clockwise / clockwise |
| `Ctrl+D` | Clone selection |
| `Ctrl+A` | Select all |
| `Delete` | Delete selected bodies or links |
| `G` | Toggle velocity/force vectors |
| `Alt+D` | Toggle live debug values |
| `H` / `?` | Help |

### Physics Model

- **Integration**: semi-implicit Euler, fixed `1/120 s` step, 2 substeps per step.
- **Collision**: rotated-AABB broad phase + SAT/clipping narrow phase + sequential impulses, with friction, restitution, and positional correction.
- **Bounds**: rotated AABB against the stage boundary, not a bounding circle.
- **Forces**: gravity, air drag, buoyancy and fluid drag, spring force, rope tension, gauge reading, Coulomb force, magnet attraction, fan, thruster, conveyor surface velocity.
- **Fields**: uniform electric `qE`, magnetic Lorentz `qv×B`, directional gravity, regional wind, inverse-square gravity well.
- **Circuits**: nodal analysis with Gaussian elimination; battery internal resistance, resistors, bulbs, switches, capacitor transients, ammeter, LED, and solenoid coil.
- **Quantum**: probabilistic tunneling, double-slit interference, qubit measurement collapse, anti-correlated entangled pairs.
- **Scale**: `60 px = 1 m`; the 2D model uses areal density so buoyancy, mass, and spring forces share one consistent effective unit system.

> This is a teaching-oriented 2D model, not a full wave-function solver and not a substitute for a real lab. The quantum section is conceptual.

### Run

Open the file directly in a modern browser:

```text
物理实验室.html
```

No dependencies, no local server needed.

### Deploy to GitHub Pages

1. Copy/rename `物理实验室.html` to `index.html`.
2. Upload it to the repository root on GitHub.
3. Open **Settings → Pages**.
4. Set Source to **Deploy from a branch**, Branch to `main`, folder to `/(root)`, then save.
5. Wait 1–2 minutes and open:

```text
https://your-username.github.io/your-repo/
```

Or use the command line:

```bash
git init
git add index.html README.md
git commit -m "feat: 2D physics sandbox"
git branch -M main
git remote add origin https://github.com/your-username/your-repo.git
git push -u origin main
```

Then enable `main / (root)` in GitHub Pages.

### Project Layout

```text
物理实验室.html   # the game (single file)
index.html        # optional Pages entry point (renamed copy)
README.md         # this document
```

### Browser Notes

- Best on desktop Chrome / Edge.
- Mobile works; side panels collapse into drawers and the canvas adapts to the screen.
- Sound requires one click or key press because of browser autoplay policies.

---

如果这个项目对你有帮助，欢迎点一个 Star。  
If you find this project useful, a star is appreciated.
