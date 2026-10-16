# LibreTV · Cloudflare Workers 单文件版

一个**自包含的 `worker.js`**：无需安装任何东西、无需构建、无需上传静态资源。
复制 `worker.js` 里的全部代码，粘贴到 Cloudflare Worker 在线编辑器即可运行。

> English guide: [README.en.md](README.en.md)

> 本项目基于 [LibreTV](https://github.com/LibreSpark/LibreTV)（Next.js 重构版，**AGPL-3.0**），
> 原作者 LibreSpark。本仓库只是将其打包为“单文件可粘贴”形态，协议仍为 AGPL-3.0。

## 体积

- `worker.js` 原始约 8.7 MB，**gzip 约 2.24 MB**
- 低于 Cloudflare **免费计划 Worker 的 3 MB（gzip）上限**，免费账号即可部署
- 已把 61 个静态资源（JS/CSS/图标等）内联进 worker，因此不依赖任何外部文件

## 部署步骤（约 1 分钟，全程网页操作）

1. 登录 Cloudflare 控制台 → **Workers 和 Pages** → **创建** → **创建 Worker**
2. 给它起个名字（如 `libretv`）→ 点 **部署**
3. 部署后点 **编辑代码（Edit code）**
4. 全选删除编辑器里的默认代码，把本仓库 **`worker.js` 的全部内容粘贴进去**
5. 点右上角 **部署（Deploy）**
6. 打开分配的 `xxx.workers.dev` 地址，即可看到 LibreTV 搜索页

> 想绑定自己的域名：Workers → 该 Worker → **设置 → 域和路由 → 添加 → 自定义域**，选你账号里的域名即可。

## 可选：环境变量（在“设置 → 变量和密钥”里添加）

| 变量 | 类型 | 说明 |
|---|---|---|
| `PASSWORD` | **密钥(Secret)** | 访问密码；不设置则站点无需密码即可访问 |
| `DEFAULT_SOURCES` | **文本(Text)** | 预置点播源，配置后新访客打开即自动加载、无需手动添加 |
| `60S_API_BASE` | 文本 | 首页榜单推荐源（不设置则显示“推荐内容加载失败”，不影响搜索） |
| `REQUEST_TIMEOUT` | 文本 | 上游请求超时(ms)，默认 8000 |

`DEFAULT_SOURCES` 为 JSON 数组，**下面只是格式示例，地址为占位、无法直接使用**：

```json
[
  {"name":"示例源","url":"https://demo.example.com/api.php/provide/vod/from/demo","isAdult":false}
]
```

> 请自行寻找合法可用的采集接口填入。本项目不提供任何影视资源与采集源。

## 免责声明

- 本项目仅为前端聚合技术学习工具，**不内置、不提供任何影视内容**。
- 使用者自行配置的第三方接口，其内容版权、可用性与合规性由使用者自行承担。
- 请勿用于商业用途，仅供个人学习研究。

## 协议

AGPL-3.0（见上游 LibreTV）。
