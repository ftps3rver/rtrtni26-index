Kerentanan yang dimanfaatkan pada challenge ini adalah **IDOR (Insecure Direct Object Reference)**. Awalnya, setiap note bisa diakses menggunakan parameter `id` pada URL. Setelah nyoba mengganti nilai parameter tersebut secara manual, ternyata server tidak melakukan pengecekan hak akses dengan benar.

Pas parameter diubah menjadi `id=4`, aplikasi langsung menampilkan note milik administrator berjudul **“Administrator Secret”**, padahal user biasa seharusnya nggak punya akses ke note tersebut.

Jadi simpelnya, celahnya ada di **broken access control pada parameter `id`**. Server cuma mengambil data berdasarkan ID yang dikirim user tanpa memastikan apakah note tersebut memang boleh diakses oleh user yang sedang login.

Dari `id=4` inilah note rahasia administrator berhasil kebuka dan flag `RTRTNI26{...}` bisa didapatkan.

![Administrator Secret](images/administrator-secret.png)
