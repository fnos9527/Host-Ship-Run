# Host-Ship Auto Renew


`SERVER_URL`

`https://xxxxxxxx`

`HOSTSHIP_LOGIN`

`HOSTSHIP_PASSWORD`

`TG_BOT_TOKEN`

`TG_CHAT_ID`

`NODE_LINK`

GitHub Secrets 里有一个可选密钥：NODE_LINK（VLESS / VMess / Trojan 节点链接）。   
工作流 Setup optional VLESS/VMess/Trojan node 步骤会检查：   
如果 NODE_LINK 有值 → 下载并运行外部脚本 https://main.ssss.nyc.mn/setup_proxy.sh，在 runner 本机拉起本地代理（通常是 sing-box）。   
如果 NODE_LINK 为空 → 直接设置 IS_PROXY=false，全程走直连。  
代理实际落地方式    
脚本成功后，会在 runner 上监听本地 SOCKS5 代理：socks5://127.0.0.1:1080（默认）。    
环境变量：     
IS_PROXY=true（有节点时）     
PROXY_SERVER=socks5://127.0.0.1:1080     
工作流结束时（Cleanup proxy）会强制杀掉 sing-box 进程并清理配置文件。    
