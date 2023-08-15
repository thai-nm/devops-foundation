# Giải thích

1. Tại sao lại cần update file `.env`?
- Một số thông tin:
  - File `.env`: file chứa các biến môi trường cần có cho frontend.
  - Biến môi trường `VITE_API_SERVER`: URL tới API backend server.
- Ở bài tập này, frontend sử dụng framework ReactJS. Muốn chạy được frontend thì cần phải có một bước build static folder `dist`, chính là step `npm run build` trong Dockerfile của repo frontend. Tại step build này, value của biến `VITE_API_SERVER` sẽ được load trực tiếp vào output static folder `dist`. Nghĩa là với đoạn code sử dụng biến `VITE_API_SERVER` ở frontend:
```javascript
await fetch(${import.meta.env.VITE_API_SERVER || "http://sample-webapp-nodejs:3000"}/quote);
```
Sau khi build ra static folder, với biến `VITE_API_SERVER=http://172.17.0.1:13000` thì đoạn code trên là sẽ chuyển thành:
```javascript
await fetch("http://172.17.0.1:13000/quote")
```
Như vậy, file `.env` chứa biến `VITE_API_SERVER` đóng vai trò giữ giá trị của backend API endpoint (trường hợp này giá trị là `http://172.17.0.1:13000`).

2. Có cách nào viết biến môi trường trên Docker Compose để frontend gọi về API mà không cần phải đổi code FE tại file `.env` và đoạn code JavaScript trên kia không?
- Với source code hiện tại thì câu trả lời là **không**.
- Lí do là file `.env` được sử dụng tại step build, vốn được chạy khi ta build Docker image của frontend. Và sau khi build xong, code frontend không còn sử dụng đến file `.env` nữa do đã load toàn bộ giá trị vào thẳng code như đã giải thích ở câu 1. Từ đó, kể cả chúng ta viết biến môi trường rồi sử dụng Docker Compose để đưa biến đó vào trong container frontend, frontend cũng sẽ không sử dụng các biến này.
- Mục đích của bài tập này là chúng ta deploy hai container: 1 frontend và 1 backend rồi cho 2 container này gọi tới nhau. 2 container này được expose tại 2 port `13000` và `18080` với địa chỉ `0.0.0.0` của host, đồng nghĩa với việc expose tại IP của host trong Docker network. Điều này có nghĩa, ta có thể mở browser ở máy host tới địa chỉ `localhost:18080` để truy cập frontend, và khi container frontend call tới địa chỉ IP của host tại port `13000` thì sẽ truy cập được backend.
- Có thể tới đây các bạn sẽ thắc mắc, tại sao ta không để giá trị của biến `VITE_API_SERVER` là `http://backend_container_name:3000`, vì ta được học Docker Compose mặc định sẽ cho phép các container call tới nhau bằng container name. Nghĩa là khi ta đứng trong container frontend, hoàn toàn có thể ping tới container backend sử dụng tên của container backend. Tuy nhiên, điều ta cần chú ý là khi ta truy cập frontend từ browser, click vào button `Give me a quote` và gọi API tới backend, thì request từ browser của chúng ta sẽ gửi đi là `GET http://backend_container_name:3000/quote` và gây ra lỗi `NAME_NOT_RESOLVE`. Lí do là vì ta đang truy cập frontend từ broswer của máy host, và máy host của chúng ta không có khả năng resolve domain name `backend_container_name` thành IP của container backend, dẫn đến lỗi kia. Chính vì vậy nên ta phải update giá trị của biến `VITE_API_SERVER`.

3. (Nâng cao) Cách khắc phục trên thực tế để tận dụng được tính năng cho phép call tới container name của Docker Compose. 
- Kiến trúc có sự thay đổi:
  - Sử dụng thêm Reverse proxy container "đứng trước" frontend container và backend container, điều hướng request khi gọi tới một domain cụ thể. Ví dụ:
    - Request tới domain `https://app.sample.com` sẽ được reverse proxy chuyển hướng truy cập tới frontend, sử dụng tên của container frontend để chuyển hướng.
    - Request tới domain `https://api.app.sample.com` sẽ được reverse proxy chuyển hướng truy cập tới backend, sử dụng tên của container backend để chuyển hướng.
- Giá trị của biến `VITE_API_SERVER` sẽ là một đường dẫn tới backend thông qua internet, ví dụ: `VITE_API_SERVER=https://api.app.sample.com`.
- Lúc này, flow của một request sẽ như sau:
  - Client mở browser, truy cập `https://app.sample.com` chính là tạo request `GET https://app.sample.com`
  - Reverse proxy nhận được request tới domain `https://app.sample.com` => cho truy cập tới trang web frontend.
  - Client click vào button `Give me a quote` => Tạo và gửi request `GET https://api.app.sample.com/quote`
  - Reverse proxy nhận được request tới domain `https://api.app.sample.com` => chuyển request tới backend xử lý.
  - Backend xử lý request và gửi về response cho client.
  - Browser lấy response nhận được và render ra kết quả trên trang web `https://app.sample.com`.