🔐 Pure Client-Side SSL Certificate Generator



一个基于浏览器原生 Web Crypto API 的 ACME 客户端，无需任何后端服务器，直接在浏览器中申请免费的 SSL 证书（Let's Encrypt, ZeroSSL, Google Trust Services）。

✨ 核心特性 (Features)

🌐 零后端 (Serverless)：完全运行在浏览器端，不需要搭建任何服务器或代理，只需一个 HTML 文件。

🛡️ 绝对隐私安全：私钥（Private Key）通过浏览器 Web Crypto API 在本地生成，永远不会离开您的设备或通过网络传输。

🚀 多机构支持：支持 Let's Encrypt (V2)、ZeroSSL、Google Trust Services。

🔧 强大的兼容性：

支持 泛域名 (Wildcard) 证书 (如 *.example.com)。

支持 多域名 (SAN) 申请 (一张证书包含多个域名)。

支持 RSA-2048 和 ECC (P-256) 双算法。

💉 独创注入模式：内置“代码注入引导”，无需安装浏览器扩展即可绕过 ACME 接口的 CORS (跨域) 限制。

📦 格式全覆盖：不仅支持 Nginx/Apache 常用的 .pem 格式，还支持一键导出 Windows/IIS 需要的 .pfx (PKCS#12) 格式。

🌍 国际化：内置 中文 / English 双语切换。

🚀 快速开始 (Quick Start)

方法一：直接运行 (推荐开发调试)

下载本仓库中的 index.html (原名 ssl_tool_final.html)。

直接在浏览器中打开。

注意：由于浏览器的同源策略 (CORS)，直接打开可能会导致无法连接 CA 服务器。推荐使用 方法二。

方法二：控制台注入法 (生产环境推荐)

这是本工具最核心的“黑科技”，可以完美绕过 CORS 限制：

在本地打开 HTML 文件。

点击右上角的 "🔧 无法连接？点击这里" 按钮。

点击 "复制全部代码"。

在浏览器新标签页打开目标 CA 的 API 地址（例如 Let's Encrypt 接口）。

按 F12 打开开发者工具，切换到 Console (控制台)。

注意：如果是 Chrome，首次粘贴可能会提示警告，请按提示输入 allow pasting 解锁。

粘贴代码并回车。

神奇的事情发生了：工具将直接在当前页面运行，且拥有合法的网络请求权限！

📝 申请流程 (Workflow)

账户准备：

选择 CA 机构（Let's Encrypt / ZeroSSL / Google）。

输入邮箱（用于接收过期通知）。

(可选) 如果是 ZeroSSL/Google，填写 EAB 凭证 (KID & HMAC)。

创建订单：

输入域名（支持 example.com, *.example.com）。

选择密钥算法（推荐 ECC，兼容性好选 RSA）。

DNS 验证：

工具会生成 TXT 记录值。

前往您的 DNS 服务商（阿里云/腾讯云/Cloudflare 等）添加对应的 _acme-challenge 记录。

使用工具自带的 "🔍 检查" 按钮确认生效。

签发下载：

点击验证，工具会自动轮询订单状态。

签发成功后，直接下载 cert.pem 和 private.key。

🛠️ 技术栈 (Tech Stack)

UI: Tailwind CSS (CDN)

Crypto:

Native window.crypto.subtle (性能核心)

jsrsasign (处理 JWS/EAB/ECC)

node-forge (处理 RSA CSR 兼容性 & PFX 导出)

Protocol: ACME v2 (RFC 8555)

⚠️ 安全声明 (Security Disclaimer)

本工具是纯静态网页，没有后台服务器。

私钥安全：所有私钥生成操作均在您浏览器的内存中完成。一旦您关闭页面或刷新，私钥将从内存中消失（除非您已经下载了它）。

开源透明：所有代码逻辑都在这一个 HTML 文件中，您可以随时审查代码，确保没有恶意上传行为。

📄 License

MIT License © 2025

如果您觉得这个工具有用，请给个 Star ⭐️ 支持一下！
