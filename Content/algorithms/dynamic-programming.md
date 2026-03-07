


Dưới đây là nội dung chuẩn Markdown cho bài viết **"Một vài bài toán Quy hoạch động thú vị"**. Nội dung được thiết kế với độ dài, chiều sâu và cấu trúc phù hợp để bạn có thể dễ dàng chuyển đổi sang HTML semantics (như `<table>`, `<blockquote>`, `<ul>`, `<pre><code>`) nhằm tối ưu điểm số môn Tin học 12.

---

# 🧠 Thuật toán: Một vài bài toán Quy hoạch động thú vị

**Chuyên mục:** Thuật toán (Algorithms) | **Dự án:** Cow IT Wiki

Nếu ví Lập trình viên như những chiến binh, thì các Ngôn ngữ lập trình là vũ khí, còn Thuật toán chính là "Binh pháp". Trong thế giới binh pháp đó, **Quy hoạch động (Dynamic Programming - DP)** nổi lên như một trong những kỹ thuật mạnh mẽ, tinh tế và cũng "hại não" nhất.

---

## 1. Quy hoạch động là gì? Sự vĩ đại của việc "Ghi nhớ"

Quy hoạch động (Dynamic Programming) là một kỹ thuật thiết kế thuật toán được nhà toán học Richard Bellman phát triển vào những năm 1950. Trái với tên gọi có vẻ mang tính "lập kế hoạch" (Planning), chữ "Programming" ở đây mang ý nghĩa toán học: tìm ra một chuỗi các bước tối ưu để giải quyết vấn đề. 

Về bản chất, Quy hoạch động là phương pháp giải quyết một bài toán lớn bằng cách **chia nhỏ nó thành các bài toán con** đơn giản hơn. Tuy nhiên, điểm khác biệt sống còn của DP so với phương pháp "Chia để trị" (Divide and Conquer - như thuật toán Quick Sort hay Merge Sort) nằm ở nguyên lý cốt lõi: **"Nhớ kết quả bài toán con"**.

> *"Những ai không thể nhớ quá khứ đều bị nguyền rủa phải lặp lại nó."* – Câu nói triết học này mô tả chính xác 100% bản chất của Quy hoạch động.

Hãy tưởng tượng một ví dụ vui:
- Nếu tôi viết lên bảng phép tính: `1 + 1 + 1 + 1 + 1 + 1 + 1 + 1 = ?` 
- Bạn đếm và trả lời: `8`
- Sau đó, tôi viết thêm `+ 1` vào cuối chuỗi phép tính trên và hỏi: `Bây giờ là bao nhiêu?`
- Bạn sẽ ngay lập tức trả lời là `9` mà không cần đếm lại từ đầu. Vì sao? Vì bộ não của bạn đã **ghi nhớ** kết quả của chuỗi trước đó là 8, bạn chỉ việc lấy `8 + 1 = 9`.

Đó chính là Quy hoạch động! Thay vì để máy tính phải tính đi tính lại một bài toán con (Overlapping Subproblems), chúng ta ép nó lưu kết quả vào một mảng hoặc một bảng (bộ nhớ). Khi cần đến, máy tính chỉ việc "tra cứu" thay vì "tính toán".

Một bài toán chỉ có thể giải bằng Quy hoạch động nếu nó thỏa mãn 2 điều kiện tiên quyết:
1. **Cấu trúc con tối ưu (Optimal Substructure):** Lời giải tối ưu của bài toán lớn được tạo thành từ lời giải tối ưu của các bài toán con.
2. **Các bài toán con gối nhau (Overlapping Subproblems):** Trong quá trình chia nhỏ, các bài toán con sẽ bị lặp lại rất nhiều lần.

Hai phương pháp tiếp cận chính của DP là:
- **Top-Down (Memoization - Ghi nhớ):** Bắt đầu từ bài toán lớn nhất, gọi đệ quy xuống các bài toán con. Lời giải bài toán con sẽ được lưu vào bộ nhớ cache.
- **Bottom-Up (Tabulation - Lập bảng):** Giải quyết tất cả các bài toán con nhỏ nhất trước, lưu vào một bảng (Array/Table), sau đó dùng kết quả ở bảng đó để dần dần xây dựng lên lời giải cho bài toán lớn nhất.

> `[GỢI Ý CHÈN ẢNH HTML]:` Tại vị trí này, bạn nên dùng thẻ `<img>` chèn một bức ảnh so sánh "Cây đệ quy khổng lồ của bài toán Fibonacci" (chưa tối ưu) và "Cây đệ quy đã được cắt tỉa nhờ Memoization" (đã tối ưu). Đặt class CSS `.img-zoom-hover` để tạo hiệu ứng khi trỏ chuột vào.
![Image 1 Placeholder](../../images/algorithms/minh-hoa-fibonacci.png)
---

## 2. Phân tích bài toán kinh điển: Cái túi 0/1 (0/1 Knapsack Problem)

Để thấy rõ sức mạnh của Quy hoạch động, đặc biệt là kỹ thuật Lập bảng (Tabulation), chúng ta hãy cùng đến với một bài toán kinh điển trong lý thuyết tối ưu hóa: **Bài toán Cái túi 0/1**.

**Đề bài:**
Một tên trộm đột nhập vào cửa hàng mang theo một cái túi (balo) có thể chịu được trọng lượng tối đa là `W`. Trong cửa hàng có `n` đồ vật, mỗi đồ vật thứ `i` có trọng lượng là `w_i` và giá trị là `v_i`. Tên trộm nên chọn lấy những đồ vật nào để tổng giá trị lấy được là lớn nhất mà không làm rách túi (tổng trọng lượng không vượt quá `W`)?
*Ràng buộc: Mỗi đồ vật chỉ được chọn 1 lần (đó là lý do có tên gọi 0/1 - Không lấy hoặc Lấy).*

**Phân tích & Xây dựng công thức truy hồi:**
Nếu dùng phương pháp duyệt trâu (Brute Force) thử mọi tổ hợp, độ phức tạp sẽ là `O(2^n)`, cực kỳ chậm và không thể chạy nổi nếu `n` lớn. Thay vào đó, ta dùng Quy hoạch động.

Ta gọi `DP[i][j]` là **giá trị lớn nhất** có thể đạt được khi xét `i` đồ vật đầu tiên, với sức chứa tối đa của túi lúc này là `j`.
Khi đứng trước đồ vật thứ `i`, tên trộm có 2 lựa chọn:

1. **Không lấy đồ vật i:** (Do túi không đủ chỗ chứa `w_i` hoặc cố tình không lấy). Khi đó, giá trị túi không đổi, bằng với việc chỉ xét `i-1` đồ vật trước đó. 
   👉 `DP[i][j] = DP[i-1][j]`
2. **Lấy đồ vật i:** (Đảm bảo `w_i <= j`). Lúc này ta nhận được giá trị `v_i`, nhưng sức chứa của túi phải giảm đi `w_i`. Giá trị còn lại của túi sẽ là giá trị tối ưu khi xét `i-1` đồ vật với sức chứa `j - w_i`.
   👉 `DP[i][j] = DP[i-1][j - w_i] + v_i`

**Công thức truy hồi cuối cùng:**
`DP[i][j] = max(DP[i-1][j], DP[i-1][j - w_i] + v_i)`

> `[GỢI Ý CHÈN ẢNH HTML]:` Chèn một hình ảnh vector (SVG) minh họa một chiếc balo có ghi "W=5kg" và xung quanh là các món đồ vật kèm theo thông số Trọng lượng (Weight) / Giá trị (Value).

---

## 3. Bảng phương án (DP Table) - Trái tim của bài toán

*(Ghi chú cho lập trình viên Web: Hãy chuyển bảng Markdown dưới đây thành cấu trúc `<table class="dp-table">`, `<thead>`, `<tbody>`, `<tr>`, `<th>`, `<td>` trong file HTML. Bạn có thể sử dụng pseudo-class `:hover` của CSS trên thẻ `<tr>` để làm sáng từng hàng khi người dùng đọc).*

Giả sử ta có sức chứa túi **W = 5**. Có 4 đồ vật (n = 4) với thông số sau:
- Đồ vật 1: `w=2, v=3`
- Đồ vật 2: `w=3, v=4`
- Đồ vật 3: `w=4, v=5`
- Đồ vật 4: `w=1, v=2`

Chúng ta sẽ xây dựng ma trận `DP[i][j]` với `i` từ 0 đến 4 (hàng) và `j` từ 0 đến 5 (cột).

| i (Đồ vật xét) \ j (Sức chứa) | j = 0 | j = 1 | j = 2 | j = 3 | j = 4 | j = 5 | Giải thích tính toán nổi bật |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :--- |
| **0** (Không có đồ vật) | 0 | 0 | 0 | 0 | 0 | 0 | Khởi tạo bảng gốc, không có đồ = 0. |
| **1** (`w=2, v=3`) | 0 | 0 | 3 | 3 | 3 | 3 | Sức chứa >= 2 bắt đầu chứa được vật 1 (Giá trị 3). |
| **2** (`w=3, v=4`) | 0 | 0 | 3 | 4 | 4 | 7 | Tại `j=5`: max(DP[1][5], DP[1][5-3] + 4) = max(3, 3+4) = 7. Lấy cả vật 1 & 2. |
| **3** (`w=4, v=5`) | 0 | 0 | 3 | 4 | 5 | 7 | Tại `j=4`: max(DP[2][4], DP[2][0] + 5) = max(4, 5) = 5. Đổi vật 2 lấy vật 3. |
| **4** (`w=1, v=2`) | 0 | 2 | 3 | 5 | 6 | 7 | Tại `j=4`: max(DP[3][4], DP[3][3] + 2) = max(5, 4+2) = 6. Lấy vật 2 & vật 4. |

Kết quả tối ưu của bài toán nằm ở ô cuối cùng ở góc dưới bên phải: **DP[4][5] = 7** (Tổng giá trị lớn nhất).

---

## 4. Code Lời giải (C++ Implementation)

Việc dịch bảng phương án trên sang code thực sự rất ngắn gọn nhờ sức mạnh của vòng lặp `for`. Đây là cấu trúc code chuẩn mực cho bài toán Cái túi.

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

// Hàm giải quyết bài toán Cái túi 0/1 bằng Quy hoạch động
int knapsack01(int W, vector<int>& w, vector<int>& v, int n) {
    // Khởi tạo DP Table: (n+1) hàng và (W+1) cột, giá trị ban đầu là 0
    vector<vector<int>> dp(n + 1, vector<int>(W + 1, 0));

    // Bắt đầu điền bảng phương án Bottom-Up
    for (int i = 1; i <= n; i++) {
        for (int j = 1; j <= W; j++) {
            if (w[i - 1] <= j) {
                // Nếu túi chứa được vật i: So sánh 2 trường hợp Lấy và Không Lấy
                dp[i][j] = max(dp[i - 1][j], dp[i - 1][j - w[i - 1]] + v[i - 1]);
            } else {
                // Nếu vật quá nặng, không thể lấy: Kế thừa kết quả hàng trên
                dp[i][j] = dp[i - 1][j];
            }
        }
    }
    
    // Kết quả tối ưu luôn nằm ở ô cuối cùng của ma trận
    return dp[n][W];
}

int main() {
    int W = 5; // Sức chứa túi
    vector<int> w = {2, 3, 4, 1}; // Trọng lượng đồ vật
    vector<int> v = {3, 4, 5, 2}; // Giá trị đồ vật
    int n = w.size();

    cout << "Gia tri lon nhat co the lay duoc la: " << knapsack01(W, w, v, n) << endl;
    return 0;
}
```
## 5 Bài Tập Vận Dụng
![Image 2 Placeholder](../../images/algorithms/Bai_2_HSG12_TPHCM_2526.jpg)
## 6Tổng kết
Quy hoạch động không phải là một thuật toán cụ thể có thể chép y nguyên từ bài này sang bài khác. Nó là một **hệ tư tưởng**. Việc làm chủ được Quy hoạch động (nhìn ra được công thức truy hồi và vẽ được bảng phương án) chính là bước chuyển mình từ một Coder bình thường trở thành một Kỹ sư thuật toán thực thụ.