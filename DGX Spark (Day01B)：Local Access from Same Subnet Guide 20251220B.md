# DGX Spark (Day01B)：Local Access from Same Subnet Guide 20251220B
## 🟩 English
> ## Scenarios & Pros/Cons
> **From a local network on Mac/PC → SSH login to DGX Spark at the same subnet**
> - Simple one-line **SSH** command **login to DGX Spark**
>   - Use DGX Spark as Server. (Mac/PC = Client)
> - **Same Subnet LAN**
>   - Refers to the situation where the Mac/PC (Client) and DGX Spark (Server) must be located under the same internal network IP segment (192.168.x.x) assigned by the same router. 
>   - This severely limits the physical distance between Client and Server.
>     - If this cannot meet your needs, please skip this: (Day01B) Local Access from Same Subnet Guide.
>       - You should read instead: [(Day01A) Remote Access from Internet Guide](https://github.com/Sniper711/DGX-Spark-Day01A-Remote-Access-from-Internet-Guide-20251220A/blob/main/DGX%20Spark%20(Day01A)%20Remote%20Access%20Guide%2020251220A.md), which breaks the physical distance limitation.
 
> - 超簡單上手的 SSH
>   - 用一行 SSH 指令連線
>   - 以 DGX Spark 為 Server, 以 Mac/PC 為 Client.
>     
> - 同子網內網指的是
>   - Mac/PC (Client) 與 DGX Spark (Server) 必須位於相同一台 router 所分配的內網IP (192.168.x.x) 區段之下
>   - 嚴重限制了 Client/Server 的物理距離
> - **重要**
>   - 若這不能滿足你的需要，請忽略這篇 (第01天B) 同子網內網操控 指南
>   - 你應該讀的是 (第01天A) 外網遠端操控 指南，打破物理距離限制

---

## 1. 先確定網路拓樸 
Mac/PC (Client) 與 DGX Spark (Server) 必須位於相同一台 router 所分配的內網IP (192.168.x.x) 區段之下

---

## 2. 在 Server (DGX Spark) 查詢其 同子網內網IP位址
方法一
```
jostname -I
```
找到有個(192.168.x.x)開頭的地址，就是 DGX Spark 的 同子網內網IP位址，記錄起來。

方法二
```
ifconfig
```
找到 inet addr: 或 inet 文字後面有個(192.168.x.x)開頭的地址，就是 DGX Spark 的 同子網內網IP位址，記錄起來。

---

## 3. 在 Client (Mac/PC) 用一行 SSH 指令，建立與 Server (DGX Spark) 的連線
正確結果應該是能成功，若已成功連線，會要求輸入 DGX Spark 開機登入密碼
```
# 把 <DGX Spark username> 包含括弧刪掉, 置換成 DGX Spark 開機後登入的 username
# 把 <192.168.x.x> 包含括弧刪掉, 置換成 DGX Spark 的 同子網內網IP位址
ssh <DGX Spark username>@<192.168.x.x>
```

---

# **恭喜你！從此你能從「同子網內網」連上你心愛的 DGX Spark 了！**

---

## 4 連線成功後，能下指令監控 Server (DGX Spark) 的狀態
方法一，從 Client (Mac/PC) 下指令，每秒監控一次 Server (DGX Spark) 的 GPU 溫度 (GPU Temp欄位) 、GPU使用率 (GPU-Util欄位)
```
watch -n 1 nvidia-smi
```

方法二，從 Client (Mac/PC) 下指令，每秒監控一次 Server (DGX Spark) 系統記憶體的 總量 (total欄位)、當前使用量 (used欄位)

```
watch -n 1 free -h
```
