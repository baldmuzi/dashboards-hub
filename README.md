# Dashboards Hub

多维度数据可视化看板集合 —— 静态站点，零构建，直接部署到 GitHub Pages。

## 在线访问

部署后访问：`https://<your-username>.github.io/<repo-name>/`

## 项目结构

```
dashboards-hub/
├── index.html              # 首页：分类浏览 + 搜索
├── data.json               # 看板元数据（新增看板只需更新此文件）
├── .nojekyll               # 让 GitHub Pages 原样发布（不经 Jekyll）
├── README.md
└── dashboards/
    └── tax/                # 类别：税收
        ├── chengdu/index.html
        └── shenzhen/index.html
```

## 现有看板

| 类别 | 看板 | 数据来源 |
|---|---|---|
| 税收 | 成都中产阶级税负 | 成都市统计局、四川省政府 |
| 税收 | 深圳劳动者税负（非私营 vs 私营） | 深圳市统计局、深圳社保局、深圳公积金中心 |

## 添加新看板

1. 在 `dashboards/<category>/<slug>/` 下放置 `index.html`
2. 在 `data.json` 的 `dashboards` 数组追加一项：
   ```json
   {
     "id": "<unique-id>",
     "category": "<category-id>",
     "title": "看板标题",
     "subtitle": "一句话简介",
     "tags": ["标签1", "标签2"],
     "path": "dashboards/<category>/<slug>/index.html",
     "updated": "YYYY-MM-DD",
     "source": "数据来源"
   }
   ```
3. 如需新类别，在 `data.json` 的 `categories` 数组追加。

## 部署

仓库 Settings → Pages → Source: `Deploy from a branch` → Branch: `main` / `/ (root)` → Save。
约 1 分钟后看板即可访问。

## 数据原则

- **所有数据来自官方/权威公开源**（统计局、税务局、社保局等），文件内附原链接
- **不编造数据**：所有数字均可溯源
- 测算口径与假设在每个看板内显式声明
