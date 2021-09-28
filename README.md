## Thêm PWA vào Angular
Để thiết lập Angular service worker trong dự án, hãy sử dụng lệnh CLI ng add @ angle / pwa. Lệnh “ng add angular pwa” sẽ hiện thực hoá việc này
 **ng add @angular/pwa**
 
- Lệnh “ng add angular pwa” được chạy đã tạo ra tệp ngsw-config.json. Nó chỉ chịu trách nhiệm service workers. Đồng thời, service workers cũng đã được tự động thêm vào file app.module.ts.
 
 // app.module.ts
import { ServiceWorkerModule } from '@angular/service-worker';
import { environment } from '../environments/environment';

@NgModule({
  declarations: [...], <br>
  imports: [ <br>
    ServiceWorkerModule.register('ngsw-worker.js', { enabled: environment.production }) <br>
  ],<br>
  providers: [...], <br>
  bootstrap: [...],<br>
  schemas: [...]<br>
})

export class AppModule { }

## Build & Cấu hình Production với http-server
Cài đặt http-server global từ NPM: **npm install -g http-server**

Để build ứng dụng cho môi trường production, chạy lệnh sau: **npm run build-prod**

Sau khi chạy lệnh, bản sẽ có bản build trong folder dist/angular-pwa. Tiếp theo, chúng ta sẽ chạy ứng dụng angular PWA sử dụng http-server

Vào trong thư mục prod build: **cd dist/<project-name>**
  
Vì ng serve không hoạt động với service worker, bạn phải sử dụng một máy chủ HTTP riêng để kiểm tra local dự án của mình. Sử dụng bất kỳ máy chủ HTTP nào. Ví dụ sau sử dụng gói máy chủ http từ npm. Để giảm khả năng xung đột và tránh phân phát nội dung cũ, hãy kiểm tra trên một cổng chuyên dụng và tắt bộ nhớ đệm. Để cung cấp thư mục chứa các tệp web của bạn với http-server. 

Để chạy lên bản build, thực hiện dòng lệnh sau: **http-server -p 8080**
  
Lệnh trên sẽ mở angular app theo đường dẫn http://127.0.0.1:8080 

## link refer.
https://angular.io/guide/service-worker-getting-started

