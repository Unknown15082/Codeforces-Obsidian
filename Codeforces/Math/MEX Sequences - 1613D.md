[Problem Link](https://codeforces.com/problemset/problem/1613/D)
%%[[Math]]%%

Xét một dãy số có MEX = $m$. Có 2 loại dãy số như sau thỏa mãn:
- Dãy số có tất cả các số $< m$. Như vậy, dãy số này sẽ có dạng $0, ..., 0, 1, ..., 1, ..., m-1, ..., m-1$.
- Dãy số có ít nhất 1 số $> m$. Khi đó, dãy sẽ có dạng $0, ..., m-1, x_1, x_2, ..., x_k$, với các số $x_i$ thuộc $\{m-1, m+1\}$.

Ta kí hiệu $dp[i][1]$ là số lượng các dãy dạng 1 có MEX = $i$, và $dp[i][2]$ là số dãy dạng 2 có MEX = $i$. Mỗi khi thêm 1 số $x$ mới, ta sẽ có 3 update sau:

- Số các dãy dạng 1 có MEX = $x+1$ ($dp[x+1][0]$) sẽ tăng thêm gấp đôi (vì ta có thể giữ nguyên dãy cũ, hoặc thêm số $x$ vào cuối dãy). Ngoài ra, $dp[x+1][0]$ cũng tăng thêm $dp[x][0]$, vì thêm số $x$ vào cuối dãy dạng 1 với MEX = $x$ sẽ tạo một dãy dạng 1 mới có MEX = $x+1$.
- Số các dãy dạng 2 có MEX = $x+1$ ($dp[x+1][1]$) sẽ tăng gấp đôi, vì ta có thể thêm $x$ vào dãy cũ hoặc giữ nguyên dãy.
- Số các dãy dạng 2 có MEX = $x-1$ ($dp[x-1][1]$) sẽ tăng gấp đôi. Ngoài ra, ta còn có thể tạo ra dãy dạng này bằng cách thêm số $x$ vào cuối một dãy dạng 1 mà đã có MEX = $x-1$. Lưu ý rằng ta chỉ update $dp[x-1][1]$ khi $x > 0$.

Kết quả chúng ta cần là tổng tất cả các số trong mảng $dp$, trừ đi 1 (đó là dãy rỗng, có dạng 1 và MEX = $0$).

Dễ thấy rằng MEX tối đa của một dãy có $n$ số chính là $n$, vậy nên ta chỉ phải lưu $2(n+1)$ số trong mảng $dp$. Mỗi khi kiểm tra 1 số, ta thực hiện 3 lần update. Ta chỉ kiểm tra đúng $n$ số trong dãy, vậy nên độ phức tạp thời gian là $O(n)$.

[Solution](https://codeforces.com/contest/1613/submission/137670465)

