# NAS User Guide

## 說明

本文件旨在提供資工系系學會管理的 NAS [使用規範](#使用規範) 與 [存取方式](#存取方式)。若您發現文件中有缺漏或錯誤，麻煩您透過 [Pull Request](https://github.com/ncu-csie-student-association/nas-user-guide/pulls) 協助我們更正。

NAS 內另有詳細的 <u>使用說明</u> 請登入後仔細閱讀 README 文件

## 來由

中央資工從過去累積了大量的照片、活動紀錄，以及學長姐的學習筆記，起初這些資料都放在 Google 的共用雲端硬碟中，當時仍享有 Google 給予學校無限大的資料存儲容量。然而在 2024 年，Google 取消了這項福利，若要採用過去的方案，每個月需支付 20 美金 [^google-workspace-price]，累積起來是一筆龐大的金額。有鑑於此，系學會決定管理自己的 NAS 存放這些資料，並以更方便的方式共用給系上的同學。

我們的 NAS 使用 Synology 的產品，之所以不使用 TrueNAS 這樣成本更低的解決方案是基於傳承、穩定性、資料安全性為考量。我們希望這樣的解決方案是可以持續，且讓大家可放心的。在成本與其他風險間的取捨下，最後是採用了市面上相當成熟的產品作為資料存儲與共享設備。

[^google-workspace-price]: 為撰寫當下 2024 年 10 月 16 日之資料。

## 使用規範

1. 資工系系學會 NAS 存有「先人的照片」與「先人的智慧」，前者為系上各種活動的照片、紀錄；後者為學長姐們的*學習筆記*，請同學們切記 <ins>**不要高調宣傳**</ins>。

2. 系學會提供的儲存空間禁止存放任何非法內容，所有上傳與變更皆有記錄，其法律責任由上傳者個人承擔。

3. NAS 採實名認證，若要存取 NAS 的資料，您必須同意使用規範，並透過 [GitHub Issue](https://github.com/ncu-csie-student-association/nas-user-guide/issues/new/choose) 進行申請，申請內容模版與範例如下：

   ```yaml
   系級: 資工四B
   學號: 110502000
   姓名: 游帥哥
   Email: squid@squidspirit.com

   我同意遵循使用規範，且不上傳任何非法內容。
   ```
> [!Note]
> 申請成功後，帳號 (預設為學號) 與密碼重設連結將以 Email 寄出，實測發現經常被歸類為垃圾郵件，請多加留意。
> （管理員亦無權限查看使用者密碼，建議使用與校務系統相同的密碼或其它常用密碼，避免遺忘。）
>
> 若帳號申請 issue 已被 closed，卻仍未收到帳號註冊郵件，請聯絡我們。
> 
> 日後若需更改密碼，請登入 [NAS 管理頁面](https://140.115.53.250:5001)，並點擊右上角頭像重設密碼。  
>
> 若因嘗試太多次錯誤密碼導致IP被封，24小時後會自動解鎖
>
> 若忘記密碼，需透過 [GitHub Issue](https://github.com/ncu-csie-student-association/nas-user-guide/issues/new/choose) 申請重置密碼，申請成功後，重置過後的密碼將以註冊時的 Email 寄出 (請多加留意垃圾郵件)，請使用新密碼登入後再將密碼改為常用密碼。
>
> 因涉及個人隱私，若不願提供私人信箱，請使用中央大學分配以 cc.ncu.edu.tw 為域名的信箱。

5. 預設權限僅能讀取、新增，但不能刪除，如有編輯或刪除的需求，請透過 NAS 內的共編文件提出申請  
   此請求提供非持續性的檔案編輯或刪除，若您具備權責需要長期管理相關資源（如新聞部），請另外聯繫系代或副系代。

6. 系學會擁有調整使用規範之權力，若有進行重大調整，將通知使用者，而變更之歷史紀錄會保留於 git commit 記錄中。

7. 註冊並使用 NAS 即表示您同意以上使用規範。

## 存取方式

有幾種方法可以存取 NAS 的檔案，一種是透過網頁直接存取、一種是使用 SMB 協議存取、一種是以 Synology Drive 的桌面或行動應用程式，以下將會分別介紹這兩種方法各自的優點與進行方式

### 網頁存取

使用網頁存取具有以下優點：

- 在任意設備進行登入（若為陌生設備請記得使用無痕模式）
- 能取得內部分享連結（需登入帳號才能存取）
- 能設定使用者資訊

以下為使用網頁存取的詳細步驟：

1. 進入 [NAS 網頁](https://nas.student.csie.ncu.edu.tw/) 並依自己的帳號 (預設為學號) 密碼進行登入。若未擁有帳號，請詳閱[使用規範](#使用規範)。

   > 我們已禁用 http 不安全的連線方式。

   成功登入後應看到以下畫面：

   ![Work Station](./image/screenshot-file-station.png)
   
   其中 `photo` 為先人的照片，而 `wisdom` 為先人的智慧。接下來的檔案操作方式邏輯皆與電腦相差不大，交由各位自行探索。


3. 若要修改密碼或信箱等個人檔案，請登入 [NAS 管理頁面](https://140.115.53.250:5001)，並點擊右上角頭像調整。
   
   > 註：管理員亦無權限查看使用者密碼，建議使用常用密碼，避免遺忘。
   
   ![Overview](./image/screenshot-overview.png)

### SMB 存取

SMB 全名 Server Message Block，為網路檔案分享系統，由微軟提出並一開始使用於 Windows 上，不過現今所有主流作業系統包括 macOS、Linux、iOS、Android 都對其有原生或套件的支援了。

使用 SMB 存取有以下優點：

- 如同使用本機掛載之磁碟
- 更方便的操作檔案
- 無需下載能直接以 Office 或其他本地程式開啟

雖然 SMB 很方便，但也有以下缺點

- 僅在 **連接學校網路** 時能透過 SMB 存取
- 無法開啟由 NAS 內的 Synology Office 創建的檔案

以下分別為在 Linux、macOS、Windows、iOS、Android 上使用 SMB 存取的步驟：

#### Linux

##### Gnome

> Linux 有眾多桌面環境，此處舉 Gnome 為例，其餘操作方法類似

1. 在檔案管理軟體中按下快捷鍵 `Ctrl-L` 或點擊 UI 編輯路徑，輸入以下路徑。

   ```text
   smb://nas.student.csie.ncu.edu.tw
   ```

   ![Gnome Enter Path](./image/screenshot-gnome-path.png)

2. 輸入帳號密碼，工作群組維持為 `WORKGROUP` 不需更改。若未擁有帳號，請詳閱[使用規範](#使用規範)。

3. `photo` 為先人的照片；`wisdom` 為先人的智慧。接下來操作與一般已掛載磁碟機相同。

##### CLI

1. 安裝 `cifs-utils` 套件

2. 掛載到目標目錄，其中：

   - `/mnt` 可為任意空目錄
   - `username` 後應更改為自己的帳號

   ```bash
   # 先人的照片
   sudo mount.cifs //nas.student.csie.ncu.edu.tw/photo /mnt -o username=110502000
   ```

   ```bash
   # 先人的智慧
   sudo mount.cifs //nas.student.csie.ncu.edu.tw/wisdom /mnt -o username=110502000
   ```

3. 取消掛載

   ```bash
   sudo umount /mnt # The path just mounted
   ```

#### macOS

> 筆者無 macOS 設備

#### Windows

在 `檔案總管 > 網路` 輸入 `\\nas.student.csie.ncu.edu.tw` 或是 `\\140.115.53.250` 再輸入帳密即可  
建議可將此頁面釘選到 [快速存取]

![Windows SMB](./image/screenshot-smb-windows.png)

#### iOS

> 筆者無 iOS 設備

建議使用 [Synology Drive 應用程式](#synology-drive) 存取。

建議

#### Android

Android 不同的手機廠商有不同的文件管理軟體，不一定能支援 SMB 連線，可尋找軟體內是否有「遠端連線」或「區域網路」類似的設定選項。若未支援，可至 Play 商店搜尋 SMB 下載支援的軟體。

建議使用 [Synology Drive 應用程式](#synology-drive) 存取。

### Synology Drive

1. 電腦用戶可至 [Synology Drive 網站](https://www.synology.com/zh-tw/dsm/feature/drive) 依作業系統下載安裝檔；手機可至 Play 商店或 APP Store 搜尋**synology drive**，下載應用程式。

2. 安裝完成後，以 `nas.student.csie.ncu.edu.tw` 作為連線位置，並允許 HTTPS 加密。

3. 依自己的帳號密碼進行登入。若未擁有帳號，請詳閱[使用規範](#使用規範)。
