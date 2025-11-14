#### GUI 設定, 一開始畫面的設定
提示語
Screen 的部份  
    1.程式執行 Zoom 放到最大
---
    root = tk.Tk()
    root.title("ERP SQL 查詢工具")
    root.state('zoomed')
    screen_width = root.winfo_screenwidth()  
    screen_height = root.winfo_screenheight()
<!-- 
讓下列2行,結果不會是同一行(只有一行)
方法 1：行尾加兩個空格   在第一行的結尾加上兩個空格，然後換行
    screen_width = root.winfo_screenwidth()  這邊有多空2各自元
screen_height = root.winfo_screenheight()
方法 2：使用 <br> 標籤   第一行的結尾加上<br>，然後換行
    screen_width = root.winfo_screenwidth()<br>
    screen_height = root.winfo_screenheight()
方法 3：使用程式碼區塊    如果是程式碼，建議使用程式碼區塊：
    ```python
     screen_width = root.winfo_screenwidth()
     screen_height = root.winfo_screenheight()
    ```
-->

## Frame 的定義
    factory_frame = tk.Frame(root, borderwidth=1, relief="solid")  
    factory_frame.place(x=0, y=0, width=screen_width, height=40)
<!-- 這行最後有空白2各字元, 結果是 上下行是分開行, 不會連在一起   -->
input_frame = tk.Frame(root, borderwidth=1, relief="solid")  
 input_frame.place(x=0, y=45, width=screen_width, height=40)  
  input_frame = tk.Frame(root, borderwidth=1, relief="solid")  
   input_frame.place(x=0, y=45, width=screen_width, height=40)  
    input_frame = tk.Frame(root, borderwidth=1, relief="solid")  
     input_frame.place(x=0, y=45, width=screen_width, height=40)  
      input_frame = tk.Frame(root, borderwidth=1, relief="solid")  
       input_frame.place(x=0, y=45, width=screen_width, height=40) 


 button_frame = tk.Frame(root, borderwidth=1, relief="flat")  
   button_frame.place(x=0, y=90, width=screen_width, height=50)  
    button_frame = tk.Frame(root, borderwidth=1, relief="flat")  
     button_frame.place(x=0, y=90, width=screen_width, height=50)

result_frame = tk.Frame(root, borderwidth=1, relief="solid")  
result_frame.place(x=0, y=150, width=screen_width, height=screen_height - 150 - 60)

error_frame = tk.Frame(root, borderwidth=1, relief="solid", bg="lightgray")  
error_frame.place(x=0, y=screen_height - 60, width=screen_width, height=60)

## 獲取可執行檔的目錄
if getattr(sys, 'frozen', False):  
    <pre>.....</pre> base_path = Path(sys.executable).parent  
else:  
    base_path = Path(__file__).parent

使用相對於可執行檔目錄的路徑
subno_path = base_path / "xlsx" / "subno.xlsx"
input_path = base_path / "xlsx" / "input.xlsx"

## Frame.button 的定義 (使用 place 會定住不會隨著Screen的調整而跳動)
btn_query = tk.Button(button_frame, text="查詢", command=lambda: execute_sql(), font=(12), width=8, height=2)
btn_query.place(x=10, y=5)

btn_test = tk.Button(button_frame, text="測試", command=test_button, font=(12), width=8, height=2)
btn_test.place(x=100, y=5)
##	Result_frame 的變化
  調整圖片大小以適應 result_frame
        frame_width = result_frame.winfo_width()  # Smart
        frame_height = result_frame.winfo_height() # Smart
   以 TABLE 的型態取顯現在 result_table
        result_table = Table(result_frame, dataframe=df_result, showtoolbar=True, showstatusbar=True)
        result_table.show()
        result_table.redraw()
        result_table.update_idletasks()
## 載入 subno 和 SQL 模板資料
    df_factories = pd.read_excel(subno_path, sheet_name="subno", engine="openpyxl")
    factories = df_factories["subno"].tolist()
    connections = dict(zip(df_factories["subno"], df_factories["connection"]))
