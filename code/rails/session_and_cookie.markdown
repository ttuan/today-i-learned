Phan biet session va cookie.
Thuong moi nguoi de nham lan giua 2 khai niem nay. Trong rails tutorial co noi
ve viec luu tru session: ```session[:user_id] = @user.id```
O day ta hieu la id cua @user se duoc luu vao trong session duoi dang 1 hash co key la ```user_id``` con key la @user.id. Nhung co 1 van de o day, khi co nhieu nguoi dung cung truy cap 1 luc, thi id
cua nguoi dung nao se duoc luu? Lieu cac key, value do co bi ghi de khog?

* Cookie la mot chuoi cac ki tu da duoc ma hoa, luu lai o trong browser cua
nguoi dung.
* Session la 1 trunk cac thong tin, duoc luu tru o tren sever.

Trong lan dau sau khi dang nhap, server se gui cookie ve cho client. Sau do, moi
khi client gui 1 request len server, cookie cung se duoc gui len theo.
Server se dua vao cookie vua duoc gui len de tim dung ```session``` cho cookie
do. Tu do, xac dinh duoc user hien tai voi ```user_id``` duoc luu trong session.
