# Xác định các phần tử thiết kế
## 1. Xác định các lớp và các hệ thống con

**1. Các lớp chính trong hệ thống:**

**1.1. Lớp WeatherStation (Trạm thời tiết)**

#### Thuộc tính:

- stationID: ID duy nhất của trạm.
- location: Vị trí địa lý (kinh độ, vĩ độ).
- powerStatus: Trạng thái nguồn (mức pin, năng lượng mặt trời/wind generator hoạt động).
- communicationStatus: Trạng thái kết nối vệ tinh.
- sensorData: Bộ dữ liệu thu thập từ các cảm biến (tốc độ gió, hướng gió, nhiệt độ, áp suất, lượng mưa...).
- localStorage: Bộ nhớ cục bộ lưu dữ liệu khi mất kết nối.
  
#### Phương thức:

- collectData(): Thu thập dữ liệu từ các cảm biến.
- processData(): Xử lý và tổng hợp dữ liệu trước khi truyền.
- transmitData(): Truyền dữ liệu đã xử lý đến hệ thống quản lý.
- storeDataLocally(): Lưu dữ liệu cục bộ khi không thể truyền đi.
- monitorHardware(): Giám sát trạng thái phần cứng (cảm biến, truyền thông).
- managePower(): Quản lý nguồn năng lượng và sạc pin.
- reconfigureSystem(): Cấu hình lại hệ thống khi có thay đổi phần mềm hoặc lỗi phần cứng.

**1.2. Lớp Sensor (Cảm biến)**

#### Thuộc tính:

- sensorType: Loại cảm biến (nhiệt độ, áp suất, gió, mưa...).
- sensorID: ID duy nhất của cảm biến.
- dataFrequency: Tần suất đo lường.
- status: Trạng thái hoạt động của cảm biến.
  
#### Phương thức:

- readData(): Đọc dữ liệu thời tiết từ cảm biến.
- calibrate(): Hiệu chỉnh cảm biến.
- selfCheck(): Tự kiểm tra trạng thái hoạt động.
  
**1.3. Lớp PowerManagement (Quản lý nguồn)**

#### Thuộc tính:

- batteryLevel: Mức pin hiện tại.
- solarPanelStatus: Trạng thái tấm năng lượng mặt trời.
- windGeneratorStatus: Trạng thái máy phát gió.
  
#### Phương thức:

- chargeBattery(): Sạc pin từ nguồn năng lượng tái tạo.
- shutDownInStorm(): Tắt hệ thống khi điều kiện thời tiết nguy hiểm.
- optimizePowerUsage(): Tối ưu hóa tiêu thụ năng lượng.
  
**1.4. Lớp Communication (Truyền thông)**

#### Thuộc tính:

- satelliteLinkStatus: Trạng thái liên kết vệ tinh.
- bandwidth: Băng thông vệ tinh hiện có.
  
#### Phương thức:

- establishConnection(): Kết nối với vệ tinh.
- transmit(): Truyền dữ liệu đến hệ thống quản lý.
- retryTransmission(): Thử lại khi truyền thất bại.
  
**1.5. Lớp DataManagement (Quản lý dữ liệu)**

#### Thuộc tính:

- rawData: Dữ liệu thô từ cảm biến.
- processedData: Dữ liệu đã được xử lý.
- storageCapacity: Dung lượng lưu trữ cục bộ.
  
#### Phương thức:

- aggregateData(): Tổng hợp dữ liệu theo khoảng thời gian.
- compressData(): Nén dữ liệu để tối ưu truyền tải.
- clearOldData(): Xóa dữ liệu cũ để giải phóng dung lượng.
  
**1.6. Lớp Maintenance (Bảo trì)**

#### Thuộc tính:

- hardwareStatus: Tình trạng phần cứng.
- errorLogs: Nhật ký lỗi.
- softwareVersion: Phiên bản phần mềm hiện tại.
  
#### Phương thức:

- sendStatusReport(): Gửi báo cáo tình trạng đến hệ thống bảo trì.
- updateSoftware(): Cập nhật phần mềm.
- performDiagnostics(): Chạy chẩn đoán lỗi.
  
## **2. Quan hệ giữa các lớp:**

#### WeatherStation liên kết với nhiều Sensor:

- Mỗi trạm thời tiết bao gồm nhiều cảm biến để đo các thông số khác nhau.
  
#### WeatherStation sử dụng PowerManagement:

- Quản lý nguồn là một phần quan trọng của trạm thời tiết.
  
#### WeatherStation liên kết với Communication:

- Để giao tiếp với hệ thống quản lý và bảo trì qua vệ tinh.
  
#### WeatherStation liên kết với DataManagement: 

- Để xử lý, lưu trữ và truyền tải dữ liệu.
  
#### Maintenance liên kết với WeatherStation:

- Để theo dõi trạng thái và thực hiện các hoạt động bảo trì.

##  **3. Ánh xạ từ lớp phân tích đến các phần tử thiết kế**

 ### 1. Lớp WeatherStation
 
**Phân tích:**
- Trạm thời tiết là lớp chính, chịu trách nhiệm tổng hợp dữ liệu từ các cảm biến, xử lý dữ liệu, và quản lý giao tiếp với các hệ thống khác.
  
**Thiết kế:**
  
- Đảm bảo rằng lớp này hoạt động như bộ điều phối chính (Coordinator Class), tương tác với các lớp phụ trợ như Sensor, PowerManagement, Communication, và DataManagement.
  
- Sử dụng các mẫu thiết kế như Facade Pattern để cung cấp một giao diện thống nhất cho các chức năng của trạm.
  
**Chi tiết thiết kế:**
**Thuộc tính:**
- stationID: String
- location: Coordinates (Lớp con đại diện cho kinh độ/vĩ độ).
- powerManagement: PowerManagement
- communication: Communication
- sensors: List<Sensor>
- dataManager: DataManagement
  
**Phương thức:**
- collectData(): Điều phối việc lấy dữ liệu từ các cảm biến.
- transmitData(): Sử dụng Communication để gửi dữ liệu đã xử lý.
- handleFault(): Quản lý lỗi thông qua các phương thức của Maintenance.
  
### 2. Lớp Sensor
**Phân tích:**
- Các cảm biến đo các thông số thời tiết và cung cấp dữ liệu thô.
  
**Thiết kế:**
- Triển khai lớp trừu tượng (Abstract Class) Sensor để đại diện cho các loại cảm biến khác nhau, sau đó kế thừa để cụ thể hóa từng loại cảm biến.
- Mẫu thiết kế Strategy Pattern có thể được áp dụng nếu các cảm biến có cách xử lý dữ liệu khác nhau.

**Chi tiết thiết kế:**

**Lớp trừu tượng Sensor:**

**Thuộc tính:**

- sensorID: String
- sensorType: SensorType (Enum gồm: TEMPERATURE, PRESSURE, WIND_SPEED, v.v.).
- dataFrequency: int (Tần suất đo lường).
  
**Phương thức:**

- readData(): WeatherData (Phương thức trừu tượng).
- selfCheck(): Boolean (Phương thức trừu tượng).
- Lớp cụ thể (VD: TemperatureSensor, WindSensor):
- Cài đặt readData() và selfCheck() dựa trên loại cảm biến.
  
### 3. Lớp PowerManagement

**Phân tích:**
- Lớp này quản lý nguồn pin và các cơ chế sạc năng lượng tái tạo.
  
**Thiết kế:**
- Phân tách quản lý năng lượng thành các mô-đun nhỏ hơn:
- BatteryManager: Quản lý pin.
- EnergyHarvesting: Quản lý năng lượng mặt trời và gió.
- Áp dụng Observer Pattern để giám sát mức năng lượng và kích hoạt hành động khi năng lượng thấp.
  
**Chi tiết thiết kế:**
  
**Thuộc tính:**
- batteryLevel: int
- solarPanelStatus: Boolean
- windGeneratorStatus: Boolean
**Phương thức:**
- chargeBattery(): Kích hoạt sạc.
- shutDownInStorm(): Ngắt hoạt động trong điều kiện thời tiết khắc nghiệt.
- optimizePowerUsage(): Tối ưu hóa sử dụng năng lượng.
### 4. Lớp Communication

**Phân tích:**

- Quản lý giao tiếp giữa trạm và hệ thống quản lý qua vệ tinh.
  
**Thiết kế:**
- Đưa thêm các chiến lược dự phòng như lưu dữ liệu cục bộ khi mất kết nối.
- Áp dụng Command Pattern để đảm bảo việc truyền dữ liệu được thực hiện tuần tự và có thể thử lại nếu thất bại.
  
**Chi tiết thiết kế:**
**Thuộc tính:**
- satelliteLinkStatus: Boolean
- bandwidth: int
- Phương thức:
- establishConnection(): Boolean
- transmit(data: ProcessedData): Boolean
- retryTransmission(data: ProcessedData): Boolean
### 5. Lớp DataManagement
**Phân tích:**
- Xử lý, tổng hợp và lưu trữ dữ liệu thu thập từ các cảm biến.
  
**Thiết kế:**
- Tối ưu hóa dữ liệu trước khi truyền để giảm băng thông qua Compression Algorithms.
- Áp dụng Singleton Pattern để đảm bảo chỉ có một bộ quản lý dữ liệu cho mỗi trạm.
  
**Chi tiết thiết kế:**
**Thuộc tính:**
- rawData: List<WeatherData>
- processedData: ProcessedData
- storageCapacity: int
  
**Phương thức:**
- aggregateData(): ProcessedData
- compressData(data: ProcessedData): CompressedData
- clearOldData(): Giải phóng dung lượng lưu trữ.
### 6. Lớp Maintenance
**Phân tích:**

- Hệ thống bảo trì theo dõi trạng thái phần cứng và thực hiện cập nhật từ xa.
  
**Thiết kế:**
- Tích hợp Remote Update System và cơ chế chẩn đoán lỗi tự động.
- Sử dụng Template Method Pattern để đảm bảo các quy trình bảo trì diễn ra theo một trình tự chuẩn.
  
**Chi tiết thiết kế:**

**Thuộc tính:**
- hardwareStatus: Map<Component, Status>
- errorLogs: List<ErrorLog>
- softwareVersion: String
  
**Phương thức:**
- sendStatusReport(): StatusReport
- updateSoftware(version: String): Boolean
- performDiagnostics(): DiagnosticReport

 ## 4.Nhóm các lớp thiết kế vào package
**Package weatherstation**

- Chứa lớp trung tâm WeatherStation.
  
**Package sensor**

**Chứa các lớp liên quan đến cảm biến:**
- Sensor (lớp cơ sở).
- TemperatureSensor.
- PressureSensor.
- WindSensor.
- RainSensor.
- Package power

**Chứa lớp PowerManagement.**
- Package communication

**Chứa lớp Communication.**
- Package data

**Chứa lớp DataManagement**
- Package maintenance

**Chứa lớp Maintenance.**
#### Biểu đồ Package
![Diagram](https://www.planttext.com/plantuml/png/X5R1Rjim3BtdAuITEc3v0QCeYYNhK235WgPRpupCEa9bogFePjdMBzjXdxHV66JBjfouxIcX-4JfFP4l-VVdxwKNOAbBEwj0FqA1wjqUGNR8Na2CetVgrqmfRS5xTTzcDcscIIWrLn5vlSpKHjXG4TUjqqqYKmldE3S4WZxcAhT7lW620aiaoTHwl11XsfLbJMQeauJTwKZUiS_KodWvtpJHHSpb8D3Mv4mj-o0ve0H3WWIaCLCtGz2cvys7KjfPYrf2XRFtcNfo9eyPOI1VcgdK3YYtU0MrbIJpF7kU3LgtbsyrXgqN1YrHx9R9878JdcZSBjyTAipYZl0zeN_5-Br6qeTCcPvrUB7QPshhd4MWCLb6o3iwySL3s4a1rcmP18_OUhGFYntgnx0-r7sUzTrpXsM5358pHcxuGv3oZceFN3Dw_oRgtb3-Ek8M34qZqYUeGkEbNNxKYVqBR444-R329xGZCPq5NWEXtKp9glQ6yiz8WRfhPkT5vVKEkC2FxJb7-hfAJ6b-OdExhnwAamVOrR9qUxgcZJWkNsovqKYbl4V3DVGT25fh15U67gS9Re7olSbbbwZIKK8liBN6xnQE27KeFMwGT8ZEGiDcQirEe_VOTE49c57uSDVky3xKUslNc7z0fxJ7jj3pPjY7JBILP0uwRwdIyuwExyVCCHIuW0gqaSE4F50KZ0K8TWDtMYQuJrc5aMWmqsGN4JBUPn7uY-s7UR8T4WDCLKcii9Ta1vplWR7hWXkepiF1Zf3aWsgNEtcGsV7A5PqnVufnb_VkGKAnRyZX4SUsridZaVAsx2rMZXiVJUC8gwiS13UnujdJkEH91rN83uxBfO62d1UZVQWxX7tjHgcZ7xtv_AApvanfHmA6lBgOWgsFZ2HJjSSNiEFXUmrvrA-lGTD7x77nykU_v_DJInvbnpuyIWtcEreU77TsYPI7lnN_0G00__y30000)

### Giải thích biểu đồ Package:

- Các lớp được nhóm theo chức năng trong hệ thống.
- Lớp **WeatherStation** nằm ở package trung tâm và liên kết với tất cả các package con.
- Package **sensor** chứa lớp cơ sở Sensor và các lớp cụ thể như **TemperatureSensor**, **PressureSensor.**
- Package **power**, **communication**, **data**, và **maintenance** độc lập, nhưng được sử dụng bởi lớp WeatherStation.

## 5.Xác định giao diện của hệ thống con

**1. Hệ thống trạm thời tiết (WeatherStationSubsystem)**

**Giao diện:** IWeatherStation
- Giao diện cung cấp các chức năng để thu thập và quản lý dữ liệu thời tiết từ các cảm biến.
  
**Phương thức:**
- collectData(): WeatherData
→ Thu thập dữ liệu từ các cảm biến trên trạm.
- getStationStatus(): StationStatus
→ Lấy thông tin trạng thái của trạm (năng lượng, cảm biến, kết nối...).
- transmitData(): void
→ Truyền dữ liệu đã xử lý đến hệ thống quản lý.
- storeDataLocally(): void
→ Lưu dữ liệu cục bộ khi không thể truyền tải.
- configure(newConfig: StationConfig): boolean
→ Cập nhật cấu hình hoạt động của trạm thời tiết.

**2. Hệ thống quản lý và lưu trữ dữ liệu (DataManagementSubsystem)**

 **Giao diện:** IDataManagement
- Giao diện xử lý và lưu trữ dữ liệu từ các trạm thời tiết.
  
 **Phương thức:**
- receiveData(data: WeatherData): boolean
→ Nhận dữ liệu thời tiết từ trạm.
- processData(rawData: WeatherData): ProcessedData
→ Xử lý dữ liệu thô thành dạng tổng hợp.
- storeData(data: ProcessedData): boolean
→ Lưu trữ dữ liệu đã xử lý vào hệ thống cơ sở dữ liệu.
- retrieveData(query: Query): DataResult
→ Truy xuất dữ liệu dựa trên các truy vấn.

**3. Hệ thống bảo trì trạm (MaintenanceSubsystem)**

**Giao diện:** IMaintenance
- Giao diện giám sát, bảo trì, và cập nhật phần mềm trạm thời tiết.
  
**Phương thức:**
- getHardwareStatus(stationID: String): HardwareStatus
→ Lấy thông tin trạng thái phần cứng của trạm.
- sendUpdate(stationID: String, updatePackage: Update): boolean
→ Gửi gói cập nhật phần mềm tới trạm.
- runDiagnostics(stationID: String): DiagnosticReport
→ Chạy chẩn đoán lỗi trên trạm từ xa.
- resetStation(stationID: String): boolean
→ Khởi động lại trạm khi cần thiết.
- scheduleMaintenance(stationID: String, time: DateTime): boolean
→ Lập kế hoạch bảo trì trạm.

**4. Hệ thống giao tiếp vệ tinh (SatelliteCommunicationSubsystem)**

**Giao diện:** ICommunication
- Giao diện quản lý giao tiếp giữa trạm thời tiết và hệ thống quản lý qua vệ tinh.
  
**Phương thức:**
- establishConnection(stationID: String): boolean
→ Thiết lập kết nối với một trạm thời tiết.
- sendData(data: CompressedData, stationID: String): boolean
→ Truyền dữ liệu từ hệ thống đến trạm qua vệ tinh.
- receiveData(stationID: String): CompressedData
→ Nhận dữ liệu từ trạm qua vệ tinh.
- checkConnectionStatus(stationID: String): boolean
→ Kiểm tra trạng thái kết nối vệ tinh của một trạm.

**5. Hệ thống dự báo thời tiết (WeatherForecastingSubsystem)**

**Giao diện:** IForecasting
- Giao diện xử lý và dự báo thời tiết dựa trên dữ liệu đã thu thập.
  
**Phương thức:**
- getWeatherData(query: Query): DataResult
→ Lấy dữ liệu thời tiết đã xử lý từ hệ thống lưu trữ.
- generateForecast(region: String, timeRange: TimeRange): ForecastResult
→ Tạo dự báo thời tiết cho một khu vực cụ thể.
- updateModel(modelConfig: ModelConfig): boolean
→ Cập nhật mô hình dự báo thời tiết.

### Biểu đồ thiết kế giao diện của hệ thống con 

![Diagram](https://www.planttext.com/plantuml/png/Z5LBRjim4Dth54HMCf1SG0iZW8sY0M8WjLDqFQOcCc5ow9936qQHatNH8_KA1VMpQCb9jP1CyitlyStux-y_Zvx1SJ0wEu3SGuNYxWS2xz1j65XPseIjFtj6SoT-PK8eOdHl854yfRZwD3xIQesIby2GpmhHekAo1LJ8dMy63ZwYaeqMnmx86zLxEbfLjaUUhSEu_smbQ7s-EfQMtbGL7EQ4fqMzw4CqoraXjjPg1Cg4UC_UiqlvqUqA22eqI7ox_1JNb-zGeZhMoUKbC2GC967ZSt1MelSrsi5fEM7mqa2m753Orz-6I32Z80xPAMnp-XdGdGlnBNvcXOXxQ_H1yuY85SHg2KZYRHO6e9w22lahkF843jiRzWttJyju3KvHv3-5T8KXbTyF9J2ERUv5g4zUcWGBqG37vGPQAgZ8UbPoElRbV8q7wxWdolVQdBHB0tcvmp9e770mbJKhWpNH-AfCccvA-0OOjLQC2sjC82K_QS04rhEFdc6hbTyjB17A_wq5gHm8Qc7DmVMAkXUVEnZgVWgTUkmQTOToVydp0xNSugpjbI_MeGJFYghRV0r0GwqEskt3xcZWX0uOErUvmqfPIYzx3HJb-Thzd1MYmoVE6ZclR8awD_7TZQhLPJ4k_NhkFZpCHyEew8Ud5_52nJoxXjHcGqQAE8oEgiIBoR2vQ_nLw48OIugjyxL0Wez6K-cbIYr4yEY5x-GkjAAzc6UFI6Ny9_e7003__mC0)

### Giải thích biểu đồ:
- Hệ thống trạm thời tiết giao tiếp trực tiếp với hệ thống quản lý dữ liệu **(IDataManagement)** để truyền dữ liệu thời tiết.
- Hệ thống bảo trì sử dụng **IMaintenance** để giám sát, bảo trì, và cập nhật các trạm thời tiết từ xa.
- Hệ thống giao tiếp vệ tinh **(ICommunication)** là trung gian truyền dữ liệu giữa các hệ thống trạm và hệ thống quản lý/lưu trữ.
- Hệ thống dự báo thời tiết sử dụng dữ liệu từ hệ thống quản lý và cung cấp dự báo thời tiết qua **IForecasting.**
