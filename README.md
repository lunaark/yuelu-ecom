# yuelu-ecom

一个用于生成电商商品详情页长图的 AI Skill。

输入产品名称、价格和可选素材后，Skill 会自动完成模板选择、卖点文案、SVG/HTML 线框、AI 上色和多屏长图拼接。内置快闪版、标准版和深度版三套结构，适配不同客单价与决策成本。

## 安装

### Codex

```bash
git clone https://github.com/lunaark/yuelu-ecom.git ~/.codex/skills/yuelu-ecom
```

### Claude Code

```bash
git clone https://github.com/lunaark/yuelu-ecom.git ~/.claude/skills/yuelu-ecom
```

重启对应工具后，说“帮我做一个商品详情页”即可触发。

## Codex 无需配置 API

在 Codex 中使用时，Skill 会直接调用内置图片生成工具完成产品图生成和线框上色，不需要 API Key。

只有运行环境没有原生图片生成能力时，才需要复制并修改 `config.env`，接入兼容的图片生成接口：

```env
IMAGE_API_ENDPOINT=https://你的接口地址/v1/images/edits
IMAGE_GEN_ENDPOINT=https://你的接口地址/v1/images/generations
IMAGE_API_KEY=你的API_KEY
```

请勿将真实密钥提交到 GitHub。

## 工作流

1. 收集产品、价格、文案和产品图。
2. 按品类与客单价匹配 5、10 或 12 屏模板。
3. 生成每屏文案及产品主图。
4. 使用 SVG/HTML 锁定版式。
5. 调用图片模型完成风格化上色。
6. 校对文字并拼接为完整详情页长图。

完整规则请阅读 [SKILL.md](SKILL.md)。

## 完整案例

仓库包含 2 套由同一套工作流生成的完整商品详情页，可点击查看原图：

- [阳光鲜榨 NFC 橙汁（10 屏）](examples/orange-juice-detail-page.png)
- [手工燕麦曲奇（5 屏）](examples/oatmeal-cookie-detail-page.png)

## 依赖

- 可截图 HTML/SVG 的浏览器工具
- Codex 内置图片生成工具；其他环境可使用兼容图片生成 API
- Python Pillow

## License

[MIT](LICENSE)
