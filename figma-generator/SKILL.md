---
name: figma-generator
description: 当用户上传figma链接/截图并要求生成页面或组件代码，或者在根据设计草稿实现静态页面时使用。生成内容技术栈包括React 18、TypeScript、Less、antd。
---

# 根据设计图生成 React 组件

当用户上传figma链接/截图并要求生成页面或组件代码时，按本规范生成 React 组件。

## 技术栈

- React 18
- TypeScript
- Less
- antd

## 功能描述

当用户请求还原设计稿时调用。此技能将执行以下步骤：

1.  **获取figma mcp server调用方式**：通过读取mcp.json，获取mcp server的调用方式
2.  **获取figma样式内容**：通过figma mcp server调用方式，获取figma样式内容
3.  **生成代码**：根据mcp返回的figma样式内容，生成React组件代码，并保存到指定路径。
4.  **报告结果**：向用户报告生成的代码数量、文件路径、操作过程。

## 关键点

- 必须去获取mcp.json
- 必须通过mcp server，用figma的url去获取到对应的样式内容
- 严格遵守mcp返回的内容去进行代码输出。不要在沙盒执行，不要有任何偏差
- 生成的代码必须按照.prettierrc和.stylelintrc.js的规范配置来
- 若设计图未提供或模糊的细节，不能做合理假设。

## 样式要求

- **适配**：适配pc小屏幕采用响应式布局。
- **还原**：还原设计稿中的配色、字体、间距、阴影、布局。
- **组件样式**：优先使用 antd 组件，通过覆盖样式使其符合设计图/截图。
- **样式类型**：必须使用css module

## 交互要求

- 仅实现静态页面，不需要复杂业务逻辑。

## 组件要求

- 规划页面结构，拆出可复用小组件。
- 使用 React Hooks（`useState` / `useEffect` 等按需使用）。
- 代码符合 React 最佳实践，无冗余代码。

## 输出格式

- **分文件输出**，例如：
  - `Index.tsx`（页面入口）
  - `index.module.less`（页面样式）
  - `components/aaa.tsx`、`components/xxx.tsx` 等子组件
- **运行说明**：在回复中给出安装依赖与启动命令（如 `pnpm install`、`pnpm dev`）。
- **输出路径**：将生成的文件放在用户指定的目录下，例如：`src/pages/test/`。若用户未指定，可询问或使用项目内合理的 pages 子路径。
