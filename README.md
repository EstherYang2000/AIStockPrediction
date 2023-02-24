# AIStockPrediction
The utilization of AI and data of social media in regard with stock investment
1. Predicted whether TSMC’s stock price was categorized as bullish or bearish by utilizing 10+ thousand and 3-year articles from PTT, News, forums as well as historical stock records.
2. Proposed trading strategies with back-testing utilizing machine learning models, such as SVM model, whose
3. precision rate reached 84.1% in top condition.  

The code stage includes three requirements.  

##  Requirement 1. Do Preproccessing of TSMC data
In requirement 1, we pick out a number of bullish and bearish articles first.  
We divided the work into two stages, including analysing stock price rallies and falls, and marking bullish and bearish articles.

### Analysing stock price rallies and falls
We choose **2330** as the target stock since its high social volume. 
However, to increase the scope of the program, we also present the **stock names** and **stock codes** as parameters to facilitate switching to other targets. 
<img width="547" alt="image" src="https://user-images.githubusercontent.com/80161804/221087736-4d92a00b-afef-4041-a96d-39723d47a4e7.png">

Another parameter, n, is the number of days to calculate the **UP** and **DOWN**, which mean that the **UP** and **DOWN** of a given day are calculated by comparing the closing price of that day with that of **n** days ago.
Then, we set n as 3 in this proposal.
<img width="561" alt="image" src="https://user-images.githubusercontent.com/80161804/221087848-555869f9-a9ca-42d9-9908-bb40595191a5.png">


We read the three years of stock price information for the target stock into a DataFrame, and sort it by date to calculate the n-day increase or decrease.  Then we lable the stock with Up or down label (up, down, -). 
Similarly, in order to increase the scope of the program and to maximise the average number of up and down data, instead of using a constant parameter for the threshold sigma, we define a function to determine the sigma. Therefore, there are six sigma values, which are the average increase and decrease for each of the three years. After labelling the ups and downs, we then link the three years of data together.
我們將目標個股的三年股價資訊讀取成 DataFrame 並以日期排序，計算 n 日漲跌幅，加上漲跌標籤（漲、跌、－）。同樣地，為了增加程式應用範圍以及盡量平均漲跌資料筆數，我們並沒有把判斷漲跌標籤的閾值 sigma 以常數參數表示，而是定義了函式來決定 sigma。判斷漲跌標籤的規則為：漲幅大於當年平均漲幅視為漲，跌幅大於當年平均跌幅視為跌；故一共有六個 sigma 值，分別為三年度的平均漲、跌幅。標記完漲跌標籤後，我們會把三年的資料串接起來。



