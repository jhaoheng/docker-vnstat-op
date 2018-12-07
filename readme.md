> 無法再 osx 上使用 ... 因 osx 無法使用 `network_mode: host`

# vnstat 功能
- 即使系統重啓後，統計數字依然可用
- 可以同時監控多個網絡接口
- 多個輸出選項
- 可以按小時、天、月或周來排序數據，也可以獲得流量最大的 10 天的信息
- 生成輸出的 PNG 圖形
- 設置「月份」，以跟進你可能擁有的不同的計費週期
- 非常輕巧――確實只耗用一小部分的系統資源
- 不管生成的流量有多大，都佔用很少的處理器資源
- 沒必要是 root 用戶即可使用它
- 可以動態選擇單位 (KB 和 MB 等)
- 可以將圖例添加到生成的輸出圖像
- 為 vnStat.cgi 的內容定位和圖像背景提供了可以定制的選項
- 接口帶寬會自動被檢測出來

# 說明
> 環境 ubuntu 16.04 , 14.04 均適用

1. 關於 vnStat (監控網絡流量或帶寬使用率)
    - 指定版本為 1.14.
    - 如何使用 : https://www.howtoforge.com/tutorial/vnstat-network-monitoring-ubuntu/
2. 關於 vnStati (依據 vnstat 創建圖形輸出並將其存儲在指定位置.) `未使用`
3. 關於 dashboard
    - `vnstat-dashboard` 資料夾
    - 透過 http://{ip}/vnstat 觀看目前流量統計
    - 解析指定版本 vnstat-1.14

# 安裝
1. `ln -s .....{path}/vnstat-1.14 /usr/bin/vnstat`
2. `vnstat --version`, 確認版本 1.14
3. `service vnstat start`
4. 開啟 web dashboard, `docker-compose up -d`. Browser : `http://{ip}/vnstat/`
    - 預先 docker-compsoe.yml 確認 `/var/lib/vnstat` 與 `/usr/bin/vnstat` 位置正確

## vnstat 指令基本操作(若使用 dashboard 則無須使用)

1. 預設設定檔 : `/etc/vnstat.conf`
2. `vnstat --longhelp`
3. `vnstat --iflist` : 目前可觀察的網路介面, 使用 `-i` 可指定特定的 interface
4. 統計
    - Hourly statistics     : `vnstat -h`
    - Monthly statistics    : `vnstat -m` 
    - Weekly statistics     : `vnstat -w`
    - Top 10 stats          : `vnstat -t`
    - live monitoring       : `vnstat -l`
5. output style
    - 0 = minimal & narrow
    - 1 = bar column visible
    - 2 = same as 1 except rate in summary and weekly
    - 3 = rate column visible `(default)`