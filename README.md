# strukturdata-Q1-2501010365-IMADEPANDERADITYAPRAMESWARA-A
# 1. Karakteristik Memori dan Akses Data
Jelaskan mengapa operasi akses elemen pada Array dapat dilakukan dalam waktu konstan
O(1), sedangkan pada Singly Linked List membutuhkan waktu linear O(n). Hubungkan
jawaban Anda dengan konsep alamat memori (kontinu vs non-kontinu).
# JAWABAN
Array itu seperti Hotel yang kamarnya berurutan. Kalau kamu tahu kamar nomor 1 ada di lantai dasar, kamu bisa langsung menebak kamar nomor 100 ada di mana karena letaknya bersebelahan dan berurutan. Kamu tinggal jalan lurus atau naik lift ke titik yang sudah pasti.
Alamat Kontinu: Memori "berjejer" rapi. Komputer tinggal hitung matematika simpel untuk langsung "lompat" ke alamat tujuan.

Linked List itu seperti Pencarian Harta Karun (Scavenger Hunt). Kamu punya petunjuk di tangan, tapi petunjuk itu cuma kasih tahu lokasi pos berikutnya. Di pos berikutnya, baru ada kertas lagi yang kasih tahu lokasi pos setelahnya.
Alamat Non-Kontinu: Node-nya "bertebaran" acak di memori. Kalau kamu mau ke node nomor 5, kamu wajib mampir ke node 1, 2, 3, dan 4 dulu hanya untuk nanya: "Eh, alamat node selanjutnya di mana ya?"

# 2. Analisis Efisiensi Operasi Manipulasi
Dalam kondisi apa sebuah Linked List lebih diunggulkan dibandingkan Array untuk ope
rasi penyisipan (insertion) dan penghapusan (deletion) data? Berikan alasan teoritisnya.
# JAWABAN
Linked List menang dalam hal Cost of Reorganization.
Array: Masalah utamanya bukan cuma menemukan tempatnya, tapi pemindahan fisik data. Menambah data di awal memaksa sistem memindahkan $n$ elemen ke alamat memori berikutnya.
Linked List: Menang saat kita butuh alokasi memori yang dinamis dan instan. Dalam sistem real-time yang tidak punya waktu untuk "menggeser-geser" data (seperti buffer komunikasi data), Linked List jauh lebih efisien karena hanya perlu memperbarui alamat memori pada pointer tanpa menyentuh data lainnya.

# 3. Konsep Doubly Linked List
Jelaskan struktur anatomi dari sebuah node pada Doubly Linked List. Apa dampak kebe
radaan pointer tambahan tersebut terhadap penggunaan memori serta fleksibilitas pene
lusuran dibandingkan dengan Singly Linked List?
# JAWABAN
Anatomi Node: Berbeda dengan Singly yang hanya punya satu penunjuk, node Doubly Linked List memiliki tiga bagian utama:

1. Data: Nilai yang disimpan.
2. Pointer next: Alamat node selanjutnya.
3. Pointer prev: Alamat node sebelumnya.
Dampaknya:
Memori: Penggunaan memori lebih boros karena setiap node harus menyimpan satu alamat tambahan (pointer prev).

Fleksibilitas: Jauh lebih fleksibel. Kita bisa melakukan penelusuran dua arah (maju dan mundur). Hal ini sangat memudahkan operasi seperti menghapus node tertentu tanpa harus mencari node sebelumnya dari awal list.

# 4. Mekanisme Circular Linked List
Apa yang membedakan Circular Linked List dari Linked List biasa secara teoritis? Se
butkan satu contoh skenario penggunaan (use case) di mana struktur melingkar ini lebih
efektif digunakan.
# JAWABAN
Secara teoritis, yang membedakan adalah node terakhir tidak menunjuk ke NULL, melainkan menunjuk kembali ke node pertama (head). Ini menciptakan siklus tanpa ujung.

Skenario Penggunaan (Use Case):
Sangat efektif untuk implementasi Round Robin Scheduling pada Sistem Operasi. Misalnya, CPU memberikan jatah waktu pada beberapa aplikasi secara bergantian. Setelah aplikasi terakhir selesai mendapatkan jatah waktu, CPU langsung kembali ke aplikasi pertama secara otomatis melalui struktur melingkar ini.

# 5. Array Dinamis di Python
Python list secara internal diimplementasikan sebagai Dynamic Array. Jelaskan meka
nisme yang terjadi ”di balik layar” ketika sebuah Dynamic Array kehabisan kapasitas saat
melakukan operasi append.
# JAWABAN
Over-allocation: Python tidak memesan memori baru sesuai jumlah elemen, tapi menggunakan Growth Factor.

Mekanisme: Saat append memicu resize, Python melakukan realloc(). Ia mencari blok memori baru, menyalin reference objek (bukan objeknya sendiri), dan menghapus blok lama.

Kenapa tetap cepat? Karena frekuensi "pindah rumah" ini berkurang secara logaritmik seiring bertambahnya ukuran list. Biaya mahal saat pindah rumah "dicicil" (diamortisasi) oleh ribuan operasi append lainnya yang sangat murah ($O(1)$), sehingga rata-ratanya tetap dianggap konstan.
