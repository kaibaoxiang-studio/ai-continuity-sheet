# ai-continuity-sheet

AI 短剧场记表生成器。输入纯剧本，调度子 skill 填写 13 列，由 `scripts/convert_continuity_sheet.py` 输出 Excel 场记表（首行为对应集数剧本原文的合并单元格）。

## 包含的 Skill

| Skill | 职责 |
|-------|------|
| `ai-continuity-sheet` | 编排层，调度子 skill 并生成 Excel |
| `cinematography-advisor` | 摄影列（设备，焦段，机位，镜头运动） |
| `lighting-colorist` | 灯光/色卡列（光源方向，色调关键词） |
| `dialogue-formatter` | 台词列（原文精简，OS 加括号） |
| `shot-duration-calculator` | 时长列（4 字 = 1 秒，模型上限内） |
| `micro-expression-director` | 微表情情绪指导列（可见细节，10 字内） |
| `action-performance-director` | 动作表演指导列（起始→核心→结尾，15 字内） |
| `scene-synopsis` | 剧情大纲列（事件 + 力量变化，15 字内） |

## 使用

1. 将这些目录放入 `~/.claude/skills/`
2. 在对话中提到"场记表"或"生成表格"即可激活
3. 主 skill 确认模型、画幅、灯光效果后逐行生成场记表

## 依赖

- Python 3 + openpyxl（生成 .xlsx）
- 被主 skill 调用：jimeng-storyboard-v3 与 leos-six-department-directing-team-skill-v1
