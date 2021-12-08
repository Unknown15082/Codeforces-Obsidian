[Problem Link](https://codeforces.com/problemset/problem/1600/E)
%%[[Combinatorics]]%%

Xét mảng $a_1, a_2, ..., a_n$, và giả sử đây là lượt của Alice.

Ta xét 2 trường hợp sau:

1. $a_1 \ne a_n$

Không mất tính tổng quát, giả sử $a_1 > a_n$. Xét dãy con tăng dài nhất bắt đầu từ $a_1$ là $a_1 < a_2 < ... < a_k$. Ta có 2 trường hợp sau:
- $k$ % 2 = 1: Khi đó, Alice sẽ lấy số $a_1$. Do $a_2 > a_1 > a_n$ nên Bob bắt buộc phải chọn $a_2$, Alice tiếp tục lấy $a_3$, ... Cuối cùng, Bob sẽ lấy số $a_{k-1}$ và Alice sẽ chọn $a_k$. Do dãy $a_1, a_2, ..., a_k$ là dãy con tăng dài nhất nên $a_k \ge a_{k+1}$ và $a_k > a_1 > a_n$, vậy nên Bob không thể chọn số nào nữa. Như vậy Alice thắng.
- $k$ % 2 = 0: Nếu Alice chọn số $a_1$, mọi chuyện sẽ diễn ra như trên, nhưng với Bob chọn số $a_k$ thay vì Alice. Chứng minh tương tự, Bob sẽ thắng. Vì vậy, Alice sẽ bắt buộc phải chọn số $a_n$ để không thua, và bài toán trở về xét mảng $a_1, a_2, ..., a_{n-1}$ và hiện tại đang là lượt của Bob.

2. $a_1 = a_n$

Ta xét tương tự như trên. Giả sử dãy con tăng dài nhất bắt đầu từ $a_1$ là $a_1, a_2, ..., a_x$, và dãy con giảm dài nhất kết thúc tại $a_n$ là $a_y, a_{y+1}, ..., a_n$. Ta đặt độ dài của dãy đầu là $L_1$ và độ dài dãy sau là $L_2$.

- Nếu $L_1$ hoặc $L_2$ lẻ thì chứng minh như trên, Alice sẽ thắng.
- Nếu $L_1$ và $L_2$ cùng chẵn thì tương tự, ta có thể chứng minh được là Bob thắng.

Ta sẽ dùng một hàm đệ quy $F(l, r, turn)$ để tìm người thắng cuộc trong bài toán xét mảng từ $a_l$ tới $a_r$ và người bắt đầu là $turn$. (Coi Alice $= 0$ và Bob $= 1$). Kết quả ta cần tìm là $F(1, n, 0)$. Do ta thấy mỗi hàm đệ quy chỉ gọi tối đa $1$ hàm khác, và mỗi lần như vậy, khoảng tìm kiếm sẽ giảm đi $1$ phần tử, vậy nên chỉ xảy ra tối đa $n$ lần gọi hàm.

Ta có thể tính được dãy con tăng dài nhất bắt đầu từ $a_x$ và dãy con giảm dài nhất kết thúc tại $a_x$ bằng cách pre-calculate trong $O(n)$. Vì vậy, ta sẽ tính mỗi hàm $F$ trong $O(1)$, và bài toán được giải quyết trong $O(n)$.

[Solution](https://codeforces.com/contest/1600/submission/137756157)