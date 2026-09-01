# 金富瑞产品二维码追溯系统

纯静态网站，可直接发布到 GitHub Pages。页面使用 Hash 路由，因此部署在
`https://<用户名>.github.io/<仓库名>/` 子路径下时，刷新子页面不会返回 404。

## 发布方式

1. 在 GitHub 新建一个公开仓库。
2. 将本目录提交并推送到仓库的 `main` 分支。
3. 工作流会自动启用并部署 GitHub Pages。
4. 在仓库的 **Actions** 页面等待 `Deploy GitHub Pages` 完成。

网站地址通常为：

```text
https://<用户名>.github.io/<仓库名>/
```

## 功能范围

- 首页、产品详情、作物种植方案、二维码群聊页面
- 高考助力活动规则和本地预报名表单校验
- 反馈表单的前端演示校验
- 两个可点击的视频播放器
- 手机与桌面响应式布局

视频文件随静态站点发布在 `assets/videos/` 下，本地预览与 GitHub Pages
均从网页同域读取，避免移动端扫码浏览器因 Release 跨域跳转而加载失败。

反馈和预报名没有连接官方后端，不会向官方服务器提交数据。

## 本地二维码生成

金富瑞项目的本地批次二维码生成器位于 `qr-generator` 文件夹。使用方法见项目根目录的
`二维码生成使用说明.md`。生成器默认使用 `https://yang1832-gg.github.io/JFR-product-trace/`，
并按现有网站记录自动去重。生成器和批次输出仅保存在本机，不会提交到公开仓库。

## 静态二维码记录

计划使用的中性 GitHub Pages 地址为：

```text
https://yang1832-gg.github.io/JFR-product-trace/
```

二维码链接使用 `?id=<24位随机查询ID>#home`，页面只读取查询 ID 对应的一个
JSON 分片。当前数据包含 9999 条记录、256 个分片，总大小约 1.07 MB。

生成器位于 `tools/generate_static_records.py`，依赖见
`tools/requirements.txt`。生成的二维码 ZIP 和编码对应表用于印刷与管理，
不需要上传到 GitHub Pages。
