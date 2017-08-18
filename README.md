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
1. 除非整句英文，否則標點符號一律中文半形。
2. 中文和英文、數字中間以 1 個半形空白隔開。
3. 所有文件都以markdown撰寫。
4. 細部文件一律放在 /doc (沒有資料夾的話，自己開一個)。
5. 引用圖檔一律放在 /image (沒有資料夾的話，自己開一個)。


## Files
1. public：連線路徑：參考 composer.json 設定。
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