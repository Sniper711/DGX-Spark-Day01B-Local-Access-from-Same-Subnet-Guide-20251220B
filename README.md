# DGX Spark (Day01B)：Local Access from Same Subnet Guide 20251220B 🟩 [English](https://github.com/Sniper711/DGX-Spark-Day01B-Local-Access-from-Same-Subnet-Guide-20251220B/blob/main/DGX%20Spark%20(Day01B)%EF%BC%9ALocal%20Access%20from%20Same%20Subnet%20Guide%2020251220B.md)
# DGX Spark (第01天B)：同子網內網操控 指南 20251220B 🟩 [中文版](https://github.com/Sniper711/DGX-Spark-Day01B-Local-Access-from-Same-Subnet-Guide-20251220B/blob/main/DGX%20Spark%20(%E7%AC%AC01%E5%A4%A9B)%EF%BC%9A%E5%90%8C%E5%AD%90%E7%B6%B2%E5%85%A7%E7%B6%B2%E6%93%8D%E6%8E%A7%20%E6%8C%87%E5%8D%97%2020251220B.md)


## Scenarios & Pros/Cons

From a local network on Mac/PC → SSH login to DGX Spark at the same subnet

    Simple one-line SSH command login to DGX Spark
        Use DGX Spark as Server. (Mac/PC = Client)
    Same Subnet LAN Access
        Refers to the situation where the Mac/PC (Client) and DGX Spark (Server) must be located under the same intranet IP segment (192.168.x.x) assigned by the same router.
        This severely limits the physical distance between Client and Server.
            If this cannot meet your needs, please skip this: (Day01B) Local Access from Same Subnet Guide.
                What you need is: (Day01A) Remote Access from Internet Guide, which breaks the physical distance limitation.
.....

.....

Congratulations — your Mac/PC can now reach your DGX Spark from anywhere.
        

## 適用情境 與 優缺點

人在外網用 Mac/PC → 透過 WireGuard VPN → SSH 登入家中 DGX Spark

    全面改用 WireGuard VPN
        以 DGX Spark 為 VPN Server. (Mac/PC = Client)
        VPN 穿透率極高，行動網路開熱點上網幾乎不被行動網路阻擋.
        WireGuard 設定 UDP 51820 Port 搭配 keepalive 是正解.
        90% 在台灣行動網路，WireGuard 能過，OpenVPN 過不了.
    不用 Tunnelblick 與 OpenVPN，不用昂貴 Router 的內建 VPN Server
        行動網路開熱點連VPN失敗主因之一：電信商刻意阻擋行動網路的 UDP/TCP 1194 Ports VPN 流量.
            改用 TCP 443 Port 能增強 VPN 穿透率，相對穩定但速度慢，在行動網路可能有TCP-over-TCP隊頭阻塞(HOL Blocking)導致熔斷(Meltdown)問題.
            某些昂貴的 Router 無法改 TCP Port# 也是問題 (僅有 TCP 1194 Port).
        行動網路開熱點連VPN失敗主因之二：行動網路NAT導致UDP丟包.
            Tunnelblick 與 OpenVPN 雖然使用UDP，但內部實作卻類似TCP與SSL/TLS，步驟多，在行動網路容易中途斷掉.
        有鑑於此，不用 Tunnelblick 與 OpenVPN
    用低階的 Router
        Router：需有 固定 Public IP (x.x.x.x), 需支援 Port Forward.
        因為不使用 Tunnerblick 與 OpenVPN，所以 Router 並不需要 VPN 高階功能 (有則關閉之)，只需便宜的 Router.
    SSH 一行指令登入 DGX Spark
.....

.....

恭喜你！從此你能從任何地方連回你心愛的 DGX Spark 了！

---

## 喜歡這個專案嗎？ 如果對您有幫助，請給一個 ★ Star 吧！這對我非常重要！

## If you find this project helpful, please give it a Star ★! Your support means a lot to me!


---
Davis Lin (Sniper711) . 
Unauthorized article copying, distribution, or modification is prohibited.

