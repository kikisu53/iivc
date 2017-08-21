## Frameworks & Database
1. PHP: Slim 3

    ```
    $ php composer.phar create-project slim/slim-skeleton [app name]
    ```

2. Bootstrap: startbootstrap-sb-admin-2

	```
	$ git clone https://github.com/BlackrockDigital/startbootstrap-sb-admin-2.git
	```
	 
    | startbootstrap-sb-admin-2 路徑 | iicv 對應路徑 | 說明 |
    |---|---|---|
    | vendor/ | public/style/ | sb-admin-2 的引用檔 |
    | dist/   | public/style/sb-admin-2/dist/ | sb-admin-2 自定義檔 |
    | js/     | public/style/sb-admin-2/js/ | sb-admin-2 自定義檔 |
    | less/   | public/style/sb-admin-2/less/| sb-admin-2 自定義檔 |

3. MVC (這是我理解的 MVC 搭配資料庫需求所下的定義，明確和詳細的定義，請自行GOOGLE)
    * Controller：請求進來之後( Route )，控制流程。
    * View：呈現給使用者的網頁。
    * Model：處理資料庫中的資料。

4. Database：MySQL


## Files
1. public：連線路徑，參考 composer.json 設定。
    * index.php 和 .htacess 。
    * style： startbootstrap-sb-admin-2 和 自定義 .css 。
        - sb-admin-2: sb-admin-2 自定義檔，包括 dist 、 js 、 less 。
        - ivc： 本專案的自定義檔，包括 .css 和 .js 。
        - 其他資料夾： sb-admin-2 的引用套件。
    * js： .js ，使用者互動的 js 檔案，版面控制的 js 放在 style/iivc 。
2. src：各種設定( .php )
    * settings
    * middleware
    * dependencies
    * routes
3. vendor： php 套件，參考 composer.json 。( gitigonre )
4. templates：.html 、 .phtml 。( Views )
5. models：資料處理。( Models )
6. controllers：( Controllers )
7. test： 測試檔， .php 。
8. logs
9. docs：文件


## 功能設計
0. 權限說明
    * 0 查詢者：只能查詢，終身權限。
        - 回顧 2017/4 的 line 對話內容，老師詢問校友怎麼辦，推測老師不排斥校友使用，故查詢者開放終身權限。
    * 1 輸入者：增加輸入權限，時間由管理者或老師決定。
        - 時間以學期為單位(每年 1/31 或 7/31 終止)，學期中加入就算一學期，每次最少開一學期，最多開四學期。
        - 輸入者或管理者推測會是大三大四或研究生，因此最多開四學期。
    * 2 管理者：增加非管理者的權限開關(只能管理非管理者)，時間由老師決定。
    * 3 老師：增加管理者的權限開關(可以管理所有使用者)，終身權限。
2. nav(選單)
    * nav-top
        - 固定在頁面左邊，捲軸不管捲多下方，仍固定在上方。
        - 依照使用登入狀況，提供不同選單
            + 0 未登入：註冊、登入
            + 1 登入：登出、修改密碼、權限申請
    * nav-sider
        - 固定在頁面左邊，捲軸不管捲多下方，仍固定在左邊。
        - 依照使用者權限，提供不同的選單。
            + 0 查詢者選單： for all 。
            + 1 輸入者選單： for 0 老師 、 1 管理者 、 2 輸入者。
            + 2 管理者選單： for 0 老師 、 1 管理者。
3. 使用者管理功能
    * 註冊 register：註冊成功後，系統皆設定為查詢者權限，其他權限需由管理者或老師手動開啟。
        - @nuk.edu.tw 的註冊者：信箱驗證。
        - 其他註冊者
            + 需填寫：真實姓名、系級、目的。
            + 信箱驗證通過後，管理者或老師審查，如審查未過，刪除該帳號。 ( 2017/4 line )
    * 登入 login
        - 帳號為註冊的 mail
        - 新增 session
        - 顯示 nav-sider
    * 登出 logout
        - 刪除 session
        - 導回登入頁
    * 忘記密碼 changePW
        - mail 系統給定密碼到註冊信箱
        - 新密碼 7 天內有效
        - 登入後，強制修改密碼
    * 修改密碼 forgetPW
    * 權限申請 authority_apply
        - 表格：真實姓名、系級、目的
4. 查詢者功能 - 策略
    * 五力分析 5p_query -> 5p_detail ( ajax 同一頁面呈現)
        - 可延伸查詢 產業、集團、公司、地區、國家、原物料、產品、服務
    * 價值鏈 vc_query -> vc_detail ( ajax 同一頁面呈現)
        - 可延伸查詢 產業、集團、公司、地區、國家、原物料、產品、服務
    * Michael Porter Diamond Model
    * The CAGE
4. 查詢者功能 - 基本資訊
    * 產業查詢 ind_query -> ind_detail
    * 集團、公司查詢 co_query -> co_detail
    * 地區、國家查詢 rc_query -> rc_detail
    * 原物料、產品、服務查詢 ob_query -> ob_detail
5. 輸入者功能
    * 輸入 keyin
6. 管理者功能
    * 權限管理 authority_manage
        - 新註冊者審核
        - 開啟「輸入者、管理者」權限
    * 「集團、公司」名稱異同調整 co_adjust
    * 公司所屬集團調整 group_adjust
    * 「原物料、產品、服務」名稱異同調整 ob_adjust


##　安全性設計
1. 所有表單都有 token 。
2. session驗證


## 資料庫設計
1. 參考整理的word檔


## Programming Rules
1. 資料夾：全部小寫，用-區分單字。
2. 檔案
    * 程式碼內容為物件：命名和物件一致，採大寫駝峰。
    * 一般檔案：全部小寫，以底線區分單字。
2. Class 物件:大寫駝峰，例如 $NewObject 。
    * 物件屬性：大寫駝峰，前面加 m ，例如 $mPropertyName 。
    * 方法(物件中的 function ):小寫駝峰，例如 function methodName 。
        - 方法參數：小寫駝峰，例如 $paramName 。
3. function 函數：全部小寫，以底線區分單字， 例如 function fun_name 。
4. 變數：全部小寫，以底線區分單字，例如 $var_name 。
    * 全域變數前面加 g ，例如 $gvar_name 。
    * 靜態變數前面加 s ，例如 $svar_name 。
5. $query 、 $result 限 SQL 使用。


## Docs Rules
1. 所有文件都以markdown撰寫。
2. 除非整句英文，否則標點符號一律中文半形。
3. 中文和英文、數字中間以 1 個半形空白隔開。
4. 細部文件一律放在 /docs  (沒有資料夾的話，自己開一個)。。
5. 引用圖檔一律放在 /images (沒有資料夾的話，自己開一個)。