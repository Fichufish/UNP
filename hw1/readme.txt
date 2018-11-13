(1)程式流程
fork
>開啟Socket
>設定網路連線(TCP/IP協定、port、對外IP)
>開啟監聽器bind()
>監聽listen()
>等待客戶端連線accept()
>若有客戶連線 fork()出子行程
>子行程讀寫瀏覽器要求
>關掉父行程

select
>開啟Socket
>設定網路連線(TCP/IP協定、port、對外IP)
>開啟監聽器bind()
>監聽listen()
>初始化客戶端，設置最大連線可處理人數
>等待客戶端連線accept()
>若有客戶連線 加入到客戶端array
>對有連線的客戶端進行讀寫瀏覽器要求

(2)功能實作
fork
使用pid=fork()建立子行程
若pid=0，為子行程，進行讀寫瀏覽器的要求
非0則為父行程，可以關閉

select
像stack一樣使用client[]存放來連線的客戶
後一個個為客戶端進行讀寫瀏覽器要求

讀寫瀏覽器要求
最基本的要求:GET /index.html HTTP/1.0\r\n\r\n
若讀到GET命令，進行字串處理，並開啟index.html網頁

(3)資料結構
大概就client[]的stack概念

(4)期望加分
N/A