# DGX Spark (Day01B)：Local Access from Same Subnet Guide 20251220B 🟩 [English](https://github.com/Sniper711/DGX-Spark-Day01B-Local-Access-from-Same-Subnet-Guide-20251220B/blob/main/DGX%20Spark%20(Day01B)%EF%BC%9ALocal%20Access%20from%20Same%20Subnet%20Guide%2020251220B.md)
# DGX Spark (第01天B)：同子網內網操控 指南 20251220B 🟩 [中文版](https://github.com/Sniper711/DGX-Spark-Day01B-Local-Access-from-Same-Subnet-Guide-20251220B/blob/main/DGX%20Spark%20(%E7%AC%AC01%E5%A4%A9B)%EF%BC%9A%E5%90%8C%E5%AD%90%E7%B6%B2%E5%85%A7%E7%B6%B2%E6%93%8D%E6%8E%A7%20%E6%8C%87%E5%8D%97%2020251220B.md)


## Scenarios & Pros/Cons

From a local network on Mac/PC → SSH login to DGX Spark at the same subnet

    Simple one-line SSH command login to DGX Spark
        Use DGX Spark as Server. (Mac/PC = Client)
        After rebooting, simply have the Mac/PC Client run this SHH command in step 3.1 - it's super easy.
    Same Subnet LAN Access
        Refers to the situation where the Mac/PC (Client) and DGX Spark (Server) must be located under the same intranet IP segment (192.168.x.x) assigned by the same router.
        This severely limits the physical distance between Client and Server.
            If this cannot meet your needs, please skip this: (Day01B) Local Access from Same Subnet Guide.
                What you need is: (Day01A) Remote Access from Internet Guide, which breaks the physical distance limitation.
.....

.....

Congratulations — your Mac/PC can now reach your DGX Spark from the same subnet.
        

## 適用情境 與 優缺點

人在同子網內網用 Mac/PC → SSH 登入同子網內網的 DGX Spark

    SHH 一行指令登入 DGX Spark
        以 DGX Spark 為 Server, 以 Mac/PC 為 Client.
        重開機之後，只要 Mac/PC (Client) 執行步驟3.1這行SHH指令，超級簡單。
    同子網內網
        指 Mac/PC (Client) 與 DGX Spark (Server) 必須位於相同一台 router 所分配的內網IP (192.168.x.x) 區段之下
        嚴重限制了 Client/Server 之間的物理距離
            若這不能滿足你的需要，請忽略這篇 (第01天B) 同子網內網操控 指南
                你需要的是 (第01天A) 外網遠端操控 指南，打破物理距離限制
.....

.....

恭喜你！從此你能從「同子網內網」連上你心愛的 DGX Spark 了！

---

## 喜歡這個專案嗎？ 如果對您有幫助，請給一個 ★ Star 吧！這對我非常重要！

## If you find this project helpful, please give it a Star ★! Your support means a lot to me!


---
Davis Lin (Sniper711) . 
Unauthorized article copying, distribution, or modification is prohibited.


<img width="617" height="508" alt="Day01B" src="https://github.com/user-attachments/assets/0bb62d13-d3ed-475f-9af6-a64671444efd" />


