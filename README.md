# itsa
## 題目2. 英哩轉公里
### 問題描述：
試撰寫一程式，可由鍵盤輸入英哩，程式的輸出為公里，其轉換公式如下：\
1 英哩= 1.6 公里
### 輸入說明：
輸入欲轉換之英哩數(int)。
### 輸出說明:
輸出公里(double)，取到小數點以下第一位。
### 範例：
|    輸入範例:    |    輸出範例:   |
| -------------- |:-------------: |
|       90       |      144.0     |
|       95       |    152.0       |

### 程式:
```    
#include <iostream>
#include<iomanip>
using namespace std;
int main()
{
    double x,y;
    cin >> x;
    y = x * 1.6;
    cout << fixed << setprecision(1) << (double)y << endl;
    return 0;
}
```
### 說明程式:
這段程式的是要我們把輸入的英哩轉成公里，首先我先宣告兩個double的變數因為公里跟英哩都有可能是小數點。\
然後再用cin >> x; 將使用者輸入的數字讀取到x 而y則是將我們的轉換公式y = x * 1.6;存取到y裡面。\
最後我用了fixed來固定小數點表示，再用setprecision()函數，因為要取到小數點第一位所以()裡面寫1。\
將y運算出來的答案給輸出最後再換行。\
然後return 0。


## 題目3. 判斷座標是否在圓形的範圍內
### 問題描述：
有一圓形，直徑為200，且中心座標為(0,0)。請寫一支程式可以輸入「點」的座標，並判斷「點」是否在圓形的範圍內。\
如果「點」的位置剛好在邊界的話也算是在圓形範圍內(例：x=100，y=0)。\
![image](https://user-images.githubusercontent.com/126050259/224534681-90faa696-6622-4162-8506-66d38a33ca2c.png)
### 輸入說明：
輸入一整數座標，依序分別X與Y。\
### 輸出說明：
輸出此座標位置在圓內或圓外訊息。\
### 範例：
![image](https://user-images.githubusercontent.com/126050259/224536092-afb1b46d-7bb1-4f7d-8b49-96958bf91ab4.png)


### 說明程式:
```
#include<iostream>
#include<math.h>
using namespace std;

int main()
{
	int x = 0, y = 0;
	while (cin >> x >> y)
	{
		if (sqrt(x * x + y * y) <= 100) cout << "inside" << endl;

		else cout << "outside" << endl;
	}
	return 0;
}
```
宣告兩個整數x和y為0\
while (cin >> x >> y)\
因為要去判斷使用者輸入的座標是否超過這個圓的範圍\
首先我們得知圓的半徑為100所以我們只需帶入算式(A*A+B*B)=C*C\
得出三角形斜邊長並判斷其長度是否在圓的半徑內


## 題目4. 停車費計算

### 問題描述：
假設某個停車場的費率是停車2小時以內，每半小時30元，超過2小時，但未滿4小時的部份，每半小時40元，超過4小時以上的部份，每半小時60元，未滿\半小時部分不計費。如果您從早上10點23分停到下午3點20分，請撰寫程式計算共需繳交的停車費。

### 輸入說明：
輸入兩組時間，分別為開始與離開時間，24小時制。

### 輸出說明：
輸出停車費。

### 範例：
![image](https://user-images.githubusercontent.com/126050259/224537822-4b10c768-b3b2-4078-b078-238492b83c5a.png)

### 程式說明

```
#include <iostream>
using namespace std;
int main()
{
	int h1,h2,m1,m2,h,m,total=0;
	cin >> h1 >> m1;
	cin >> h2 >> m2;
	h = h2 - h1;
	m = (h * 60) + (m2 - m1);

	if (m > 120) {
		m = m - 120;
		total = total + 120;
		if (m > 120) {
			m = m - 120;
			total = total + 160;
			if (m > 1) {
				total = total + ((m / 30) * 60);
			}
		}
		else {
			total = total + ((m / 30) * 40);
		}
	}
	else {
		total = total + ((m / 30) * 30);
	}
	
	
	cout  << total << endl;
	return 0;
}
```
我把時換算成分也就是m = (h * 60) + (m2 - m1);這行\
接下來就是用if去判斷停車的時間\
我們以兩小時跟四小時做一個時間區隔如果時間大於數值將會自動將那個時段的金額加入變數total\
而如果不滿時間將會跑入else的程式將剩餘時間/30並*當下時段的費用以算出剩餘時間的費用

## 題目5. 十進制轉二進制

### 問題描述：
撰寫一個程式，使用者輸入一個整數，印出8位元的二進制表示。

### 輸入說明：
輸入一個整數，介於-128～127之間。

### 輸出說明：
以8位元的二進制顯示。

### 範例：
![image](https://user-images.githubusercontent.com/126050259/224538644-92277d8c-838d-4479-b054-2c8477e7ae8f.png)

### 程式說明:
```
#include<iostream>  
using namespace std;

int main() {
    int n = 0;
    int bin[8];
    cin >> n;
    if (n < -128 || n > 127) {
        cout << "error！" << endl;
        return 0;
    }
    if (n < 0)
    {
        n += 256;
    }
    for (int i = 7; i >= 0; i--)
    {
        bin[i] = n % 2;
        n /= 2;
    }
    for (int i = 0; i < 8; i++)
    {
        cout << bin[i];
    }
    cout << "\n";

}
```

宣告一個整數n=0將輸入的數字存到n\

int bin[8];因為要以八位元二進制顯示\

![image](https://user-images.githubusercontent.com/126050259/224543384-bf8a2368-f4c8-4f00-a007-38d417cd61c3.png)

這段是-128~127這段的範圍，如果超過就會跑error!\
 
 ![image](https://user-images.githubusercontent.com/126050259/224543409-340ce41a-9931-4c60-9370-be09d428490e.png)


因為我是用補數的方式來呈現負數所以這裡打上了這個\


![image](https://user-images.githubusercontent.com/126050259/224543425-430cddb5-b4aa-48d5-b9fa-f692bc891aaf.png)

接下來這裡因為十進制轉二進制我是用短除法那樣去轉所以bin[i] = n % 2;裡面的i是n%2的結果下面n /= 2;就是除法，下一個迴圈就是把那個i給印出來而已

## 題目6. 季節判定

### 問題描述：
試撰寫一程式，可輸入月份，然後判斷其所屬的季節（ 3~5 月為春季，6~8 月為夏季， 9~11 月為秋季， 12~2 月為冬季）。

### 輸入說明：
輸入月份。

### 輸出說明：
輸出該月份的季節， 3~5 月為春季(Spring)， 6~8 月為夏季(Summer)， 9~11 月為秋季(Autumn)， 12~2 月為冬季(Winter)。    

### 範例：
![image](https://user-images.githubusercontent.com/126050259/224543620-bc905302-3696-4886-92c9-a6f1dbd511a3.png)

### 程式說明:
```
#include <iostream>
using namespace std;

int main() {
    int m;
    cin >> m;

    if (m >= 3 && m <= 5) {
        cout << "Spring" << endl;
    }
    else if (m >= 6 && m <= 8) {
        cout << "Summer" << endl;
    }
    else if (m >= 9 && m <= 11) {
        cout << "Autumn" << endl;
    }
    else {
        cout << "Winter" << endl;
    }
    return 0;
}
```
宣告一個整數m\
將輸入的數字儲存到m\
用if去判斷輸入的數字是哪個季節\
如3-5月就是spring

