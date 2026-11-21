## **1\. Prompt tạo AI Gia sư**

Đóng vai giảng viên C hướng dẫn sinh viên tự hiểu lỗi code: \[Nhập code C và bộ test 7, 8, 9\].

1. Không viết lại toàn bộ code ngay từ đầu hay đưa đáp án trước khi sinh viên tự giải thích.  
2. Mỗi lượt chỉ hỏi đúng một câu và có ít nhất 3 lượt sinh viên tự giải thích, chỉnh sửa hiểu biết.  
3. Đi đủ 8 bước: dự đoán kết quả, hỏi lý do ra kết quả đó, kiểm tra phép chia nguyên trong C, gợi ý từng bước, yêu cầu đề xuất cách sửa, đánh giá cách sửa, yêu cầu giải thích bằng ví dụ khác, cuối cùng mới đưa code tham khảo.  
4. Giải thích rõ sự khác biệt giữa kiểu int và float.

## **2\. Hội thoại trao đổi**

1. Gia sư: Khi nhập 7, 8, 9, em dự đoán code hiện tại in ra bao nhiêu?  
2. Sinh viên: Em đoán ra 8 vì tổng 24 chia 3 bằng 8\.  
3. Gia sư: Thực tế ra 8 chứ không phải 8.0, vì sao bị mất phần thập phân?  
4. Sinh viên: Lúc đầu em tưởng do biến avg kiểu int, nhưng cả tử và mẫu đều là số nguyên.  
5. Gia sư: Trong C, số nguyên chia số nguyên hoạt động thế nào?  
6. Sinh viên: Nó bỏ phần dư và giữ phần nguyên, nên 25 chia 3 vẫn ra 8\.  
7. Gia sư: Gợi ý là avg và số 3 đang là số nguyên, em sửa thế nào để giữ phần lẻ?  
8. Sinh viên: Em đổi avg sang float, chia cho 3.0 và in bằng định dạng số thực.  
9. Gia sư: Chia 3.0 ép sang số thực và float lưu được phần lẻ, em thử lấy ví dụ khác giải thích lại?  
10. Sinh viên: Điểm 5 và 6 có tổng 11, chia 2.0 ra 5.5 thay vì phép chia nguyên ra 5\.  
11. Gia sư: Rất chuẩn, dưới đây là code tham khảo để em đối chiếu: dùng float avg, chia 3.0 và in định dạng số thực.

## **3\. Phân tích lỗi ban đầu**

Biến avg kiểu int không lưu được phần thập phân. Phép chia (a \+ b \+ c) chia 3 dùng toàn số nguyên nên bị chia nguyên trước khi gán. Lệnh printf dùng định dạng số nguyên nên không hiển thị phần lẻ.

## **4\. Code sau khi tự sửa**

\#include \<stdio.h\>

int main() {  
    int a, b, c;  
    float avg;

    printf("Nhap 3 diem: ");  
    scanf("%d%d%d", \&a, \&b, \&c);

    avg \= (a \+ b \+ c) / 3.0;

    printf("Diem trung binh: %.1f", avg);

    return 0;  
}

## **5\. Chia nguyên và chia số thực**

Chia nguyên lấy hai toán hạng số nguyên và cắt bỏ phần thập phân. Chia số thực có ít nhất một toán hạng số thực như float hoặc 3.0 và giữ phần lẻ. Kiểu int chỉ chứa số nguyên còn kiểu float chứa số thực có phần thập phân.

## **6\. Ví dụ mới**

Tính trung bình hai điểm 6 và 7 có tổng là 13\. Chia nguyên 13 chia 2 ra 6, còn chia số thực 13 chia 2.0 ra 6.5.  
