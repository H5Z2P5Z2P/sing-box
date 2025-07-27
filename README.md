# 介绍

最好用的 sing-box 一键安装脚本 & 管理脚本

## 🔥 增强版特性

本版本在原始脚本基础上新增了 **VLESS-REALITY 前置转发功能**，提供 SNI 嗅探和端口保护。

# 特点

- 快速安装
- 无敌好用
- 零学习成本
- 自动化 TLS
- 简化所有流程
- 兼容 sing-box 命令
- 强大的快捷参数
- 支持所有常用协议
- 一键添加 VLESS-REALITY (默认) **🆕 支持前置转发**
- 一键添加 TUIC
- 一键添加 Trojan
- 一键添加 Hysteria2
- 一键添加 Shadowsocks 2022
- 一键添加 VMess-(TCP/HTTP/QUIC)
- 一键添加 VMess-(WS/H2/HTTPUpgrade)-TLS
- 一键添加 VLESS-(WS/H2/HTTPUpgrade)-TLS
- 一键添加 Trojan-(WS/H2/HTTPUpgrade)-TLS
- 一键启用 BBR
- 一键更改伪装网站
- 一键更改 (端口/UUID/密码/域名/路径/加密方式/SNI/等...)
- **🆕 VLESS-REALITY 前置转发和 SNI 嗅探保护**
- **🆕 前置转发端口管理和同步更新**
- **🆕 JSON 配置格式化输出**
- 还有更多...

# 设计理念

设计理念为：**高效率，超快速，极易用**

脚本基于作者的自身使用需求，以 **多配置同时运行** 为核心设计

并且专门优化了，添加、更改、查看、删除、这四项常用功能

你只需要一条命令即可完成 添加、更改、查看、删除、等操作

例如，添加一个配置仅需不到 1 秒！瞬间完成添加！其他操作亦是如此！

脚本的参数非常高效率并且超级易用，请掌握参数的使用

# 安装

## 快速安装（增强版）

### 🔥 一键安装（推荐）
```bash
bash <(wget -qO- -o- https://raw.githubusercontent.com/H5Z2P5Z2P/sing-box/main/install.sh)
```

### 方法二：wget方式
```bash
wget -O- https://raw.githubusercontent.com/H5Z2P5Z2P/sing-box/main/install.sh | bash
```

### 方法三：本地安装
```bash
# 克隆增强版仓库
git clone https://github.com/H5Z2P5Z2P/sing-box.git
cd sing-box

# 本地安装
bash install.sh --local-install
```

### ✅ 增强版特性
- **自动下载增强版**：从我们的仓库下载包含前置转发功能的版本
- **完整功能**：包含所有 VLESS-REALITY 前置转发增强功能
- **即装即用**：安装后自动配置前置转发

## 🔥 安装后自动配置

安装脚本会自动：
- ✅ 创建一个 VLESS-REALITY 配置
- ✅ 自动启用前置转发功能  
- ✅ 配置 SNI 嗅探保护
- ✅ 显示客户端连接信息（使用前置转发端口）

## ⚠️ 重要提醒

- **客户端连接**: 使用安装后显示的**前置转发端口**，不是 Reality 节点端口
- **端口说明**: Reality 节点监听 127.0.0.1，前置转发监听 0.0.0.0
- **配置管理**: 修改端口或 SNI 时会自动同步前置转发配置

## 原版文档

原版安装及使用：https://233boy.com/sing-box/sing-box-script/

# 帮助

使用：`sing-box help`

```
sing-box script v1.0 by 233boy
Usage: sing-box [options]... [args]...

基本:
   v, version                                      显示当前版本
   ip                                              返回当前主机的 IP
   pbk                                             同等于 sing-box generate reality-keypair
   get-port                                        返回一个可用的端口
   ss2022                                          返回一个可用于 Shadowsocks 2022 的密码

一般:
   a, add [protocol] [args... | auto]              添加配置
   c, change [name] [option] [args... | auto]      更改配置
   d, del [name]                                   删除配置**
   i, info [name]                                  查看配置
   qr [name]                                       二维码信息
   url [name]                                      URL 信息
   log                                             查看日志
更改:
   full [name] [...]                               更改多个参数
   id [name] [uuid | auto]                         更改 UUID
   host [name] [domain]                            更改域名
   port [name] [port | auto]                       更改端口
   path [name] [path | auto]                       更改路径
   passwd [name] [password | auto]                 更改密码
   key [name] [Private key | atuo] [Public key]    更改密钥
   method [name] [method | auto]                   更改加密方式
   sni [name] [ ip | domain]                       更改 serverName
   new [name] [...]                                更改协议
   web [name] [domain]                             更改伪装网站

进阶:
   dns [...]                                       设置 DNS
   dd, ddel [name...]                              删除多个配置**
   fix [name]                                      修复一个配置
   fix-all                                         修复全部配置
   fix-caddyfile                                   修复 Caddyfile
   fix-config.json                                 修复 config.json
   import                                          导入 sing-box/v2ray 脚本配置

管理:
   un, uninstall                                   卸载
   u, update [core | sh | caddy] [ver]             更新
   U, update.sh                                    更新脚本
   s, status                                       运行状态
   start, stop, restart [caddy]                    启动, 停止, 重启
   t, test                                         测试运行
   reinstall                                       重装脚本

测试:
   debug [name]                                    显示一些 debug 信息, 仅供参考
   gen [...]                                       同等于 add, 但只显示 JSON 内容, 不创建文件, 测试使用
   no-auto-tls [...]                               同等于 add, 但禁止自动配置 TLS, 可用于 *TLS 相关协议
其他:
   bbr                                             启用 BBR, 如果支持
   bin [...]                                       运行 sing-box 命令, 例如: sing-box bin help
   [...] [...]                                     兼容绝大多数的 sing-box 命令, 例如: sing-box generate uuid
   h, help                                         显示此帮助界面

谨慎使用 del, ddel, 此选项会直接删除配置; 无需确认
反馈问题) https://github.com/233boy/sing-box/issues
文档(doc) https://233boy.com/sing-box/sing-box-script/
```

## 🆕 新增功能详解

### VLESS-REALITY 前置转发

#### 功能特点
- **SNI 嗅探保护**: 通过前置转发隐藏真实的 Reality 节点端口
- **自动端口管理**: 使用随机高位端口(32768-65535)作为前置转发端口  
- **智能路由规则**: 基于 SNI 域名进行流量分发
- **配置同步**: 修改 Reality 配置时自动同步前置转发规则

#### 工作原理
```
客户端 → 前置转发端口(随机高位) → Reality节点(127.0.0.1) → 目标服务器
```

#### 使用方法

##### 1. 添加 VLESS-REALITY 配置（自动启用前置转发）
```bash
sing-box add reality
# 或者
sing-box add r
```

##### 2. 管理前置转发
在更改配置菜单中选择 **"更改前置转发"** 选项：
```bash
sing-box change [配置名称]
# 选择：更改前置转发
```

可选操作：
- **启用前置转发**: 为现有 Reality 配置启用前置转发
- **禁用前置转发**: 关闭前置转发功能  
- **更改前置端口**: 重新分配前置转发端口

##### 3. 端口同步更新
修改 Reality 端口时，前置转发配置会自动同步：
```bash
sing-box port [配置名称] [新端口]
```

##### 4. SNI 同步更新  
修改 serverName 时，前置转发规则会自动同步：
```bash
sing-box sni [配置名称] [新域名]
```

#### 安全优势

1. **端口隐藏**: Reality 节点只监听 127.0.0.1，不对外暴露
2. **SNI 过滤**: 只有匹配的 SNI 域名才会转发到 Reality 节点
3. **流量阻断**: 其他流量直接阻断，保护后端节点
4. **端口随机**: 前置转发使用随机端口，难以探测

#### 配置文件结构
```
/etc/sing-box/
├── conf/
│   ├── VLESS-REALITY-{port}.json  # Reality 节点配置
│   └── ...
├── config.json                    # 前置转发配置  
└── bin/
    └── sing-box
```

#### 故障排除

查看前置转发配置：
```bash
cat /etc/sing-box/config.json | jq
```

检查端口状态：
```bash
netstat -tulnp | grep [前置端口]
```

测试连接：
```bash
telnet [服务器IP] [前置端口]
```

### 其他增强功能

#### JSON 格式化
- 所有生成的配置文件自动格式化
- 提高配置文件的可读性和维护性

#### 配置验证  
- 端口更改时自动验证前置转发配置
- 确保配置文件的一致性和有效性

## 📋 版本对比

| 功能 | 原版 | 增强版 |
|------|------|--------|  
| VLESS-REALITY 基础支持 | ✅ | ✅ |
| 前置转发保护 | ❌ | ✅ |
| SNI 嗅探 | ❌ | ✅ |
| 端口同步更新 | ❌ | ✅ |
| 前置转发管理 | ❌ | ✅ |
| JSON 格式化 | ❌ | ✅ |

## 🙏 致谢

本增强版本基于 [233boy/sing-box](https://github.com/233boy/sing-box) 开发，感谢原作者的优秀工作。