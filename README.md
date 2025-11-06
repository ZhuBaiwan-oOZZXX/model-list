感谢 [https://github.com/lobehub/lobe-icons](https://github.com/lobehub/lobe-icons) 项目提供的图标

## deno 部署
1. 登录 [deno](https://dash.deno.com)
2. 创建一个 New Playground
3. 粘贴 deno.ts 代码
4. 设置中添加环境变量

环境变量至少添加：
- `API_URL`：需填写至 /v1/models，例如：`https://api.openai.com/v1/models`
- `API_KEY`：对应密钥

## 添加分组

1. 添加图标在 `ICON_CONFIG` 配置，冒号前的内容为分组名称，其中的 `icon` 和 `keywords` 属性为模型图标的 URL 和匹配模型用的关键词

2. 怎么分组的：
- 程序会遍历从 API 获取到的每一个模型名
- 将模型名（转为小写后）与 `GROUP_CONFIG` 中定义的分组按顺序进行关键词匹配
- 一旦模型名包含了某个分组的任何一个关键词，该模型就会被立即分配到这个分组，并停止继续匹配。
- 例如，`glm-4.5` 会匹配到 `zhipu` 组的关键词 `glm`，因此它就被分到 `zhipu` 组
- 如果一个模型遍历完所有自定义分组后，依然没有匹配到任何关键词，它就会被放入一个名为 `default` 的默认分组里

---

如果你的模型名称很混乱，建议在 NewAPI 中的重定向修改模型名称。
