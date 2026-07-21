---
title: "Blog 1"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---


# Ừ MỘT ĐỨA INTERN: KHI "USER" CỦA DATABASE LÀ AI AGENT CHỨ KHÔNG PHẢI CON NGƯỜI ĐỒNG LOẠI 


Dạo này em đang tập tành nghiên cứu về GenAI và AI Agent, hôm nay vô tình lướt được bài viết cực kỳ bánh cuốn trên AWS Partner Network Blog. Đọc xong em thấy "vỡ ra" nhiều tư duy mới về thiết kế hạ tầng nên em xin phép mổ xẻ lại theo góc nhìn của một đứa intern để chia sẻ và rất mong được các anh chị đi trước chỉ giáo thêm ạ!

Trước giờ làm mấy bài tập lớn ở trường, em cứ nghĩ database chỉ cần hứng request từ người dùng (gõ lệnh ➡️ bấm Submit ➡️ đợi trả kết quả) là xong. Tốc độ của con người thì có hạn nên traffic khá dễ thở. Nhưng bài blog này đã chỉ ra một thực tế hoàn toàn khác khi chúng ta chuyển sang thời đại của AI Agent tự trị (Autonomous Agents).

Khi này, "User" không còn là con người nữa mà là những cỗ máy chạy lặp liên tục (planning ➡️ executing ➡️ evaluating ➡️ revising). Tiện tay mình ra một lệnh như "Tối ưu hóa chuỗi cung ứng giùm anh", là ở dưới con AI Agent nó tự "vắt óc" sinh ra hàng ngàn câu lệnh SQL, tự tạo rồi xóa schema tạm thời liên tục trong vài giây để thử nghiệm.

Mấy anh tác giả (toàn SAs khủng của AWS với PingCAP) có chỉ ra 3 cái "đau đầu" chí mạng cho database truyền thống khi gặp case này:

Rác Metadata: Agent tạo/xóa bảng tạm vô tội vạ làm hệ thống dễ bị hụt hơi.

Traffic "co giật" thất thường: Vừa mới nghỉ ngơi (idle) xong, tích tắc sau đã nhảy lên chạy song song cực hạn (highly parallel) vì các Agent đồng loạt tổng hợp dữ liệu.

Bài toán kinh tế: Cấu hình tài nguyên cố định (fixed capacity) để phòng lúc Agent cao điểm thì lúc nó nghỉ, tiền cloud vẫn nhảy đều đều, xót ví doanh nghiệp lắm ạ.

Để giải quyết, họ đưa ra một Blueprint kết hợp giữa Amazon Bedrock (làm bộ não suy luận) và TiDB Cloud (tầng database co giãn). Em thấy cách họ thiết kế giải quyết mấy bài toán trên thông minh thực sự:

Lưu một nơi, tính một nẻo (Tách biệt Compute & Storage): Dữ liệu gốc nằm yên vị, an toàn trên Amazon S3, còn các node tính toán (Compute) thì tự động scale up khi Agent chạy nặng và tự động hạ xuống thấp nhất khi Agent nghỉ. Đúng kiểu dùng bao nhiêu trả bấy nhiêu, siêu tối ưu chi phí!

Database cũng "Git Branch" được luôn: Giống kiểu tụi em hay git branch để code tính năng mới, AI Agent có thể dùng tính năng Serverless Branching của TiDB Cloud để tạo riêng một nhánh DB độc lập, tha hồ test schema hay chạy thử nghiệm dữ liệu mà không sợ làm sập con Production. Xong việc xóa branch là xong, cực gọn.

Gom tất cả vào một (All-in-One DB): Thay vì một đứa intern như em phải đi mò mẫm dựng DB cho transaction (OLTP), rồi lại dựng thêm cái để phân tích (OLAP), rồi lại còng lưng cấu hình thêm con Vector DB riêng để làm RAG... thì TiDB Cloud nó thầu luôn cả 3 việc này trong một hệ thống duy nhất. Đỡ phân mảnh hạ tầng và giảm độ trễ tối đa cho AI luôn ạ. 

Trong bài họ cũng kể mấy use case thực tế "khét" lắm, như con game gì đấy ứng dụng cái này xử lý mượt mà hàng triệu player mà không cần phân mảnh database thủ công (manual sharding), hay nền tảng Forge của Atlassian scale tới hơn 3 triệu bảng trong một cluster duy nhất luôn. 

Em thì vẫn đang trong quá trình học hỏi và tích lũy kinh nghiệm, không biết ở đây có anh chị nào đã triển khai thực tế hệ thống AI Agent hay mô hình RAG dùng Amazon Bedrock kết hợp với TiDB Cloud (hoặc các dạng kiến trúc tương tự) chưa ạ? Anh chị đi trước cho em xin ít review hoặc lời khuyên với nha. 

Em cảm ơn các anh chị nhiều ạ!

Bài viết tham khảo..

https://aws.amazon.com/vi/blogs/apn/generative-ai-using-tidb-and-amazon-bedrock/

![Ảnh của bạn](/images/3-Blog/Blog1.jpg)