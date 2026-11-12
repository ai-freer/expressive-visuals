# 互动案例的源码依据 · 2026-11-12

这份记录用于复查互动指南中的案例，不随 Skill 分发。以下是对具体版本的静态检查，没有据此判断实际手感、可见度或观众理解。

**Saltline。** 检查[作者页面](https://claude.ai/artifact/BGY1SztrAYcJQHSsnHHGmp)此前留存的内嵌 legacy-v8 脚本，SHA-256 为 `8d0057dc4d6dac77e20be2ef1f2b623e19346b5803fde1b3dbabbab508d75d9d`。检索 `objective:done` 可定位完成处理：递增切断数，把中继对象设为 cut，刷新 HUD 计数与目标。对象的 setState/update 在 cut 后把灯光强度从亮、闪烁衰减到零；目标文本在 allCut 后改为去船上，标记列表加入撤离点。依据是对象更新和目标分支，不是对截图外观的推测。这不是对当前活动脚本的逐版本保证。

**归藏《雾锁山门》。** [发布快照 21683d9](https://github.com/op7418/guizang-game-skill/tree/21683d9e00bd3736efe52f78d8380debbd2af3d3) 中的 game.cdb73b9b.js 可检索 `re.parry()`：同一判定分支更新体力、震动、闪光并发声。声音方法叠加 metal、ring 采样与合成音；assets/ 保留模型和音频。调试对象赋给 window.G，公开 press 和 step；启动逻辑读取 stage=boss。[角色动作制作笔记](https://github.com/op7418/guizang-game-skill/blob/6001e56e1eaa60be49e5aa4ef81d08b746a1b4e2/references/characters-animation.md)另外说明定制动作如何用肘膝朝向和两段骨骼解算。这是作者的方法说明，不能据此断言所有动作都实时求解。

Clockmaker 的部位视角和 Tidewright 的波面计算沿用[前次案例研究](2026-11-11-fable-5-2-3d-case-review.md)。指南中的凸轮、琴弦和标注展品是迁移示例，不是这些作品的实测结果。
