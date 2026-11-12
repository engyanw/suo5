# Node.js

环境依赖：Node.js 18+

| 运行环境                    | 自动检测 | 全双工 | 半双工 | 短链接 |
|:------------------------|:----:|:---:|:---:|:---:|
| Node.js Standalone (18/22) |  ✓   |  ✓  |  ✓  |  ✓  |

## 独立运行

`suo5.js` 不依赖第三方 npm 模块，以 **HTTPS** 方式启动，直接运行即可：

```bash
node suo5.js
```

默认监听 `8080` 端口。启动时若未提供 TLS 证书，会自动调用 `openssl` 生成一张临时自签名证书（仅用于测试）。也可通过环境变量指定已有证书与端口：

| 环境变量 | 说明 |
|:--|:--|
| `SUO5_TLS_CERT`       | PEM 证书文件路径（与 `SUO5_TLS_KEY` 同时指定） |
| `SUO5_TLS_KEY`        | PEM 私钥文件路径（与 `SUO5_TLS_CERT` 同时指定） |
| `SUO5_TLS_PASSPHRASE` | 私钥口令（可选） |
| `SUO5_PORT`           | 监听端口，默认 `8080` |

Suo5 客户端使用 `https://` 连接。客户端默认跳过 TLS 证书校验，因此自签名证书可直接使用：

```bash
./suo5 -t https://target:8080/
```

## Next.js 内存马

`next_payload.http` 是针对 CVE-2025-55182/CVE-2025-66478 生成的请求。根据目标修改请求中的
`Host` 和请求路径后发送，执行成功后会在目标现有的 Node.js HTTP Server 中挂载 `/test` 路由。

Suo5 客户端连接地址为：

```bash
./suo5 -t http://target:3000/test
```
# Node.js

环境依赖：Node.js 18+

| 运行环境                    | 自动检测 | 全双工 | 半双工 | 短链接 |
|:------------------------|:----:|:---:|:---:|:---:|
| Node.js Standalone (18/22) |  ✓   |  ✓  |  ✓  |  ✓  |

## 独立运行

`suo5.js` 不依赖第三方 npm 模块，直接运行即可：

```bash
node suo5.js
```

默认监听 `8080` 端口，Suo5 客户端连接地址为：

```bash
./suo5 -t http://target:8080/
```

## Next.js 内存马

`next_payload.http` 是针对 CVE-2025-55182/CVE-2025-66478 生成的请求。根据目标修改请求中的
`Host` 和请求路径后发送，执行成功后会在目标现有的 Node.js HTTP Server 中挂载 `/test` 路由。

Suo5 客户端连接地址为：

```bash
./suo5 -t http://target:3000/test
```
