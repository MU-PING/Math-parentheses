# Math-parentheses
## 程式簡介
### 簡述
> 使用 Dynamic Programming 技術實作

A mathematical expression is given without parentheses. Design an algorithm to parenthesize the expression such that the value of the expression is maximized. For example, consider the expression: 2 + 7 * 5. There are two ways to parenthesize the expression 2 + ( 7 * 5 ) = 37 and ( 2 + 7 ) * 5 = 45, so in this case, your algorithm
should output the second expression. Here, you may assume the given expressions contain only 3 kinds of binary operators ‘ + ’, ‘ - ’, and ‘ * ’.

* Input：數學表達式
* Output：含括號的數學表達式，其值最大

1 <= expression's length <= 30 and if there are several solutions, output one of them

Example 1
```
Input: 2 + 7 * 5 - 3 * 6
Output: ( ( ( 2 + 7 ) * 5 ) - 3 ) * 6  or  ( ( ( ( 2 + 7 ) * 5 ) - 3 ) * 6 ) 
```

 
Test 1
```
Input: 5 - 8 + 7 * 4 - 8 + 9
Output: 5 - ( ( 8 + 7 ) * ( 4 - ( 8 + 9 ) ) )  
```
Test 2
```
Input: -11 + 22 - -11 - 22
Output: -11 + ( 22 - ( -11 - 22 ) )  
```
Test 3
```
Input: 2 - 7 * 5 + 1 - 4 + 8 * 3 
Output: 2 - ( 7 * ( 5 + ( 1 - ( ( 4 + 8 ) * 3 ) ) ) )   
```

### 補充說明
1. Q: 輸入都沒有空格 ? 要不要重複輸入 ?  
A: 輸入只有一行，沒有空格，不需重複輸入

2. Q: 數字一定是整數 ? 一定小於10 ?  
A: 數字位數>=1，但不會太大，不需考慮overflow

3. Q: 所謂總長度 <= 30指的是 數字數 ? 運算數 ? 字元數 ?  
A: 字元數，例如：-12 * -11 + 5 - -0 總長度 = 12

4. 「如果數字前有負號且負號前有一個運算子」 或 「第一個數字前面有負號」，則把負號跟數字看為負整數  
例如：-10+-30，-10、-30 是一負整數，不是減法的意思

### 範例圖
#### Input
![image](https://user-images.githubusercontent.com/93152909/139864586-5d737cb9-325b-4ef8-a4c2-bd34d5813338.png)
#### DP
![image](https://user-images.githubusercontent.com/93152909/139864346-b5e3ac62-ea18-49b8-86d0-b018d02b1e09.png)
#### Output
> 最小值用同樣原理也可以產生，原始碼中有額外實作

![image](https://user-images.githubusercontent.com/86537930/125863992-4ae54fad-6e7a-4ffc-8bdc-340f4053e0f9.png)

## Dynamic Programming
> 動態規劃，簡稱 DP，是一種通過把原問題分解為相對簡單的子問題的方式求解複雜問題的方法。
* Dynamic Programming = Divide and Conquer + Memoization
	* Divide and Conquer：動態規劃是分治法的延伸
	* Memoization：子問題一再出現，就用記憶法儲存這些問題的答案，避免重複求解，以空間換取時間

* DP 常適用於有「重疊子問題」和「最佳子結構」性質的問題，且子問題要滿足「無後效性」
	* 重疊子問題：子問題具相同解法與答案
	* 最佳子結構：局部最佳解能決定全域最佳解
	* 無後效性：即子問題的解一旦確定，就不再改變
* 滿足 DP 性質的實例
	* fibonacci數列
	* 切割鋼條問題
	* Floyd最短路問題
	* 最大不下降子序列
	* 矩陣鏈乘
	* 凸多邊形三角剖分
	* 0-1背包
	* 最長公共子序列
	* 最佳二分搜尋樹 
* fibonacci 實例  
計算 fib(4) 時，fib(2) 會出現兩次，將 fib(2) 透過記憶體存起來，可以避免重複計算。 fib(0) 、 fib(1)亦如此。
![image](https://user-images.githubusercontent.com/86537930/126080949-ab9cda9a-dae5-462c-9773-9f2f096b1d1f.png)
