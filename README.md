# 新概念英语第二册 · NCE Book 2

📘 AI 辅助教学的《新概念英语第二册》在线学习项目。

## 🌐 在线地址

https://nce-book2.pages.dev

## 📖 进度

| 课 | 标题 | 语法点 |
|:-:|:----|:-------|
| 1 | A Private Conversation | 简单陈述句语序 |
| 2 | Breakfast or Lunch? | 现在进行时 vs 一般现在时 |
| 3 | Please Send Me a Card | 一般过去时（不规则动词） |
| 4 | An Exciting Trip | 现在完成时 |
| 5 | No Wrong Numbers | 一般过去时 vs 现在完成时对比 |
| 6 | Percy Buttons | 冠词 a/an/the |
| 7 | Too Late | 过去进行时 |

## 🚀 部署

项目已配置 [Cloudflare Pages](https://pages.cloudflare.com/)，推送后自动部署：

```bash
npx wrangler pages deploy . --project-name nce-book2
```

## 📁 项目结构

```
├── index.html              # 首页导航
├── lessons/                # 课程 HTML
├── reference/              # 语法参考文档
├── learning-records/       # 学习记录
├── wrangler.toml           # Cloudflare 配置
└── README.md
```
