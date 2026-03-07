# 🕸️ Thuật toán: Một vài bài toán Lý thuyết đồ thị rối não

**Chuyên mục:** Thuật toán (Algorithms) | **Dự án:** Cow IT Wiki

Nếu ví Lập trình viên như những kiến trúc sư, thì Cấu trúc dữ liệu là vật liệu xây dựng, còn Thuật toán chính là "Bản vẽ kỹ thuật". Trong thế giới bản vẽ đó, **Lý thuyết đồ thị (Graph Theory)** nổi lên như một hệ thống "kinh mạch" phức tạp, trừu tượng và cũng "hại não" nhất, chi phối từ Google Maps, mạng xã hội Facebook cho đến cách Internet vận hành.

---

## 1. Lý thuyết đồ thị là gì? Sự vĩ đại của việc "Gạt bỏ chi tiết thừa"

Lý thuyết đồ thị là một nhánh của toán học rời rạc và khoa học máy tính, chuyên nghiên cứu về các mạng lưới kết nối. Trái với chữ "đồ thị" (Graph) thường làm ta liên tưởng đến trục tọa độ Oxy hay biểu đồ hình tròn trong môn Toán, Đồ thị ở đây mang ý nghĩa hoàn toàn khác: **Sự kết nối giữa các thực thể**.

> *"Bản chất của vũ trụ không nằm ở bản thân các vật thể, mà nằm ở cách chúng kết nối với nhau."* – Triết lý này mô tả chính xác 100% bản chất của Lý thuyết đồ thị.

Môn học này ra đời một cách đầy tình cờ vào thế kỷ 18 tại thành phố Königsberg (Phổ). Người dân ở đây có một câu đố rảnh rỗi: *"Làm sao để đi dạo qua đúng 7 cây cầu của thành phố, mỗi cầu đi đúng 1 lần và trở về điểm xuất phát?"*. Suốt nhiều năm, cả thành phố bế tắc.

Cho đến khi nhà toán học thiên tài Leonhard Euler xuất hiện. Thay vì đi thử nghiệm thực tế, ông làm một việc chưa ai từng làm: **Gạt bỏ mọi chi tiết thừa**. Ông nhận ra kích thước hòn đảo hay độ dài cây cầu không quan trọng. Thứ duy nhất quan trọng là **các điểm giao cắt (Đỉnh)** và **sự kết nối (Cạnh)**. Bằng cách vẽ các hòn đảo thành các "dấu chấm" và cầu thành "đoạn thẳng", Euler đã chứng minh bài toán là vô nghiệm. Ngay lúc đó, Lý thuyết đồ thị ra đời!

Một Đồ thị (Graph) luôn được định nghĩa bằng $G = (V, E)$, trong đó:
1. **Đỉnh (Vertex - V):** Là các thực thể độc lập. Có thể là một ngã tư đường, một máy tính, hoặc một tài khoản Facebook cá nhân.
2. **Cạnh (Edge - E):** Là mối liên kết giữa 2 Đỉnh. Nếu là đường 2 chiều (bạn bè Facebook), ta gọi là *Đồ thị vô hướng*. Nếu là đường 1 chiều (Follow trên Instagram), ta gọi là *Đồ thị có hướng*.

> `[GỢI Ý CHÈN ẢNH HTML]:` Tại vị trí này, bạn nên dùng thẻ `<img>` chèn một bức ảnh chia đôi: Một bên là bản đồ cổ điển 7 cây cầu Königsberg, một bên là mô hình đồ thị trừu tượng hóa (các chấm và đường thẳng) mang phong cách Cyberpunk (Màu #1230AE và #C68FE6). Đặt class CSS `.img-zoom-hover`.
![Image 1 Placeholder](../../images/algorithms/7-bridges-of-konigsberg.jpg)
---

## 2. Phân tích bài toán kinh điển: Tìm đường đi ngắn nhất (Shortest Path)

Để thấy rõ độ "rối não" nhưng đầy ma lực của Đồ thị, chúng ta cùng đến với một bài toán kinh điển trong điều hướng mạng lưới: **Bài toán Tìm đường đi ngắn nhất**.

**Đề bài:**
Bạn đang ở ngã tư `S` (Source) và muốn đi đến ngã tư `D` (Destination) trong một thành phố có `N` ngã tư. Giữa các ngã tư có các con đường nối nhau, mỗi con đường tốn một thời gian di chuyển khác nhau gọi là **Trọng số (Weight)**. Làm sao để tìm ra lộ trình từ `S` đến `D` tốn ít thời gian nhất?

**Phân tích & Giải thuật Dijkstra:**
Nếu dùng phương pháp duyệt trâu (Brute Force) tìm mọi con đường từ S đến D rồi so sánh, độ phức tạp sẽ bùng nổ thành `O(N!)`, siêu máy tính cũng phải "đứng hình". Thay vào đó, ta dùng **Thuật toán Dijkstra** (phát minh năm 1956).

Dijkstra thuộc họ thuật toán Tham lam (Greedy). Nguyên lý cốt lõi của nó nằm ở một thao tác gọi là **Lan truyền (Relaxation)**.
Ta gọi `dist[u]` là khoảng cách ngắn nhất từ đỉnh gốc `S` đến đỉnh `u`.
Khi ta đứng ở đỉnh `u` và nhìn sang đỉnh hàng xóm `v` (được nối bởi cạnh có trọng số `w`), ta tự hỏi: *"Liệu đi từ S đến u, rồi từ u đi thêm đoạn w đến v, có nhanh hơn con đường hiện tại đang ghi nhận đến v không?"*

**Công thức Relaxation kinh điển:**
Nếu `dist[u] + w < dist[v]` thì cập nhật: `dist[v] = dist[u] + w`

> `[GỢI Ý CHÈN ẢNH HTML]:` Chèn một hình ảnh vector (SVG) minh họa một Đồ thị có trọng số gồm 5 đỉnh (A, B, C, D, E) với các mũi tên và con số chi phí trên từng đoạn đường.
![Image 3 Placeholder](../../images/algorithms/dijkstra.png)
---

## 3. Bảng chạy tay (Trace Table) - Trái tim của thuật toán

*(Ghi chú cho lập trình viên Web: Hãy chuyển bảng Markdown dưới đây thành cấu trúc `<table class="graph-table">`, `<thead>`, `<tbody>`, `<tr>`, `<th>`, `<td>` trong file HTML. Sử dụng pseudo-class `:hover` của CSS trên thẻ `<tr>` để làm sáng từng hàng khi người dùng tra cứu các bước chạy thuật toán).*

Giả sử ta có đồ thị 5 đỉnh (0, 1, 2, 3, 4). Đỉnh gốc xuất phát là **0**.
Các cạnh và trọng số: `(0->1: 4)`, `(0->2: 1)`, `(2->1: 2)`, `(1->3: 1)`, `(2->3: 5)`, `(3->4: 3)`.

Ban đầu, khoảng cách tới chính đỉnh 0 là `0`, khoảng cách tới mọi đỉnh khác là `Vô cực (∞)`. Bảng dưới đây mô phỏng quá trình Dijkstra "lan truyền" (Greedy chọn đỉnh có `dist` nhỏ nhất chưa duyệt):

| Bước (Chọn đỉnh gần nhất) | dist[0] | dist[1] | dist[2] | dist[3] | dist[4] | Giải thích thao tác Relaxation (Cập nhật) |
| :--- | :---: | :---: | :---: | :---: | :---: | :--- |
| **Khởi tạo** | **0** | ∞ | ∞ | ∞ | ∞ | Bắt đầu. Chỉ biết mỗi đường đi đến chính nó (0). |
| **Duyệt Đỉnh 0** (dist=0) | 0 | 4 | **1** | ∞ | ∞ | Từ 0 đi tới 1 tốn 4, đi tới 2 tốn 1. Cập nhật `dist[1]=4`, `dist[2]=1`. |
| **Duyệt Đỉnh 2** (dist=1) | 0 | **3** | 1 | **6** | ∞ | (Đỉnh 2 đang nhỏ nhất). Từ 2 đi tới 1 tốn 2 -> Tổng là 1+2=3 < 4 (Cập nhật `dist[1]=3`). Từ 2 đi tới 3 tốn 5 -> Tổng là 1+5=6 (Cập nhật `dist[3]=6`). |
| **Duyệt Đỉnh 1** (dist=3) | 0 | 3 | 1 | **4** | ∞ | (Đỉnh 1 đang nhỏ nhất). Từ 1 đi tới 3 tốn 1 -> Tổng là 3+1=4 < 6. Cập nhật `dist[3]=4`. |
| **Duyệt Đỉnh 3** (dist=4) | 0 | 3 | 1 | 4 | **7** | (Đỉnh 3 đang nhỏ nhất). Từ 3 đi tới 4 tốn 3 -> Tổng là 4+3=7. Cập nhật `dist[4]=7`. |
| **Duyệt Đỉnh 4** (dist=7) | 0 | 3 | 1 | 4 | 7 | 4 không có đường đi tiếp. Thuật toán kết thúc! |

Kết quả: Từ 0 đến 4 ngắn nhất tốn **7 đơn vị** (Lộ trình tối ưu: 0 -> 2 -> 1 -> 3 -> 4).

---

## 4. Code Lời giải (C++ Implementation)

Để Dijkstra đạt tốc độ siêu tốc $O(E \log V)$, các "pháp sư code" luôn sử dụng **Hàng đợi ưu tiên (Priority Queue)** để mỗi lần lấy ra "đỉnh gần nhất" chỉ mất chi phí logarit.

```cpp
#include <iostream>
#include <vector>
#include <queue>

using namespace std;
const int INF = 1e9; // Khởi tạo khoảng cách là Vô cực

// Hàm cài đặt thuật toán Dijkstra
void dijkstra(int start, int n, vector<vector<pair<int, int>>>& graph) {
    // Mảng lưu khoảng cách ngắn nhất, ban đầu gán bằng INF
    vector<int> dist(n, INF); 
    
    // Min-Heap {khoảng cách, đỉnh}: Đỉnh có khoảng cách nhỏ nhất luôn trồi lên đầu
    priority_queue<pair<int, int>, vector<pair<int, int>>, greater<pair<int, int>>> pq;
    
    // Bước 1: Khởi tạo đỉnh xuất phát
    dist[start] = 0;
    pq.push({0, start});
    
    while (!pq.empty()) {
        int d = pq.top().first;  // Khoảng cách hiện tại
        int u = pq.top().second; // Đỉnh đang xét
        pq.pop();
        
        // Nếu tìm được đường khác ngắn hơn trong lúc chờ ở queue thì bỏ qua
        if (d > dist[u]) continue;
        
        // Bước 2: Lan truyền (Relaxation) sang các hàng xóm v
        for (auto edge : graph[u]) {
            int v = edge.first;
            int weight = edge.second;
            
            // Công thức Cập nhật cốt lõi
            if (dist[u] + weight < dist[v]) {
                dist[v] = dist[u] + weight;
                pq.push({dist[v], v});
            }
        }
    }
    
    // In kết quả mảng dist
    cout << "Khoảng cách từ đỉnh " << start << " den cac dinh con lai:\n";
    for(int i = 0; i < n; i++) cout << "Dinh " << i << ": " << dist[i] << "\n";
}

int main() {
    int n = 5; // Số đỉnh (0 đến 4)
    vector<vector<pair<int, int>>> graph(n);
    // Add edges: graph[u].push_back({v, weight});
    graph[0].push_back({1, 4}); graph[0].push_back({2, 1});
    graph[2].push_back({1, 2}); graph[1].push_back({3, 1});
    graph[2].push_back({3, 5}); graph[3].push_back({4, 3});

    dijkstra(0, n, graph);
    return 0;
}
```

## 5. Bài Tập Vận Dụng

> `[GỢI Ý CHÈN ẢNH HTML]:` Chèn một hình ảnh đề thi Học sinh giỏi Tin học thực tế (Ví dụ bài toán tìm đường đi thoát khỏi mê cung, bài toán giao thông đô thị có tính chất Đồ thị).

![Image 2 Placeholder](../../images/algorithms/Bai_3_HSG12_TPHCM_2526_1.jpg)
![Image 2 Placeholder](../../images/algorithms/Bai_3_HSG12_TPHCM_2526_2.jpg)

## 6. Tổng kết

Lý thuyết đồ thị không chỉ là những thuật toán khô khan như Dijkstra, BFS, DFS hay Kruskal. Nó là một **cách nhìn nhận thế giới**. Việc làm chủ được cách trừu tượng hóa một vấn đề thực tế (ví dụ: một bàn cờ vua, một sơ đồ tổ chức công ty, một hệ thống mạng LAN) thành các Đỉnh và Cạnh chính là bước chuyển mình từ một Coder gõ phím cơ học trở thành một Kỹ sư Thiết kế Hệ thống (System Designer) thực thụ.