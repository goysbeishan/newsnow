# NewsNow

![](screenshots/preview-1.png)

![](screenshots/preview-2.png)

English | [简体中文](README.zh-CN.md) | [日本語](README.ja-JP.md)

> [!NOTE]
> This is a demo version currently supporting Chinese only. A full-featured version with better customization and English content support will be released later.

***Elegant reading of real-time and hottest news***

## Features
- Clean and elegant UI design for optimal reading experience
- Real-time updates on trending news
- GitHub OAuth login with data synchronization
- 30-minute default cache duration (logged-in users can force refresh)
- Adaptive scraping interval (minimum 2 minutes) based on source update frequency to optimize resource usage and prevent IP bans

## Deployment

### Basic Deployment
For deployments without login and caching:
1. Fork this repository
2. Import to platforms like Cloudflare Page or Vercel

### Cloudflare Page Configuration
- Build command: `pnpm run build`
- Output directory: `dist/output/public`

### GitHub OAuth Setup
1. [Create a GitHub App](https://github.com/settings/applications/new)
2. No special permissions required
3. Set callback URL to: `https://your-domain.com/api/oauth/github` (replace `your-domain` with your actual domain)
4. Obtain Client ID and Client Secret

### Environment Variables
Refer to `example.env.server`. For local development, rename it to `.env.server` and configure:

```env
# Github Client ID
G_CLIENT_ID=
# Github Client Secret
G_CLIENT_SECRET=
# JWT Secret, usually the same as Client Secret
JWT_SECRET=
# Initialize database, must be set to true on first run, can be turned off afterward
INIT_TABLE=true
# Whether to enable cache
ENABLE_CACHE=true
```

### Database Support
Supported database connectors: https://db0.unjs.io/connectors
**Cloudflare D1 Database** is recommended.
1. Create D1 database in Cloudflare Worker dashboard
2. Configure database_id and database_name in wrangler.toml
3. If wrangler.toml doesn't exist, rename example.wrangler.toml and modify configurations
4. Changes will take effect on next deployment

### Docker Deployment
In project root directory:

```sh
docker compose up
 ```

You can also set Environment Variables in `docker-compose.yml`.

## Development
> [!Note]
> Requires Node.js >= 20

```sh
corepack enable
pnpm i
pnpm dev
 ```

### Adding Data Sources
Refer to `shared/sources` and `server/source`s directories. The project provides complete type definitions and a clean architecture.

## Roadmap
- Add **multi-language support** (English, Chinese, more to come).
- Improve **personalization options** (category-based news, saved preferences).
- Expand **data sources** to cover global news in multiple languages.

***release when ready***
![](https://testmnbbs.oss-cn-zhangjiakou.aliyuncs.com/pic/20250328172146_rec_.gif?x-oss-process=base_webp)

## Contributing
Contributions are welcome! Feel free to submit pull requests or create issues for feature requests and bug reports.

## License

[MIT](./LICENSE) 

# 🙏 感谢
[ourongxing](https://github.com/ourongxing/newsnow/)
本项目由VTEXS的[开源项目免费VPS计划]提供算力支持。
感谢VTEXS对开源社区的支持。https://vtexs.com/

 # 
<center>
<details><summary><strong> [点击展开] 赞赏支持 ~🧧</strong></summary>
*我非常感谢您的赞赏和支持，它们将极大地激励我继续创新，持续产生有价值的工作。*

- **USDT-TRC20:** `TWTxUyay6QJN3K4fs4kvJTT8Zfa2mWTwDD`
- **TRX-TRC20:** `TWTxUyay6QJN3K4fs4kvJTT8Zfa2mWTwDD`

<div align="center"> 
  <img src="https://github.com/user-attachments/assets/e6cdc42a-6374-4722-b833-601738f72196" width="200"></br> 
  TRC10/TRC20扫码支付 
</div> 
</details>
</center>

 #
 免责声明:
 - 1、该项目设计和开发仅供学习、研究和安全测试目的。请于下载后 24 小时内删除, 不得用作任何商业用途, 文字、数据及图片均有所属版权, 如转载须注明来源。
 - 2、使用本程序必循遵守部署服务器所在地区的法律、所在国家和用户所在国家的法律法规。对任何人或团体使用该项目时产生的任何后果由使用者承担。
 - 3、作者不对使用该项目可能引起的任何直接或间接损害负责。作者保留随时更新免责声明的权利，且不另行通知。
