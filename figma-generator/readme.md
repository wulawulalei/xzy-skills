## 一、获取 Figma 个人 API Key（关键）

- 登录 Figma 官网，点击右上角头像→「Settings（设置）」→左侧「Security（安全）」；
- 在「Personal Access Tokens」区域，点击「Generate new token」；
- 输入令牌名称，权限仅勾选 **file_contents:read**（最低必需，避免权限过高）；
- 点击「Generate token」，立即复制令牌并保存（关闭窗口后无法再次查看）。

## 二、配置

1. 在 Trae 的配置目录创建mcp.json：
   -- Windows：C:\Users\[你的用户名]\.trae\mcp.json
   -- Mac/Linux：~/.trae/mcp.json

2. 粘贴以下配置（替换<你的API密钥>，Windows/Mac 配置略有差异）：

```
// Mac/Linux 配置
{
  "mcpServers": {
    "Figma MCP": {
      "command": "npx",
      "args": ["-y", "figma-developer-mcp", "--figma-api-key=<你的API密钥>",  "--stdio"]
    }
  }
}
```

```
// Windows 配置
{
  "mcpServers": {
    "Figma MCP": {
      "command": "cmd",
      "args": ["/c", "npx", "-y", "figma-developer-mcp", "--figma-api-key=<你的API密钥>", "--stdio"]
    }
  }
}
```

3. 保存后，Trae 会自动加载并启动 MCP 服务器，无需手动执行终端命令。

## 三、使用方法

1. 在浏览器打开Figma，选中需要生成代码的部分，右键，选择`Copy link to selection`

2. 粘贴到agent对话框，提示应用对应skill，并填写想要输出的路径，回车即可

## 四、沟通方式

- https://www.figma.com/design/aaa请根据figma-generator这个skill，还原上述figma链接的设计稿，将代码写在pages/ai/index/tsx
