Từ rails 4 trở đi, trong Gemfile mặc định lúc cài app, Rails có add thêm cho
project gem `turbolink`. Lúc đầu mình không hiểu lắm về công dụng của gem này,
sau đọc lại thì có tác dụng rất lớn, giúp cho việc load trang web nhanh hơn rất
nhiều.

Turbolink sẽ giúp cho việc load trang web được giảm bớt nhờ việc bớt load các
file js. Khi ta click vào 1 thẻ <a> trên trang, turbolink sẽ dùng ajax để gọi
tới địa chỉ trang đó, sau đó lấy thẻ <body> trong request đẻ thay vào thẻ <body>
hiện tại. ^^ Như vậy tốc độ sẽ tăng lên nhiều do không phải load thêm các đoạn
js được require trong <header>
