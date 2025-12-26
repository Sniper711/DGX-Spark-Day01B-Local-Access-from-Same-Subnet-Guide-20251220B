# DGX Spark (Day01B)：Local Access from Same Subnet Guide 20251220B
## 🟩 English
> ## Scenarios & Pros/Cons
> **From a local network on Mac/PC → SSH login to DGX Spark at the same subnet**
> - Simple one-line **SSH** command **login to DGX Spark**
>   - Use DGX Spark as Server. (Mac/PC = Client)
> - **Same Subnet LAN Access**
>   - Refers to the situation where the Mac/PC (Client) and DGX Spark (Server) must be located under the same internal network IP segment (192.168.x.x) assigned by the same router. 
>   - This severely limits the physical distance between Client and Server.
>     - If this cannot meet your needs, please skip this: (Day01B) Local Access from Same Subnet Guide.
>       - What you need is: [(Day01A) Remote Access from Internet Guide](https://github.com/Sniper711/DGX-Spark-Day01A-Remote-Access-from-Internet-Guide-20251220A/blob/main/DGX%20Spark%20(Day01A)%20Remote%20Access%20Guide%2020251220A.md), which breaks the physical distance limitation.

---

## 1. Confirm the Network Topology 

Mac/PC (Client) and DGX Spark (Server) **must be located under the same internal network IP segment (192.168.x.x) assigned by the same router**.

This severely limits the physical distance between Client and Server.

---

## 2. On the DGX Spark server, query its internal IP address on the same subnet
Method 1
```
jostname -I
```
Find the DGX Spark's IP address that starts with (192.168.x.x), and make a note of it.

Method 2
```
ifconfig
```
Find the text `inet addr:` or `inet`, followed by an address that starts with (192.168.x.x)—this is the DGX Spark's internal IP address on the same subnet—and make a note of it.

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
