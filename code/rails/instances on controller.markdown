Trong controller, chung ta k nen dung qua nhieu bien instances. Toi da chi nen
dung 2 bien. Neu co nhieu hon, ta nen lam 1 thu muc app/models/supports/<ten
controller>
trong file Support se viet cac ham de lay bien install, Trong controller chi can
khai bao ```@support = Supports::User.new``` sau do dung bien @support de goi
den cac ham lay bien install trong view.
