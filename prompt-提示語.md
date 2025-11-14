##幫我生成一個 sql005-cursor.py
### 1.GUI 的設定
### 2.使用相對於可執行檔目錄的路徑
subno_path = base_path / "xlsx" / "subno.xlsx"
input_path = base_path / "xlsx" / "input.xlsx"
### 3.frame 的組成
有5個 frame
F-1 : name = factory_frame ,   borderwidth=1, relief="solid", factory_frame.place   (x=0, y= 0, width=screen_width, height=40)
F-2 : name = input_frame,      borderwidth=1, relief="solid", input_frame.place     (x=0, y=45, width=screen_width, height=40)
F-3 : name = button_frame,     borderwidth=1, relief="flat",  button_frame.place    (x=0, y=90, width=screen_width, height=50)
F-4 : name = result_frame,     borderwidth=1, relief="solid", result_frame.place    (x=0, y=135, width=screen_width, height=screen_height - 150 - 60)
F-5 : name = error_frame =     borderwidth=1, relief="solid", bg="lightgray",       (x=0, y=screen_height - 60, width=screen_width, height=60)
### 4.frame 上的 lable, Combobox, button 
F-1-1 : label 廠別 + combo 從下拉選單選擇目標廠別, 資料來源  subno.xlsx 的 A儲存格 (subno)
F-1-2 : label 代碼 + combo 從下拉選單選擇目標代碼,

F-3-1 : button name = '查詢'   font=(12), width=8, height=2, btn_query.place(x=  10, y=   5)
F-3-2 : button name = '存檔'   font=(12), width=8, height=2, btn_query.place(x= 110, y=   5)
F-3-3 : button name = 'E-mail' font=(12), width=8, height=2, btn_query.place(x= 220, y=   5)
F-3-9 : button name = '離開'   font=(12), width=8, height=2, btn_query.place(x=1430, y=   5)




### 5. result_frame: 查詢結果顯示的元件與函式       def execute_sql():


button_frame.place(x=0, y=90, width=screen_width, height=50)


factor的 LABEL 的 LABEL 上有按鈕  F-1-1.查詢  F-1-2.   F-1-3.   F-1-4.   F-1-5.
F-2. factory_frame 上有按鈕  F-1-1.查詢  F-1-2.   F-1-3.   F-1-4.   F-1-5.







主要功能
1. 多廠別支援
factory 支援多個廠別資料庫連線，根據 User 所選定的廠別而定, 切換動態切換不同的資料庫環境
A001 自動替換 SQL 中的廠別相關參數
2. 動態查詢介面
下拉選單選擇查詢代碼
根據選擇的查詢自動生成輸入欄位
支援不同類型的輸入參數
3. SQL 查詢執行
PostgreSQL 資料庫支援
自動參數替換和 SQL 生成
查詢結果以表格形式顯示
4. 資料匯出功能
Excel 檔案匯出
自動郵件發送功能
支援多種資料格式