# CSDLPT-PTIT: Cơ sở dữ liệu phân tán - CellPhoneS Cần Thơ

## Mô tả dự án
Dự án này xây dựng hệ thống quản lý cửa hàng CellPhoneS với các chi nhánh phân bố trên nhiều địa điểm, cụ thể là chi nhánh Cần Thơ, với trụ sở chính đặt tại Hà Nội. Hệ thống bao gồm quản lý thông tin sản phẩm, khách hàng, đơn hàng, nhà cung cấp, và nhân viên. Cơ sở dữ liệu thiết kế dựa trên mô hình quan hệ, với các bảng đại diện cho từng thực thể và mối quan hệ giữa chúng.

### Các bảng chính trong hệ thống:

#### 1. **Bảng Stores: Quản lý cửa hàng**
- **Mục đích**: Lưu thông tin về các cửa hàng của CellPhoneS.
- **Cấu trúc**:
  - `StoreID`: Mã cửa hàng (khóa chính, tự động tăng).
  - `DepartmentID`: Mã chi nhánh (liên kết với bảng `Department`).
  - `StoreName`: Tên cửa hàng.
  - `StoreAddress`: Địa chỉ cửa hàng.

#### 2. **Bảng Products: Quản lý sản phẩm**
- **Mục đích**: Lưu thông tin sản phẩm được bán tại các cửa hàng.
- **Cấu trúc**:
  - `ProductID`: Mã sản phẩm (khóa chính, tự động tăng).
  - `Name`: Tên sản phẩm.
  - `Brand`: Thương hiệu sản phẩm.
  - `Price`: Giá sản phẩm.
  - `Quantity`: Số lượng tồn kho.
  - `Description`: Mô tả sản phẩm.
  - `CategoryID`: Mã danh mục sản phẩm (liên kết với bảng `Categories`).

#### 3. **Bảng Categories: Danh mục sản phẩm**
- **Mục đích**: Quản lý các danh mục của sản phẩm.
- **Cấu trúc**:
  - `CategoryID`: Mã danh mục (khóa chính, tự động tăng).
  - `CName`: Tên danh mục.
  - `DescCate`: Mô tả danh mục.

#### 4. **Bảng Customers: Quản lý khách hàng**
- **Mục đích**: Lưu thông tin khách hàng mua sắm tại CellPhoneS.
- **Cấu trúc**:
  - `CustomerID`: Mã khách hàng (khóa chính, tự động tăng).
  - `FullName`: Họ và tên khách hàng.
  - `Email`: Địa chỉ email (duy nhất).
  - `Phone`: Số điện thoại liên lạc.
  - `Address`: Địa chỉ giao hàng.

#### 5. **Bảng Orders: Quản lý đơn hàng**
- **Mục đích**: Lưu thông tin các đơn hàng được đặt tại cửa hàng.
- **Cấu trúc**:
  - `OrderID`: Mã đơn hàng (khóa chính, tự động tăng).
  - `CustomerID`: Mã khách hàng (liên kết với bảng `Customers`).
  - `StoreID`: Mã cửa hàng (liên kết với bảng `Stores`).
  - `OrderDate`: Ngày và giờ đặt hàng.
  - `TotalAmount`: Tổng tiền đơn hàng.
  - `Status`: Trạng thái đơn hàng.

#### 6. **Bảng OrderDetails: Chi tiết đơn hàng**
- **Mục đích**: Lưu chi tiết về từng sản phẩm trong mỗi đơn hàng.
- **Cấu trúc**:
  - `OrderID`: Mã đơn hàng (liên kết với bảng `Orders`).
  - `ProductID`: Mã sản phẩm (liên kết với bảng `Products`).
  - `Quantity`: Số lượng sản phẩm trong đơn hàng.
  - `Price`: Giá sản phẩm tại thời điểm đặt hàng.

#### 7. **Bảng Suppliers: Thông tin nhà cung cấp**
- **Mục đích**: Lưu thông tin về các nhà cung cấp sản phẩm cho cửa hàng.
- **Cấu trúc**:
  - `SupID`: Mã nhà cung cấp (khóa chính, tự động tăng).
  - `SupName`: Tên nhà cung cấp.
  - `ContactName`: Tên người liên hệ.
  - `Phone`: Số điện thoại nhà cung cấp.
  - `Address`: Địa chỉ nhà cung cấp.

#### 8. **Bảng ProductSuppliers: Nhà cung cấp sản phẩm**
- **Mục đích**: Lưu thông tin về nhà cung cấp sản phẩm cụ thể.
- **Cấu trúc**:
  - `ProductID`: Mã sản phẩm (liên kết với bảng `Products`).
  - `SupplierID`: Mã nhà cung cấp (liên kết với bảng `Suppliers`).
  - `Quantity`: Số lượng sản phẩm được cung cấp.

#### 9. **Bảng Employees: Quản lý thông tin nhân viên**
- **Mục đích**: Lưu thông tin về nhân viên làm việc tại cửa hàng.
- **Cấu trúc**:
  - `EID`: Mã nhân viên (khóa chính, tự động tăng).
  - `FullName`: Họ và tên nhân viên.
  - `Address`: Địa chỉ nhân viên.
  - `Phone`: Số điện thoại nhân viên.
  - `Email`: Địa chỉ email nhân viên.
  - `Position`: Chức vụ của nhân viên.
  - `Salary`: Mức lương của nhân viên.
  - `StoreID`: Mã cửa hàng nơi nhân viên làm việc (liên kết với bảng `Stores`).

#### 10. **Bảng Headquarter: Thông tin trụ sở chính**
- **Mục đích**: Quản lý thông tin về trụ sở chính của hệ thống CellPhoneS.
- **Cấu trúc**:
  - `HeadquarterID`: Mã trụ sở chính (khóa chính, tự động tăng).
  - `Name`: Tên trụ sở.
  - `Address`: Địa chỉ trụ sở chính.

#### 11. **Bảng Department: Quản lý chi nhánh**
- **Mục đích**: Lưu thông tin chi nhánh của hệ thống.
- **Cấu trúc**:
  - `DepartmentID`: Mã chi nhánh (khóa chính, tự động tăng).
  - `Name`: Tên chi nhánh.
  - `Address`: Địa chỉ chi nhánh.
  - `HeadquarterID`: Mã trụ sở chính (liên kết với bảng `Headquarter`).

---

## Hướng dẫn sử dụng
1. Tạo cơ sở dữ liệu và chạy các lệnh SQL trên để tạo bảng.
2. Nhập dữ liệu vào các bảng phù hợp với nhu cầu.
3. Sử dụng các truy vấn SQL để quản lý thông tin sản phẩm, đơn hàng, khách hàng, nhà cung cấp, và nhân viên của hệ thống.

---

## Yêu cầu hệ thống
- MySQL hoặc hệ quản trị cơ sở dữ liệu quan hệ tương tự.
- Công cụ hỗ trợ quản lý cơ sở dữ liệu như MySQL Workbench hoặc phpMyAdmin.

---


