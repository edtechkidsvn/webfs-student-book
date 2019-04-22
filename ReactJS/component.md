# Component

## I. Component là gì
### 1. Khái niệm
Trong các dự án website thực tế, khi làm phần giao diện cho các trang của một website thì thông thường người ta thường chọn cách viết tất cả code HTML của trang đó trong chung một file. Điều đó dẫn đến hai vấn đề như sau:
- Có một số phần cần có mặt trong nhiều hơn 1 trang ví dụ như thanh Navbar hoặc phần Footer,... Khi đó code của những phần này phải lặp lại trên các trang mà nó xuất hiện, gây lặp code và rất tốn công nếu muốn thêm hoặc sửa những phần code đó.
- Nội dung của 1 trang HTML phức tạp thì sẽ dài và khó quản lý, đặc biệt là khi muốn chỉnh sửa nội dung hoặc khi gặp lỗi trên trang.

Vì thế để giải quyết những vấn đề đó, trong ReactJS chúng ta sẽ chia nhỏ code của một trang HTML ra thành những đoạn code nhỏ hơn gọi là `component`. Các `component` không phụ thuộc lẫn nhau và **có khả năng sử dụng lại** cùng với việc **dễ dàng để sửa nội dung hoặc tìm ra phần gặp lỗi**.
### 2. Cú pháp
Có hai loại component là `Stateless functional components` và `Class components`. Trong mỗi components đều phải trả về nội dung được viết bằng `JSX` - là một dạng thay thế cho HTML trong ReactJS.

- `Stateless functional components` là components đơn giản được tạo bởi một function và JSX sẽ được trả về bằng `return` trong function đó.

```javascript
// Kiểu thông thường
function Navbar() {
	return ...
}

// Kiểu gán vào biến
const Navbar = function () {
	return ...
}

// Hoặc dùng arrow function
const Navbar = () => {
	return ...
}
```

- `Class components` là components được tạo bởi class kế thừa từ class `Component` của React, chúng ta sẽ phải import class này từ thư viện `react`. JSX trong class components sẽ được trả về bởi `return` trong phương thức `render` của class đó.

```javascript
import React, { Component } from 'react';

class Navbar extends Component {
	render() {
		return ...
	}
}
```

- Những component này sẽ ghép với nhau để trở thành một trang hoàn chỉnh. Để sử dụng component thì chúng ta sẽ đưa nó vào trong JSX với cú pháp sau:

```javascript
...
render() {
	return (
		<div>
			<Navbar />
			<Content />
			<Footer />
		</div>
	);
}
...
```
### 3. JSX

- JSX hay Javascript XML là một dạng cú pháp mở rộng cho javascript trong React. Nó dùng để giúp chúng ta có thể code được phần cấu trúc HTML thông thường trong React.
- Cú pháp của JSX có dạng giống với XML, hay cũng có thể nói là giống như HTML với các node (nút), mỗi node sẽ có thẻ đóng, mở và nội dung bên trong.

```xml
// Cấu trúc của một node trong JSX
<JSXElementName JSXAttributesopt>
	content
</JSXElementName>
// Nếu không có content bên trong thì có thể đóng luôn mà không cần thẻ đóng
<JSXElementName JSXAttributesopt />
```
- Về cơ bản JSX vẫn hỗ trợ các tag HTML thông thường nhưng sẽ có 1 số điểm khác biệt:
	- Bắt buộc phải có thẻ đóng, nếu không có content bên trong thì phải đóng như bên trên.
	- Attribute class bị trùng với từ khoá của javascript nên phải đổi thành className.
	- Các attribute dạng hyphen separated hoặc có 2 từ trở lên thì sẽ phải chuyển về dạng camel case. Ví dụ: onchange => onChange, tabindex => tabIndex,...