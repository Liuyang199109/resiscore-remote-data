# 远程数据包

把本目录下的 `manifest.json` 和 `v1/` 一起上传到同一个 HTTPS 静态数据域名。例如：

```text
https://static.example.com/resiscore-mini/manifest.json
https://static.example.com/resiscore-mini/v1/guangzhou/quality/index.json
https://static.example.com/resiscore-mini/v1/guangzhou/transport/guangzhou.json
```

`manifest.json` 使用相对于数据域名的路径。小程序会把 `config.js` 的 `dataBaseUrl` 与这些路径拼接；网页版部署时也可以使用同样的目录结构。

建议的服务器设置：

- `manifest.json` 使用不缓存或短缓存；
- `v1/` 下的版本化数据文件使用长缓存；
- JSON 返回 `Content-Type: application/json`；
- 开启 gzip 或 Brotli 传输压缩；
- 上传新数据文件后，最后再替换 manifest；
- 保留旧版本数据，方便用户更新失败时继续使用旧缓存。

质量和证据数据已经按广州行政区拆分，搜索索引单独生成。原始 PDF、DOCX、XLSX、抓取 HTML、临时缓存和网页 bundle 不属于远程运行包。
