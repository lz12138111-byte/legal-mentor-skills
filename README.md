# Legal Mentor Skills

把资深律师办案方法整理成可复用、可审计、可由律师复核的开放 Agent Skills。

技能 `cn-criminal-defense` 面向中国刑事案件，支持：

- 案情诊断与控方证明路径还原；
- 构成要件、证据和程序审查；
- 主位、备位和兜底策略设计；
- 犯罪数额、损失和资金用途核算思路；
- 取保、不捕、不诉、一审、二审和执行交叉等阶段任务；
- 法律文书起草与律师草稿复核。

当前版本：`v0.2.0`

`v0.2.0` 新增医保骗保专项分析：医保协议标准与刑事事实分层、患者逐案挂床核查、人员权力—信息—行为—获利矩阵、DIP/医保结算申报与实际损失拆分，以及证据不足不起诉、酌定不起诉和取保的三级路径。

## 民事案件法律文书写作skill

新增独立技能 [`cn-civil-litigation-writing`](skills/cn-civil-litigation-writing/SKILL.md)，将诉讼思路、证据组织与法言法语结合，支持民事起诉状、答辩状、上诉状、代理意见、证据目录、情况说明、律师函和内部诉讼方案的起草、修改及复核。

其方法由实务文书匿名提炼，未包含原始材料，也不将样本法律观点固化为现行规则。涉及法律依据、期限与案例时需核验。技能参考文件按任务加载，包含诉讼策略、证据与程序、语言表达、文书类型及虚构练习。

安装到 Codex 个人技能目录（在仓库根目录运行）：

```bash
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills"
cp -R skills/cn-civil-litigation-writing "${CODEX_HOME:-$HOME/.codex}/skills/"
```

调用示例：

```text
使用 $cn-civil-litigation-writing。我代理被告，请根据以下合同、证据和原告诉请，先确定核心抗辩，再起草答辩状；缺失事实明确标记，不自行补写。
```

也可以只要求润色或复核，技能不会因此擅自改变诉讼请求。其他兼容工具可将该完整技能目录安装至其支持的 skills 位置。

## 公开范围

仓库只包含蒸馏后的通用方法、工作流和空白模板，不包含原始案件文书、原始附件、原始案情全文、当事人资料、完整案件分析卡、联系方式、账户、真实案号、卷宗页码或未公开侦查信息。

原始样本只在本地私有训练资料目录维护，不进入本仓库的 Git 历史。

技能自身不包含可执行脚本，不会自动联网或外发数据。调用它的 AI 工具仍可能按照其自身产品设置处理输入；提交案件材料前，请先脱敏并确认数据处理政策。

## 安装

先克隆仓库：

```bash
git clone https://github.com/lz12138111-byte/legal-mentor-skills.git
cd legal-mentor-skills
```

### Codex

安装到个人技能目录：

```bash
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills"
cp -R skills/cn-criminal-defense "${CODEX_HOME:-$HOME/.codex}/skills/"
```

开启新任务后，可直接说：

```text
使用 $cn-criminal-defense。站在辩护人视角分析以下案件，先列事实状态、控方证明路径和证据缺口，再给主备策略。
```

### Kimi Code

安装到 Kimi 与其他兼容工具共享的个人目录：

```bash
mkdir -p "$HOME/.agents/skills"
cp -R skills/cn-criminal-defense "$HOME/.agents/skills/"
```

也可复制到 `$KIMI_CODE_HOME/skills/`（默认 `~/.kimi-code/skills/`）。开启新会话后调用：

```text
/skill:cn-criminal-defense 复核这份不予逮捕法律意见，按阻断性问题、重要问题、优化建议分级。
```

### WorkBuddy / CodeBuddy

在 WorkBuddy 中进入“技能 → 添加技能 → 上传技能”，选择 `skills/cn-criminal-defense` 本地技能包。安装后可在对话中输入 `/` 选择技能，也可用自然语言触发。

使用项目级 CodeBuddy / WorkBuddy Enterprise 时，可复制到工作区：

```bash
mkdir -p .codebuddy/skills
cp -R skills/cn-criminal-defense .codebuddy/skills/
```

## 推荐输入

至少提供以下信息；缺失项可以写“未知”：

```text
代理身份：辩护人 / 被害人代理人 / 其他
程序阶段：
涉嫌罪名：
办案机关原认定：
案件目标：
已知事实：
证据及来源：
不利事实：
希望交付：案件诊断 / 证据审查 / 策略 / 文书草稿 / 文书复核
```

## 重要声明

本项目用于法律研究与律师工作辅助，不构成法律意见，也不能替代执业律师阅读完整卷宗、核验事实证据和确认现行有效法律。中国法律、司法解释、政策和案例会变化；任何拟提交给办案机关或当事人的内容，都必须由具备相应资格、了解完整案情的律师复核。

不得将本技能用于伪造材料、妨害作证、毁灭证据、规避合法监管或其他违法目的。

## 许可证

MIT License。详见 [LICENSE](LICENSE)。

## 测试

仓库使用完全虚构、无个人信息的测试输入覆盖案件分析、诈骗金额拆分、取保方案、走私主观明知分析、庭审提问生成和医保骗保专项审查。测试用例与验收点见 [tests/TEST_CASES.md](tests/TEST_CASES.md)，本版结果见 [tests/RESULTS.md](tests/RESULTS.md)。
