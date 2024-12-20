## Xác định các phần tử thiết kế
### 1. Các phần tử thiết kế chính
**a. Các thành phần phần cứng (Hardware Components)**

**Cảm biến (Sensors):**

**Chức năng:**
- Thu thập dữ liệu môi trường như nhiệt độ, độ ẩm, áp suất không khí, tốc độ gió.
  
**Ví dụ:**
-  Cảm biến nhiệt độ (Thermometer), cảm biến độ ẩm (Hygrometer), cảm biến áp suất (Barometer).
  
**Bộ xử lý chính (Main Processor):**

**Chức năng:**
- Điều phối hoạt động của hệ thống, xử lý dữ liệu, thực thi các thuật toán phát hiện lỗi.
  
**Bộ nhớ tạm (Temporary Storage):**

**Chức năng:**
- Lưu trữ dữ liệu tạm thời trước khi xử lý hoặc truyền tải.
  
**Nguồn năng lượng (Power System):**

**Chức năng:**
- Cung cấp năng lượng, bao gồm tấm pin mặt trời, tua-bin gió và pin dự trữ.
  
**Hệ thống truyền thông vệ tinh (Satellite Communication Module):**

**Chức năng:**
-Truyền tải dữ liệu từ hệ thống tới trung tâm điều khiển từ xa.

**Mô hình hóa thành phần phần cứng:**

![Diagram](https://www.planttext.com/plantuml/png/V9DBReD038Rtd6AKLRF81LXKKTDANJHI9781bx78g8oDF8O8LJbP5prIhr0DZq0UBIl0zl_vjsT-lhxNGK6qzcLIGVu11Ph5AuWzWg3PiA-Oa3Gip6TYJ5v222P32YpTZ_XuX50BFeF2mp8Tel4hCUPqBjg2evrmZc5UcpEBTGIAMHiKVHHesDaXNFK5dRG5XRdwCZM37jeRsXvznGBIPieIFOt0e3oqskjTI5p21LKSDcTZVzDsV4Jf3KnJONBAqeNUiC6oa-WI5RGEPqX-02dm2LHHsYl_uUWqF-pvXL2ADeF6KR5bYxEqgOiC5ClIAMxO-vfS3kgOjcphSlAl0XIyqtz6yCvS8j3K8BgcqmIo4JoyTkp4ZATXjNgysd5g0f8D9b8ISnMCwJTBIllrX77lQCVY-OJlaIhXnjbO6HFlqluTpqMlfsIDPEED-0K00F__0m00)

**b. Các thành phần phần mềm (Software Components)**

**Bộ xử lý dữ liệu (DataProcessor):**

**Chức năng:**
- Xử lý dữ liệu thô từ các cảm biến, làm sạch dữ liệu và phát hiện các lỗi.
  
**Bộ phát hiện lỗi (ErrorDetectionModule):**

**Chức năng:**
- Phân tích dữ liệu để phát hiện bất thường hoặc lỗi hệ thống.
  
**Quản lý năng lượng (PowerManagementModule):**

**Chức năng:**
- Theo dõi và tối ưu hóa việc sử dụng năng lượng, chuyển hệ thống sang chế độ tiết kiệm năng lượng khi cần thiết.
  
**Quản lý lỗi (FaultManagementModule):**

**Chức năng:**
- Phát hiện và xử lý các lỗi trong hệ thống, kích hoạt cơ chế tự phục hồi (AutoReconfiguration).
  
**Bộ giao tiếp vệ tinh (SatelliteCommunication):**

**Chức năng:**
- Quản lý truyền tải dữ liệu qua vệ tinh tới trung tâm điều khiển.
  
**Hệ thống lưu trữ (StorageModule):**

**Chức năng:**
- Lưu trữ dữ liệu tạm thời hoặc dài hạn, đảm bảo dữ liệu không bị mất khi có sự cố.

  **Mô hình hóa thành phần phần mềm:**
  
  ![Diagram](https://www.planttext.com/plantuml/png/Z5DBJiD03Dtd51QhTi45Pe4gyLc1L54uW9anOKGoZcod5KKz6GkEn1NG9A6q9Qt8Ad7UP_pi-VhudAcXM5jNHOF-5Kk2imK_smg5u9BhXXCbqpDuBm1yXQfmXOPpOK-gB5qzFxuYJFdN9A2XWmKbPSc5gOC1JY5_3uIch_sNijdwNukmN96HjyZfZaDRqVOOcB1wMzEEwfxGrFNqUsfOR4zspYkIEqnOKat93dIviLZ7DNMeHyMI9bC7IuvX0EWgcdzvu5jUzKeSTY6_FZVOLdRK9tHzTHWT6jWvyDJ14tDEUe0BUKxFiMo55czgL8zQBj2eggBH9TTrcwB7dDpMqmIJrj5EXFR7bUAoKyCKikNmkkzgB5ZIGODgBAV6inEfa4caPOyUNOa23hRn_FnYV3_SpxwHGZOkO1oN1SOdv42w6IXG9ce1HrRcb4HCHeBUCdiSazb7vkL0AGM5jWbeb2N-DhyVkklZrlvsKkXRtnGpIY5V-My0003__mC0)
  
  
### 2. Tổ chức các phần tử thiết kế
**Hệ thống được tổ chức theo kiến trúc phân lớp (Layered Architecture), bao gồm các lớp chính:**

**Lớp phần cứng (Hardware Layer):**
- Bao gồm các cảm biến, bộ xử lý chính, nguồn năng lượng và module truyền thông vệ tinh.
  
**Lớp xử lý dữ liệu (Data Processing Layer):**
- Gồm các module xử lý dữ liệu, phát hiện lỗi, và quản lý năng lượng.
  
**Lớp giao tiếp (Communication Layer):**
- Bao gồm các thành phần liên quan đến truyền tải dữ liệu qua vệ tinh.
  
**Lớp lưu trữ (Storage Layer):**
- Quản lý bộ nhớ tạm và dữ liệu lưu trữ dài hạn.

  **Mô hình hóa Kiến trúc phân lớp**
  
  ![Diagram](https://www.planttext.com/plantuml/png/R5BDQiCm3BxxAKJlVO4UHikwiSC2XUm5XArcPh4TP8KGHfziXptINc5uIOgJ-MQaxq-IVxw-Zr6GfNUjwb1_O4EmUyMHc0oSMBzR8Iqzqmu-5S0Tye9i1cI2F-pK1D0jnWWr-HWuArHe_OM3fhYkNy90N8zHoELq56fRA_GOdEkzrIWs-2gOlYK5SCjZd54GPcdhcrAQ12cPFp47FbCQBvTVsi_OjrAXnuOSUIdRhn8MLr6SPIjJI-3qA0YyaUi28uyp9jUUAbao1VFkORz_M0yE1uZaJGJ60GmAAjW04cNhbbWIc29q4uxCGlu7JVnL93Y0CFfu9OuBAxjuCMEN-dStwni5vKjCTiNjBhxEIeHh8a_kDtKaRz97_mK00F__0m00)
  
### 3. Các cơ chế thiết kế được sử dụng
**a. Cơ chế xử lý dữ liệu (Data Processing Mechanism)**
- Dữ liệu từ cảm biến được thu thập, làm sạch và xử lý để đảm bảo tính chính xác.
  
- Xử lý dữ liệu theo chu kỳ, giảm tải cho hệ thống khi năng lượng thấp.

  **Mô hình hóa Cơ chế xử lý dữ liệu**
  
  ![Diagram](https://www.planttext.com/plantuml/png/T94nRiCm301tlOB8L0_vW8OYGzS01Jnq9YH2CM990Kad20g_h4EVr2yKYcKZDX1kedZaKVhx-Js88kiGUtD1TyP0iFj0HVZax4YaIm6Ev4wOEeax-3O0haSHQ2b9vaUYH2IKWQcWRusjj-La0CO5AedQ-8brFM5wa1uLd-76pXxaQxCI609JGALNq1UXdeZR8KRa-qgXrSmOw9ZzqDEY89gh_DHjDRMnSCsThwLCoXrTbrMtWgCnCB_EVl--sTc2KF82Z3Seemni2WgoThIJdS1bdZIHepbGykNd_W400F__0m00)
  
**b. Cơ chế phát hiện lỗi (Error Detection Mechanism)**
- Các thuật toán phân tích dữ liệu được áp dụng để phát hiện bất thường.
  
- Phân biệt lỗi phần cứng (như cảm biến hỏng) và lỗi dữ liệu.

**Mô hình hóa Cơ chế phát hiện lỗi**

![Diagram](https://www.planttext.com/plantuml/png/R951JiCm44NtFiMegsJH2tY1kYZi8Y5wWY7-b0Z74tcSIe1wCXOSYIiWEo4YLRomv3ypx-kFVxw-3veufh7tPk3sZS-WtNsC4kc8X3Pr4gX1-ygXqtv7duQezQnAHqxy6AM5giIYvpDCIYvMZXDREY6en2pKbkO1kFmsHDS5LpmNoqRSwB5GER1__y0_wWfKssdy2OF4jC8-yEXJmu7Fw17I3TSLlzAZLIpJArHj9y3S7g7YBoXIzPBlkLvRUXRnu53C3TriPx-_smveyy8kdOF-RGwESa93smEPj9t9aY8u9PJFcyAekPe3Wik_-mi00F__0m00)

**c. Cơ chế quản lý năng lượng (Power Management Mechanism)**
- Theo dõi mức năng lượng và tự động chuyển đổi chế độ hoạt động (tiết kiệm năng lượng khi pin yếu).
  
- Ưu tiên cung cấp năng lượng cho các thành phần thiết yếu.

  **Mô hình hóa Cơ chế quản lý năng lượng**
  
  ![Diagram](https://www.planttext.com/plantuml/png/Z9112i9034NtFKNeIXTUe0iHroq8wW529zJ1pgHCqXOLJ-R28ta5wLYqBWIpJ5x-_ydZTb-9Oj3MrKc3vH4hWdJ3FGKeq6D5Zhn2GUK1lHMNmYK1A6iKWKXjJwBaOdSenzugXpZAgQDwDiz6K55R6R4mw8MArgXAuJH07LipJgMtMXvsd7CVLmisD46ktma-CGisRKtlBDoeTVPCaTeBLbEHltmI-3foiLZ-iCn0o1k19ZvENgTUanLvCpps2G00__y30000)
  
**d. Cơ chế tự phục hồi (Auto-Reconfiguration Mechanism)**
- Khi lỗi được phát hiện, hệ thống sẽ tự động tái cấu hình để tiếp tục hoạt động.
  
**Ví dụ:**
- Ngắt cảm biến bị lỗi và sử dụng các cảm biến dự phòng nếu có.

**Mô hình hóa Cơ chế tự phục hồi**

![Diagram](https://www.planttext.com/plantuml/png/b591JWCn3Bpd5LPFkuT-80TKKE5M2RKlC8ctHCqcLUnKAgWluy2J-09AThjIqO94RixOCvv9lZu-LooO9FTU7T4SS4-mkCyIbrioCNHkdnEAYm4sP5unEEuNyAu0Z4TcUCBiPOC1zzHJa4sqsLF5ox4aPAJsS9Fe69DeU4mffcqjMZqGZErfKgJTcONwfYlesDHgE4Ld5S1bajzHu9WclPwGSw8r2ZQj7j5INVTnZ2-UcZcg1pI7VFmd8Hfn9vHvncfqNIDmCVo81WFwyzl0R55GmtEAXfZ9bhls9gTAg-2Nj9VBksiGUeoSeIRtvyYDOJrPON0TzEW2y01rw3mhcBTJYEObT9ct35J6O7XyLXUrec3BP_i6003__mC0)
  
**e. Cơ chế truyền thông (Communication Mechanism)**
- Dữ liệu được truyền qua vệ tinh theo lô để tiết kiệm năng lượng.
  
- Hỗ trợ truyền dữ liệu ưu tiên cao (báo cáo lỗi) khi có sự cố khẩn cấp.

  **Mô hình hóa Cơ chế truyền thông**
  
  ![Diagram](https://www.planttext.com/plantuml/png/Z911Qa9138RtSuhWIXTUu2sAKEdkGMbFy3iJxT2PZ4potCWxcGkFv1NAFEI92w5PXV0bNvBRvRfHGxKX9tU4_yM1QV5USXuaUbWiGZtx7qZKlA2p8_89glGDuvIYyJFRW1PM8PgZRM5O1XWw-gp5iog7Lbjrj2ibCUJUKDbpF4tJ866vwkYUEg9njdvWIDP3SE3COdq9G-9P6jZOsyJelwJA4YRyYu-bMhC-WD4vUY5ShzzUFQ2RJrVQjsPgYxZHRLX2U_8V0000__y30000)
  
**f. Cơ chế lưu trữ (Storage Mechanism)**
- Dữ liệu được lưu trữ tạm thời nếu kết nối vệ tinh bị gián đoạn.
  
- Cơ chế nén dữ liệu được áp dụng để tối ưu hóa bộ nhớ.

****Mô hình hóa Cơ chế lưu trữ**

![Diagram](https://www.planttext.com/plantuml/png/j90n2i9044NxESMGoXIvG0f9OHiGz0B3xgZ191jc9e4GSZ8BZ-GLP3LQnDgfFfy7Zp-FsxrG8x6-gQ4ZTwKpOtAm836Kx2xKLjeaE06YgqaLZznqGKZ63pK1lauj2E_8QEF9ACUz1CUgx6ENvZY4oY-ei4d5mvjELoWWpb_R8Yc3x-i_gG1_DsNPTgNEqOHQFR4eHYdCK73huz-U0000__y30000)
