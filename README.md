## Basic Frameworks
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


## Programming Rules & Docs Rules
1. http://www.ichiayi.com/wiki/tech/mantis_coding

## Docs Rules
1. 所有文件都以markdown撰寫。
2. 除非整句英文，否則標點符號一律中文半形。
3. 中文和英文、數字中間以 1 個半形空白隔開。
4. 細部文件一律放在 /doc (沒有資料夾的話，自己開一個)。
5. 引用圖檔一律放在 /image (沒有資料夾的話，自己開一個)。


## Files
1. public：連線路徑，參考 composer.json 設定。
    * index.php 和 .htacess 。
    * style： startbootstrap-sb-admin-2 和 自定義 .css 。
    * js： .js 。
2. config：各種設定( .php )
    * settings
    * middleware
    * dependencies
    * routes
3. vendor： php 套件，參考 composer.json 。( gitigonre )
5. templates：.html 、 .phtml 。( Views )
6. models：資料處理。( Models )
7. controllers：( Controllers )
8. test： 測試檔， .php 。
9. logs


## 架構
0. 權限說明
    * 0 查詢者：只能查詢，終身權限。
        - 回顧 4 月的 line 對話內容，老師詢問校友怎麼辦，推測老師不排斥校友使用，故查詢者開放終身權限。
    * 1 輸入者：增加輸入權限，時間由管理者或老師決定。
        - 時間以學期為單位(每年 1/31 或 7/31 終止)，學期中加入就算一學期，每次最少開一學期，最多開四學期。
        - 輸入者或管理者推測會是大三大四或研究生，因此最多開四學期。
    * 2 管理者：增加非管理者的權限開關(只能管理非管理者)，時間由老師決定。
    * 3 老師：增加管理者的權限開關(可以管理所有使用者)，終身權限。

1. nav(選單)：依照使用者權限，提供不同的選單
    * nav0：查詢者選單，登出、修改密碼、權限申請， for all 。
    * nav1：輸入者選單， for 0 老師 、 1 管理者 、 2 輸入者。
    * nav2：管理者選單， for 0 老師 、 1 管理者。

2. 使用者管理功能
    * 註冊 register 
    * 登入 login
    * 登出 logout
    * 忘記密碼 changePW
    * 修改密碼 forgetPW
3. 管理者功能
    * 權限管理
    * 「所屬集團、集團、公司」名稱異同調整。
    * 「原物料、產品、服務」名稱異同調整
4. 輸入者功能
    * keyin
5. 查詢者輸入
    * 5p
    * vc
    * 產業查詢
    * 集團、公司查詢
    * 地區、國家查詢
    * 原物料、產品、服務