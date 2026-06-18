# Twikoo 评论系统

Twikoo 是一个简洁、安全、免费的静态网站评论系统，基于腾讯云 CloudBase 开发。

## ✨ 特性

- **免费部署** — 基于腾讯云 CloudBase，无需服务器
- **隐私安全** — 支持私有化部署，用户数据由自己掌控
- **轻量简洁** — 仅需几行代码即可完成前端集成
- **反垃圾评论** — 内置 Akismet 反垃圾评论支持
- **邮件通知** — 支持新评论邮件提醒
- **管理面板** — 内嵌管理面板，支持密码登录管理
- **支持多种框架** — 支持 Hexo、Hugo、Valine、Waline 等多种博客/文档框架
- **表情包支持** — 支持自定义表情包和 OwO 表情

## 📦 快速开始

### 1. 部署后端（腾讯云 CloudBase）

1. 打开 [腾讯云 CloudBase 控制台](https://console.cloud.tencent.com/tcb)
2. 新建一个环境，选择**按量计费**
3. 进入「环境设置」→「安全配置」，获取环境 ID
4. 在环境内进入「云函数」，创建名为 `twikoo` 的云函数
5. 将 [twikoo 云函数代码](https://github.com/twikoojs/twikoo/releases) 上传部署

> 详细教程：[Twikoo 官方文档](https://twikoo.js.org/)

### 2. 前端集成

在你的网站 HTML 中添加以下代码：

```html
<div id="tcomment"></div>
<script src="https://cdn.jsdelivr.net/npm/twikoo@latest/dist/twikoo.all.min.js"></script>
<script>
twikoo.init({
  envId: '你的CloudBase环境ID',
  el: '#tcomment',
  // region: 'ap-guangzhou', // 环境地域，默认为 ap-shanghai
  // path: window.location.pathname, // 用于区分不同文章的自定义路径
  // lang: 'zh-CN', // 语言，支持 zh-CN / en
});
</script>
```

### Hexo 集成

```bash
npm install hexo-next-twikoo
```

在 Hexo 配置文件中添加：

```yaml
twikoo:
  enable: true
  envId: 你的CloudBase环境ID
  region: ap-shanghai
```

### Hugo 集成

在主题配置中添加对应的 Twikoo 配置项，或直接在模板中引入上述前端代码。

## 🔧 配置说明

### 基本配置

| 参数 | 类型 | 默认值 | 说明 |
|------|------|--------|------|
| `envId` | String | - | CloudBase 环境 ID（必填） |
| `el` | String | - | 评论容器元素选择器（必填） |
| `region` | String | `ap-shanghai` | 环境地域 |
| `path` | String | `window.location.pathname` | 文章路径标识 |
| `lang` | String | `zh-CN` | 语言设置 |

### 反垃圾评论配置

在 CloudBase 环境中配置 Akismet：

- `AKISMET_KEY` — Akismet API Key（可选）
- `MAIL_SUBSCRIBE` — 邮件订阅开关
- `MAIL_TEMPLATE` — 邮件模板路径

### 管理面板

访问 `https://<你的环境ID>.service.tcloudbase.com/` 进入管理面板：

- 首次访问需设置管理员密码
- 支持评论审核、删除、置顶等操作
- 可配置通知邮件模板

## 📂 项目结构

```
twikoo/
├── cloudfunction/       # 云函数后端代码
│   ├── index.js         # 主入口
│   └── package.json     # 依赖配置
├── dist/                # 前端构建产物
├── docs/                # 文档
└── README.md            # 项目说明
```

## 🌐 相关链接

- [GitHub 仓库](https://github.com/twikoojs/twikoo)
- [官方文档](https://twikoo.js.org/)
- [更新日志](https://github.com/twikoojs/twikoo/releases)
- [问题反馈](https://github.com/twikoojs/twikoo/issues)

## 📄 许可证

[MIT License](https://github.com/twikoojs/twikoo/blob/main/LICENSE)
