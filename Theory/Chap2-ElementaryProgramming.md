# Scanner & Nummeric data type

### 💦 How to use Scanner to prompt user to enter input from keyboard:
1. Import Scanner class:
```java
   import java.util.Scanner;
```
Scanner là một class nằm trong gói java.util, là một gói thư viện của java chứa các hàm ultilities

2. Create Scanner class instance:
```java
Scanner scanner = new Scanner(System.in);
```
3. Prompt user to enter data:
```java
System.out.print("Enter your data: ");
```
Data từ user console thông thường là primitive data type như number, string, boolean. Các kiểu dữ liệu khác như object, blob, image, binary thì có thể dùng các class InputStream trong java.io

4. Read user data from scanner:<br>

Tuỳ kiểu dữ liệu, sử dụng các hàm tương ứng để đọc primitive data:<br>
VD double => scanner.nextDouble(), int => scanner.nextInt();

Lưu ý: khi gọi hàm nextLine() sau hàm nextInt(), kết quả của nextLine() sẽ là một chuỗi rỗng. Lý do vì nextLine() đọc kí tự "\n" khi user gõ Enter.

Fixed bằng cách sử dụng ```scanner.skip(“[\r\n]+")``` ngay sau dòng nextInt(), truyền vào một RegExp thì scanner sẽ skip kí tự "\n".

5. Handle user data:

Note: Khi sử dụng nextInt(), nextLine(),... để đọc data từ user, java block luồng code đang chạy và đợi cho tới khi nào user nhập data. Có thể set time vd sau 1' user không có động thái gì, thì thông báo ra màn hình rồi terminate program.

6. Close scanner:
```java
scanner.close()
```
Khi làm việc với file và network, luôn luôn đóng connection sau khi đã xong chuyện để release resource.

### 💦 static typed
tuyên ngôn của Java là 'strongly static typed', static typed có nghĩa là kiểu dữ liệu sẽ được xác định ngay tại thời điểm biên dịch và không thay đổi, để tránh cast từ loại object này sang loại object khác, vd cast từ People qua Dog là không được)

Khai báo biến = với khai báo kiểu dữ liệu mà biến đó có thể lưu trữ (cấp phát bộ nhớ).



### 💦 Numeric Data Type
| Name   | Range            | Storage Size    |
|--------|------------------|-----------------|
| byte   | -2^7 to 2^7-1    | 8-bit signed    |
| short  |-2^15 to 2^15 -1 | 16-bit signed   |
| int    | -2^31 to 2^31 - 1 | 32-bit signed   |
| long   | -2^63 to 2^63 - 1 | 64-bit signed   |
| float  |                  | 32-bit IEEE 754 |
| double |                  | 64-bit IEEE 754 |

#### Signed Bit
```java
VD: byte b = 8;
```
- binary format là 00001000
- được lưu trữ bằng 8 bit, bit đầu tiên là bit dấu (0 là số dương, 1 là số âm)
- để biểu diễn giá trị âm của b, thay bit đầu tiên thành 1 => binary là 10001000
- bởi vì bit đầu tiên được lấy làm bit dấu, nên signed byte chỉ có range từ -2^7 tới 2^7-1. Tương tự cho short, int, long
- Khai báo binary trong java:
```java
int binaryNumber = 0b1000;
```

#### Unsigned Bit
Java không hỗ trợ unsigned bit, nhưng unsigned bit hiểu đơn giản là không có bit dấu. Nên nó có có thể biểu diễn giá trị từ 0 tới 2^n (255 giá trị cho kiểu byte). 

#### Tràn số:
VD integer có range là -2^31 tới 2^31-1, giá trị maximum mà int có thể biểu diễn là 2147483647, nếu gán một giá trị vượt quá dung lượng, sẽ gây nên tràn số.

```agsl
int x = 2147483647 + 1; // or int x = 2147483648
```
thì x sẽ trở thành -2^31 (tức -2147483648)

### 💦 Assignment statement:
VD1:
```java
int x = 6/2.0;
```

+ ```x``` là variable (variable là những gì bên trái dấu bằng)
+ ```6/2.0``` là expression (biểu thức)
+ ```int x = 6/2.0``` là 1 phép gán (assignment): gán giá trị của expression 6/2.0 vào biến x <br/>

=> Trong java, kiểu dữ liệu của expression bắt buộc chuyển về cùng kiểu dữ liệu với biến bên trái, vd ```int x = 1.0``` là không hợp lệ vì data type của x là int còn data type của expression là double.  <br>
=> Kết quả của ```6/2.0=3.0```, kết quả này có kiểu dữ liệu là double. Double không thể cast ngầm về kiểu int do có mất dữ liệu nên đoạn code ```int x = 6/2.0``` sẽ bị compile error <br>
Fixed: ```int x = (int) (6/2.0)``` => casting kết quả expression về kiểu int, sẽ có mất dữ liệu

VD2: 
```java 
double x = 6/2
``` 

=> kết quả của expression trả về int, vì là chuyển đổi từ datatype int có độ lớn nhỏ hơn double nên có thể cast ngầm được


### 💦 Default:
Java lấy default cho số nguyên là int, và default cho số thực là double <br>
4 -> kiểu int <br>
4.0 -> kiểu double <br>
4L or 4l -> kiểu long <br>
4f or 4F -> kiểu float <br>

