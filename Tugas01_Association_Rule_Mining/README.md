# Association Rule Mining

Analisis asosiasi (*Association Rule*) adalah metode *machine learning* dan *data mining* digunakan untuk menemukan hubungan yang menarik (*joint value*) item-item yang sering muncul  secara bersama-sama dalam suatu *database*. Aturan ini bisa berupa studi  transaksi di supermarket, misalnya  seseorang yang membeli susu bayi juga  membeli sabun mandi. Di sini berarti susu  bayi bersama dengan sabun mandi. Karena awalnya berasal dari studi tentang database transaksi konsumen untuk menentukan kebiasaan suatu produk dibeli bersama produk apa, maka aturan asosiasijuga sering dinamakan *Market Basket Analysis*. Pada *Market Basket Analysis* memungkinkan pengecer untuk mengidentifikasi hubungan item yang sering dibeli orang bersama-sama.



Bentuk umum dari Aturan asosiasi yaitu:

Misalkan 𝐼 = {𝐼1,𝐼2, ⋯ ,𝐼𝑚}  merupakan kumpulan  item. Sekumpulan item disebut sebagai ***itemset***. *Itemset* yang mengandung k-*item* disebut ***k-itemset***. **D** merupakan database yang terdiri dari kumpulan transakasi (*T*), dimana T->I. Setiap transaksi memiliki *ID* transaksi yang disebut *TID*.   

Sebuah *association rule* dituliskan dalam bentuk X &#8594; Y, dimana  X&#8594;I,  Y&#8594;I. *Association rule* berbentuk *“If antecendent then consequent”* (Larose & Larose, 2015). *X* disebut sebagai *Antecedent atau left-hand side (LHS)* dan *Y* disebut *Consequent atau right-hand side (RHS)*. 

*"If roti dan mentega, maka susu" ("Jika roti dan mentega dibel, maka susu juga akan dibeli pelanggan")*

*Antecedent* 	: Roti dan Mentega

*Consequent*	: Susu 

*Itemset*		: {Roti, Mentega, Susu}



Terdapat dua proses yang dilakukan untuk  mendapatkan assosiation rule : 

**a. Mendapatkan semua *frequent itemset***

 *I* dikatakan *frequent itemset* apabila nilai *support* dari item memenuhi nilai minimum support (*min_sup*). Algoritma yang dapat digunakan untuk mencari *frequent itemset* dapat berupa Algoritma *Apriori*, ataupun *FP-Growth*. 	

***Support*** adalah ukuran atau presentasi munculnya sebuah *itemset* dalam sebuah transaksi. Pertimbangkan itemset_1 = {Roti, Mentega} dan itemset_2 = {Roti, Sampo}. Dalam hal ini transaksi yang memiliki roti dan mentega akan lebih banyak dibandingkan roti dan sampo, sehingga itemset_1 umumnya memiliki support yang lebih tinggi daripada itemset_2.

Nilai support sebuah item diperoleh dengan rumus berikut:

![alt text](https://github.com/ToKu404/Machine-Learning-Assignment/blob/main/Assets/Tugas1/Math1.jpg?raw=true)

​			Sedangkan nilai support dari 2 item diperoleh dari rumus berikut:

![alt text](https://github.com/ToKu404/Machine-Learning-Assignment/blob/main/Assets/Tugas1/Math2.jpg?raw=true)

Jika sebuah itemset kebetulan memiliki support yang sangat rendah, kita tidak dapat mengambil informasi yang cukup tentang hubungan antar itemnya dan karenanya tidak ada kesimpulan yang dapat ditarik dari aturan seperti itu.

**b. Menghasilkan *association rule* yang kuat dari *frequent itemset***

Setelah semua pola frequensi tinggi ditemukan, barulah dicari aturan assosiatif yang kuat. *Association rule* yang kuat memenuh syarat minimum untuk *confidence *(*min_confidence*) dengan menghitung *confidence(A &#8594; B)*

***Confidence*** adalah kuatnya hubungan antar item dalam aturan asosiasi. Dapat dikatakan sebagai nilai presentase atau ukuran kemungkinan munculnya *Consecuent* diantara semua grup yang berisi *Antercedent*. Semakin tinggi nilainya, maka semakin besar kemungkinan item *Consecuent* muncul jika diketahui bahwa semua item *Antercedent* muncul dalam itemset tersebut. 

Nilai *confidence* dari aturan A &#8594; B diperoleh dari rumus berikut : 

![alt text](https://github.com/ToKu404/Machine-Learning-Assignment/blob/main/Assets/Tugas1/Math3.jpg?raw=true)

Sebelum beranjak, pertimbangkan *confidence* untuk {Mentega} &#8594; {Roti}, maka dapat diperkirakan nilanya sangat tinggi. Bagaimana dengan {Sikat gigi}&#8594;{Susu}? *Confidence* untuk aturan ini akan tinggi juga mengingat {Susu} adalah  itemset yang sering muncul pada transaksi lainnya.

> Tidak masalah apa yang terdapat pada *antersedent*, *confidence* untuk *association rule* yang memiliki *consecuent* yang sering muncul akan selalu tinggi 

Meski suatu aturen memiliki nilai *confidence* yang tinggi, padahal secara intuitif dapat diketahui bahwa aturan ini memiliki asosiasi yang lemah, sehingga terdapat sesuatu yang sedikit menyesatkan tentang nilai kepercayaan yang tinggi ini. *Lift* diperkenalkan untuk mengatasi tantangan ini.

***Lift*** adalah suatu ukuran untuk mengetahui  kekuatan aturan asosisasi (association rule) yang  telah terbentuk. Nilai lift ratio biasanya digunakan  sebagai penentu apakah aturan asosiasi valid atau tidak valid. Untuk menghitung lift ratio digunakam  rumus sebagai berikut:

![alt text](https://github.com/ToKu404/Machine-Learning-Assignment/blob/main/Assets/Tugas1/Math4.jpg?raw=true)

Untuk mendapatkan nilai benchmark confidence sendiri dapat dihitung menggunakan rumus sebagai berikut:

![alt text](https://github.com/ToKu404/Machine-Learning-Assignment/blob/main/Assets/Tugas1/Math5.jpg?raw=true)

dimana : 

Nc = Jumlah transaksi dengan item yang menjadi consequent

N = jumlah transaksi basis data



Contoh aturan asosiasi : 

*{Roti, Mentega} &#8594; {Susu} (support = 40%, confidence = 50%)*

Association Rules di atas dapat dibaca secara sederhana menjadi : "50% dari transaksi di database yang memuat item roti dan mentega juga memuat item susu.  Sedangkan 40% dari seluruh transaksi yang ada di database memuat ketiga item itu."  Dapat juga diartikan : "Seorang konsumen yang membeli roti dan mentega punya kemungkinan 50% untuk  juga membeli susu. Aturan ini cukup signifikan karena mewakili 40% dari catatan transaksi selama ini.



**Market Basket Analysis**

Market basket analysis merupakan suatu proses untuk  menganalisis kebiasaan pembelian pelanggan dengan menemukan  hubungan antara item-item yang dibeli pelanggan dalam  keranjang belanjaannya. Informasi yang ditemukan nantinya  dapat digunakan untuk mengembangkan strategi pemasaran  dalam supermarket sehingga dapat meningkatkan keuntungan  yang didapatkan. 

Market basket data dapat direpresentasikan dengan format  biner seperti pada contoh berikut. Dimana setiap baris merupakan  data setiap transaksi dan kolom menggambarkan item-itemnya.  Format ini biasanya digunakan saat association rule digunakan  dalam mengidentifikasi frequent itemset (Venkatachari, 2016).

**Tabel 1** *Binary Database* 

| TID | Roti | Mentega | Susu|Selai|
|-----|------|---------|-----|-----|
| T1  | 1	 | 1 	   |1    |0    |
| T2  | 1	 | 1       |0    |1    |
| T3  | 1	 | 0       |0    |1    |
| T4  | 0	 | 1       |1    |0    |

Tabel 1 menunjukkan data transaksi. Apabila transaksi mengandung item dalam kolom maka akan diberi nilai 1 namun jika tidak maka akan  diberi nilai 0.

**Tabel 2**  *Database* Transaksi
| TID | Itemset|
|-----|-----|
| T1  | Roti, Mentega, Susu|
| T2  | Roti, Mentega, Selai |
| T3 | Roti, Selai|
| T4  | Mentega, susu|

Tabel 2 menunjukkan ID transaksi dan keterangan tentang item apasajakah yang dibeli pada transaksi ID tersebut.

### Apriori

*Apriori* adalah algoritma yang diperkenalkan oleh R. Agrawal dan R. Srikant pada tahun 1994 untuk mencari frequent itemset untuk data *Boolean* pada *association* *rule* (Han & Kember, 2006). *Apriori* menggunakan metode iteratif dimana k-*itemset* digunakan untuk menentukan (k+1) itemset. 

Item I *infrequent* adalah jika:

1) P(I) < *min\_support* *threshold*, maka *infrequent*.
1) P(I+A) < *minimum\_support threshold*, maka I+A *infrequent*, dimana A juga termasuk *itemset*.
1) Jika *itemset* *infrequent* maka semua supersetnya juga akan *infrequent*.

Langkah awal dalam algoritma apriori yang harus dilakukan adalah melakukan *scanning* data untuk menemukan *support* untuk setiap 1-itemset. Hanya item yang memenuhi *minimum* *support* saja yang akan dilakukan analisis lebih lanjut. Item yang memenuhi *minimum* *support* ini dinotasikan dengan 𝐿1. 𝐿1 akan digunakan untuk menemukan 𝐿2. 𝐿2 akan digunakan untuk menemukan 𝐿3, dan seterusnya sampai tidak ada k-*itemset* yang dapat dibentuk. Untuk menemukan 𝐿𝑘 dibutuhkan satu kali *full* *scanning* *database*. 

Langkah-langkah yang diikuti dalam Algoritma Apriori dari data mining adalah:

1. *Join Step:* Langkah ini menghasilkan (k+1) itemset dari K-*itemsets* dengan menggabungkan setiap item dengan dirinya sendiri
1. *Prune Step:* Langkah ini melakukan *scanning* jumlah setiap item di *database.* Jika *candidate item* tidak memenuhi *min\_support,* maka item tersebut dianggap *infrequent* dan karenanya akan dihapus. Langkah ini dilakukan untuk memperkeci ukuran *candidate itemsets.*

Cara Kerja Apriori

1. Tentukan *minimum support.*
1. Iterasi 1 : hitung item-item dari *support* (transaksi yang memuat seluruh item) dengan *menscan* *database* untuk 1-*itemset*, setelah 1-itemset didapatkan, dari 1-*itemset* apakah diatas *minimum* *support*, apabila telah memenuhi *minimum* *support*, 1-*itemset* tersebut akan menjadi pola *frequent* tinggi.
1. Iterasi 2 : untuk mendapatkan 2-*itemset*, harus dilakukan kombinasi dari k-*itemset* sebelumnya, kemudian scan *database* lagi untuk hitung item-item yang memuat *support*. itemset yang memenuhi minimum support akan dipilih sebagai pola *frequent* tinggi dari kandidat.
1. Tetapkan nilai k-itemset dari support yang telah memenuhi minimum support dari k-itemset.
1. Lakukan proses untuk iterasi selanjutnya hingga tidak ada lagi k-itemset yang memenuhi minimum support.


Untuk lebih jelasnya, berikut ini adalah contoh penerapan algoritma apriori. Misalkan *support count* yang digunakan adalah 2. Berikut ini adalah *database* transaksi

Tabel 3 Database Transaksi

| **TID** | **Itemset yang dibeli** |
| ------- | ----------------------- |
| T1      | A, B, E                 |
| T2      | B, D                    |
| T3      | B, C                    |
| T4      | A, B, D                 |
| T5      | A, C                    |
| T6      | B, C                    |
| T7      | A, C                    |
| T8      | A, B, C, E              |
| T9      | A, B, C                 |

Langkah pertama yaitu scanning *database* dan menghitung jumlah transaksi untuk 1-*itemset*. Ck= {A, B, C,D, E}.

Berikut ini adalah hasilnya.

Tabel 4 *Support Count 1-itemset*

| **1-*Itemset*** | ***Support Count*** |
| --------------- | ------------------- |
| A               | 6                   |
| B               | 7                   |
| C               | 6                   |
| D               | 2                   |
| E               | 2                   |

Karena semua item memenuhi *minimum* *support* maka L1 = {A, B, C,D, E}. Selanjutnya membangkitkan *candidate* *generation*. C2 = {AB, AC, AD,AE, BC, BD, BE, CD, CE,DE}. Setelah itu masuk ke tahap *prune* yaitu melakukan scanning kembali apakah subset untuk setiap itemset yang ada pada C2 merupakan bagian dari L1. Jika tidak maka *itemset* ini akan dikeluarkan dari C2. Selanjutnya menghitung *support* *count* untuk C2. Berikut adalah hasilnya.

Tabel 5 *Support Count 2-itemset*

| **2-*Itemset*** | ***Support Count*** |
| --------------- | ------------------- |
| AB              | 4                   |
| AC              | 4                   |
| AD              | 1                   |
| AE              | 2                   |
| BC              | 4                   |
| BD              | 2                   |
| BE              | 2                   |
| CD              | 0                   |
| CE              | 1                   |
| DE              | 0                   |

Dari tabel di atas dapat dilihat bahwa terdapat tiga *itemset* yang tidak memenuhi minimum support yaitu CD, CE, dan DE sehingga item ini tidak termasuk ke dalam L2. Jadi L2 = {AB, AC, AD, AE, BC, BD, BE, CD, CE, DE}. Kembali ke tahap *join* *step* yaitu membangkitkan candidate generation untuk 3-itemset. Maka didapatkan C3 = {ABC, ABE, ACE, BCD, BCE, BDE}.

Selanjutnya dilakukan *scanning* kembali pada *database*, ternyata ada *subset* dari C3 yang bukan merupakan bagian dari L2, sehingga *itemset* tersebut dikeluarkan dari C3. Sehingga didapatkan C3 = {ABC, ABE}. Berikut adalah tabel nilai *support* *count* untuk C3.

Tabel 6 *Support Count 3-itemset*

| **3-*Itemset*** | ***Support Count*** |
| --------------- | ------------------- |
| ABC             | 2                   |
| ABE             | 2                   |

Ternyata semua data untuk 3-*itemset* ini memenuhi *minimum* *support*, maka didapatkan L3 = {𝐴𝐵𝐶, 𝐴𝐵𝐸} dan dapat dilanjutkan ke tahap selanjutnya yaitu membangkitkan *candidate* *generation* untuk 4-*itemset*. Maka C4 = {ABCE}. Namun setelah dilakukan scanning database ternyata terdapat subset dari itemset ini yang tidak frequent maka C4 = ∅ sehingga L4 = ∅. Sehingga proses dihentikan.

### FP-Growth

Menggunakan *Apriori* memerlukan beberapa pemindaian database untuk memeriksa jumlah dukungan setiap *item* dan *itemset*. Ketika basis datanya besar, ini akan menghabiskan banyak memori dan daya komputasi. Oleh karena itu dibuatlah algoritma FP-*Growth* untuk mengatasi kekurangan tersebut. Metode ini hanya memindai database dua kali dan menggunakan struktur pohon (FP-*Tree*) untuk menyimpan semua informasi. 

*Root* mewakili *null*, setiap *node* mewakili *item*, sedangkan asosiasi node adalah *itemset* dengan urutan yang dipertahankan saat membentuk pohon.

*Pseudocode* dan Penjelasan FP-tree :

1. Deduksi item yang sering dipesan. Untuk item dengan frekuensi yang sama, urutannya diberikan menurut urutan abjad.
1. Bangun pohon FP dari data di atas
1. Dari FP-tree di atas, buatlah FP-conditional tree untuk setiap item (atau itemset).
1. Tentukan Frequent Pattern.

Misalkan tabel berikut ini merupakan *database* transaksi suatu supermarket (data asli, belum dilakukan reduksi dimensi) ditampilkan dalam Tabel di bawah dengan nilai *minimum* *support* yang digunakan adalah 3.

Tabel 7 Database Transaksi Sebelum Reduksi Dimensi

| **TID** | **Item yang dibeli** |
| ------- | -------------------- |
| 1       | f,a,c,d,g,i,m,p      |
| 2       | a,b,c,f,l,m,o        |
| 3       | b,f,h,j,o            |
| 4       | b,c,k,s,p            |
| 5       | a,f,c,e,l,p,m,n      |

Pertama-tama akan dilakukan scanning database untuk melihat nilai frekuensi setiap item. Frekuensi dari item-item yang ada pada database yaitu <(f:4), (c:4), (a:3), (b:3), (m:3), (p:3), (o:2), (l:2), (d:1), (e:1), (g:1), (h:1), (i:1), (j:1), (k:1), (n:1), (s1)>, dimana angka setelah tanda “:” mengindikasikan nilai *support* *count*. Setiap item pada tabel diurutkan dengan urutan menurun.

Pola urutan ini penting sebab setiap bagian dari pohon akan mengikuti pola ini. Item dengan nilai support kurang dari min\_support yang ditentukan akan dikeluarkan dari pengamatan. Item-item yang memenuhi min\_support yaitu u <(f:4), (c:4), (a:3), 

(b:3), (m:3), (p:3)>. Berikut ini adalah kemunculan item yang frequent dalam setiap transaksi yang terbentuk setelah mengeluarkan item yang tidak memenuhi min\_support dan diurutkan sesuai frekuensi.

Tabel 8 Database Transaksi Setelah Reduksi Dimensi

| **TID** | **Item yang dibeli** |
| ------- | -------------------- |
| 1       | f,c,a,m,p            |
| 2       | f,c,a,b,m            |
| 3       | f,b                  |
| 4       | c,b,p                |
| 5       | f,c,a,m,p            |

Setelah didapatkan daftar transaksi yang hanya berisi item yang frequent, langkah selanjutnya yaitu melakukan scanning yang kedua pada transaksi untuk pembentukan *FP-tree*. Akar dari pohon ini akan diberikan label “null”.

1. Hasil pemindaian transaksi yang pertama digunakan untuk membangun cabang yang pertama pada pohon: {(f:1),(c:1),(a:1),(m:1),(p:1). Frequent item pada transaksi yang ditulis berdasarkan urutan pada list frequent item. Berikut ini adalah gambar yang mengilustrasikan pembentukan FP-tree setelah pemindaian pada TID 1.

![alt text](https://github.com/ToKu404/Machine-Learning-Assignment/blob/main/Assets/Tugas1/001.png?raw=true)  

2. Untuk transaksi kedua, karena urutan frequent item <f,c,a,b,m> berbagi awalan <f,c,a> dengan bagian yang  sudah ada <f,c,a,m,p> maka count untuk setiap titik  sepanjang awalan akan meningkat 1, dan titik baru (b:1) dibentuk dan disambungkan sebagai anak dari (a:2) dan titik baru yang lain (m:1) dibentuk dan disambungkan dengan anak dari (b:1). Gambar berikut mengilustrasikan FP-tree setelah pemindaian TID 2.

![alt text](https://github.com/ToKu404/Machine-Learning-Assignment/blob/main/Assets/Tugas1/002.png?raw=true)  

3. Untuk transaksi ketiga, karena frequent item yang tercatat <f,b> hanya berbagi <f> dengan f awalan subtree, maka count f naik 1 dan titik baru (b:1) dibentuk dan disambungkan sebagai anak cabang dari (f:3). Sehingga FP-tree setelah pemindaian TID 3 dapat diilustrasikan dengan gambar sebagai berikut

![alt text](https://github.com/ToKu404/Machine-Learning-Assignment/blob/main/Assets/Tugas1/003.png?raw=true)  

4. Pemindaian pada transaksi keempat membentuk cabang kedua pada pohon <(c:1),(b:1),(p:1). Setelah pemindaian TID 4, ilustrasi FP-tree dapat dilihat pada gambar berikut.

![alt text](https://github.com/ToKu404/Machine-Learning-Assignment/blob/main/Assets/Tugas1/004.png?raw=true)  

5. Pada transaksi terakhir, karena frequent item <f,c,a,m,p> identik dengan yang pertama maka bagian ini berbagi count pada setiap titik sehingga nilainya bertambah 1. Sehingga FP-tree yang dapat terbentuk setelah pemindaian TID 5 adalah sebagai berikut.

![alt text](https://github.com/ToKu404/Machine-Learning-Assignment/blob/main/Assets/Tugas1/005.png?raw=true)  

Untuk memfasilitasi pohon tranversal, suatu kepala item pada tabel dibangun dengan setiap poin pada item dihubungkan dengan kejadian pertama yang muncul pada pohon. Titik dengan nama item yang sama akan dihubungkan dengan urutan titik yang tersambung. Setelah melakukan pemindaian pada semua transaksi, maka pohon yang terbentuk dari semua titik-titik yang terhubung tersebut akan terbentuk seperti pada gambar berikut.

![alt text](https://github.com/ToKu404/Machine-Learning-Assignment/blob/main/Assets/Tugas1/006.png?raw=true)  

Proses penggalian informasi dimulai dari node-link header table yang paling bawah. Berikut ini adalah langkah pembentukan FP-*Growth* (Samuel, 2007). 

1. Membangun conditional pattern base. Conditional pattern base bisa didapatkan melalui FP-*tree* yang terbentuk. Caranya yaitu dengan melihat FP-*tree* yang berisi akhiran 𝑎𝑖 . Setiap lintasan yang tidak mengandung 𝑎𝑖 dibuang. Jadi support count untuk setiap titik adalah nilai support count untuk titik tersebut yang muncul bersama 𝑎𝑖 . Dalam menyebutkan conditional pattern base, hanya prefix nya saja yang disebutkan. 
2. Membangun conditional FP-*tree*. Pada tahap ini support count dari setiap item pada conditional pattern base dijumlahkan. Setiap item yang memiliki support count lebih dari minimal support maka akan dibangkitkan conditional FP-*tree* nya.
3. Pencarian frequent itemset . Jika conditional FP-*tree* merupakan single path, maka untuk mendapatkan frequent itemset dilakukan kombinasi untuk setiap item yang berada pada conditional FP-*tree*. Jika conditional FP-tree bukan merupakan single path maka frequent itemset dibangkitkan secara rekursif.

Berikut ini adalah pembentukan FP-*Growth* untuk contoh sebelumnya.

1. Pembentukan *FP*-*Growth* untuk *suffix* p 

   Berikut ini adalah conditional pattern base untuk suffix p. Dimana untuk semua lintasan yang tidak mengandung p nilai support count sudah dikurangi. Terdapat dua conditional pattern base dengan suffix p yaitu (fcam :2) dan (cb:1). Agar lebih mudah dalam mendapatkan conditional FP-tree untuk suffix p, perhatikan gambar berikut ini.

![alt text](https://github.com/ToKu404/Machine-Learning-Assignment/blob/main/Assets/Tugas1/007.png?raw=true) 

   Berdasarkan Gambar diatas *conditional* *pattern* *base* yang memenuhi *minimal* *support* adalah item c yaitu dengan support *count* 3. Sehingga didapatkan conditional FP-*tree* adalah {(c:3)}|p. Pada suffix p, conditional FP-*tree* yang terbentuk merupakan *single* *path* sehingga untuk mendapatkan frequent itemset dilakukan dengan mengkombinasikan saja conditional FP-*tree*. Jadi frequent itemset yang terbentuk adalah p, cp.

2. Setelah menghilangkan item yang tidak mengandung dalam lintasan, maka *conditional pattern base* yang terbentuk adalah (fca:2) dan (fcab:1). Berikut ini adalah gambar untuk *conditional pattern* yang terbentuk.

![alt text](https://github.com/ToKu404/Machine-Learning-Assignment/blob/main/Assets/Tugas1/008.png?raw=true)    

   Berdasarkan gambar diatas item yang memiliki *support* *count* lebih dari atau sama dengan 3 adalah a, c, f. Sehingga *conditional* FP-*tree* yang terbentuk adalah {(f:3, c:3, a:3)}|m. *Conditional* FP-*tree* yang terbentuk merupakan *single* *path*, sehingga *frequent* *itemset* didapatkan dengan mencari kombinasinya. *Frequent* *itemset* yang terbentuk adalah m, fm, cm, am, fcm, fam, cam, fcam.

   Pada gambar diatas dapat dilihat bahwa *support* *count* untuk item f adalah 2 dan untuk c adalah 1. Karena *support* *count* dari f dan c tidak lebih dari 3 maka untuk suffix b tidak ada *conditional* FP-*tree* yang dibangkitkan. Tidak ada conditional FP-*tree* yang dibangkitkan, sehingga *frequent* itemset yang terbentuk hanya b saja.

3. Pembentukan FP-*Growth* untuk *suffix* a 
    *Conditional* *pattern* base yang terbentuk untuk *suffix* a hanya ada satu yaitu (fc:3). Berikut ini adalah gambar *conditional* *pattern* base yang terbentuk untuk *suffix* a.

![alt text](https://github.com/ToKu404/Machine-Learning-Assignment/blob/main/Assets/Tugas1/009.png?raw=true) 

  *Conditional pattern base* untuk *suffix* a berbentuk *single* *path* maka semua *item* diatas a pasti memenuhi *minimal* *support* *count* karena a memenuhi *minimal* *support* *count*. Jadi *conditional* FP-tree yang terbentuk adalah {(f:3, c:3)}|a. Pada suffix b, conditional FP-*tree* yang terbentuk juga merupakan *single* *path*. Jadi frequent itemset yang terbentuk adalah a, fa, ca, dan fca.

4. Pembentukan FP-*Growth* untuk *suffix* c

   Sama halnya dengan *suffix* a, pada *suffix* c conditional pattern base yang terbentuk hanya ada satu yaitu (f:3). Untuk *suffix* c, *conditional* *pattern* base yang terbentuk adalah seperti pada gambar berikut.
   

![alt text](https://github.com/ToKu404/Machine-Learning-Assignment/blob/main/Assets/Tugas1/010.png?raw=true) 

   Sama halnya dengan *suffix* a, pada *suffix* b *conditional* *pattern* *base* juga merupakan single path. Jadi conditional FP-tree yang terbentuk adalah {(f:3)}|c. Frequent itemset yang terbentuk untuk suffix c adalah c dan fc.

5. Pembentukan FP-Growth untuk *suffix f conditional pattern* base

![alt text](https://github.com/ToKu404/Machine-Learning-Assignment/blob/main/Assets/Tugas1/011.png?raw=true) 

   Berbeda dengan *suffix* yang lainnya, pada *suffix* f tidak ada conditional *pattern* *base* yang terbentuk. Karena tidak ada *conditional* *pattern* *base* yang terbentuk maka tidak ada conditional FP-*tree* yang terbentuk dan *fequent* *itemset* hanya berisi dirinya sendiri yaitu *item* f.

   

   Hasil dari *conditional* *pattern*-*bases*, *conditional* FP-*tree* dan *frequent* *itemset* yang didapatkan dirangkum dalam

| ***Suffix*** | **Conditional Pattern-base** | **Conditional FP-tree** | **Frequent Itemset** |
| :----------: | :--------------------------: | :---------------------: | :------------------: |
|      p       |      {(f cam:2),(cb:1)}      |         {(c:3)}         |          p           |
|      m       |     {(f ca:2),(fcab:1)}      |    {(f:3, c:3, a:3}     |          m           |
|      b       |    {(f ca:1),(f:1),(c:1)}    |            ∅            |          b           |
|      a       |          {(fcc:3)}           |       {(f:3, c:3}       |          m           |
|      c       |           {(f:3)}            |         {(f:3}          |          c           |
|      f       |              ∅               |            ∅            |          f           |



# Implementasi Kode Association Rule Dengan Apriori

Mengimport Library yang akan digunakan


```python
import numpy as np
import pandas as pd
from mlxtend.frequent_patterns import apriori, association_rules
from mlxtend.preprocessing import TransactionEncoder
import matplotlib.pyplot as plt
%matplotlib inline
```

## Contoh 1, Dataset Online Retail

Data yang di gunakan merupakan data transaksi dari sebuah pusat grosir yang melayani transaksi di beberapa negara.


Data Source : https://www.kaggle.com/mashlyn/online-retail-ii-uci

### 1. Meload dan Mengeksplor dataset



```python
from google.colab import drive
drive.mount('/content/drive/')
file = 'drive/My Drive/Dataset/online_retail_II.xlsx'
```

    Drive already mounted at /content/drive/; to attempt to forcibly remount, call drive.mount("/content/drive/", force_remount=True).


Memuat Data Menggunakan library Pandas


```python
df = pd.read_excel(file)
df.head()
```

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Invoice</th>
      <th>StockCode</th>
      <th>Description</th>
      <th>Quantity</th>
      <th>InvoiceDate</th>
      <th>Price</th>
      <th>Customer ID</th>
      <th>Country</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>489434</td>
      <td>85048</td>
      <td>15CM CHRISTMAS GLASS BALL 20 LIGHTS</td>
      <td>12</td>
      <td>2009-12-01 07:45:00</td>
      <td>6.95</td>
      <td>13085.0</td>
      <td>United Kingdom</td>
    </tr>
    <tr>
      <th>1</th>
      <td>489434</td>
      <td>79323P</td>
      <td>PINK CHERRY LIGHTS</td>
      <td>12</td>
      <td>2009-12-01 07:45:00</td>
      <td>6.75</td>
      <td>13085.0</td>
      <td>United Kingdom</td>
    </tr>
    <tr>
      <th>2</th>
      <td>489434</td>
      <td>79323W</td>
      <td>WHITE CHERRY LIGHTS</td>
      <td>12</td>
      <td>2009-12-01 07:45:00</td>
      <td>6.75</td>
      <td>13085.0</td>
      <td>United Kingdom</td>
    </tr>
    <tr>
      <th>3</th>
      <td>489434</td>
      <td>22041</td>
      <td>RECORD FRAME 7" SINGLE SIZE</td>
      <td>48</td>
      <td>2009-12-01 07:45:00</td>
      <td>2.10</td>
      <td>13085.0</td>
      <td>United Kingdom</td>
    </tr>
    <tr>
      <th>4</th>
      <td>489434</td>
      <td>21232</td>
      <td>STRAWBERRY CERAMIC TRINKET BOX</td>
      <td>24</td>
      <td>2009-12-01 07:45:00</td>
      <td>1.25</td>
      <td>13085.0</td>
      <td>United Kingdom</td>
    </tr>
  </tbody>
</table>


Datanya terdiri dari 8 Variabel
1. Invoice : Nomor nota pada setiap pembelian
2. StockCode : Merupakan kode stok dari sebuah barang
3. Description : Deskripsi dari barang tersebut.
4. Quantitiy : Jumlah barang yang di beli pada sebuah transaksi.
5. InvoiceDate : tanggal pembelian
6. Unit Price : Harga per unit barang
7. CustomerID : ID Dari pelanggan
8. Country : Negara dari pelangan.

### 2. Menghapus semua nilai Null

Menghilangkan Spasi sebelum dan setelah variabel Description


```python
df["Description"] = df["Description"].str.strip()
```

Menghapus variabel *invoice* yang kosong


```python
# Mengecek jumlah data yang null dan non-null pada tiap kolom
df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 525461 entries, 0 to 525460
    Data columns (total 8 columns):
     #   Column       Non-Null Count   Dtype         
    ---  ------       --------------   -----         
     0   Invoice      525461 non-null  object        
     1   StockCode    525461 non-null  object        
     2   Description  522530 non-null  object        
     3   Quantity     525461 non-null  int64         
     4   InvoiceDate  525461 non-null  datetime64[ns]
     5   Price        525461 non-null  float64       
     6   Customer ID  417534 non-null  float64       
     7   Country      525461 non-null  object        
    dtypes: datetime64[ns](1), float64(2), int64(1), object(4)
    memory usage: 32.1+ MB

```python
# axis=0 berarti drop semua baris yang kosong
# subset["Invoice"] berarti drop yang kolom invoicenya kosong
# inplace=True berari method ini tidak akan mengembalikan apa-apa (None)
df.dropna(axis=0, subset=['Invoice'], inplace=True)
```

### 3. Menggunakan data yang nilai kolom "Quantity" positif


```python
df["Quantity"].describe()
```


    count    525461.000000
    mean         10.337667
    std         107.424110
    min       -9600.000000
    25%           1.000000
    50%           3.000000
    75%          10.000000
    max       19152.000000
    Name: Quantity, dtype: float64

Karena data quantity mengandung nilai negatif oleh karena itu difilter untuk dengan mengambil yang hanya lebih besar 0


```python
df = df[df["Quantity"]>=0]
df["Quantity"].describe()
```


    count    513135.000000
    mean         11.715412
    std          92.974635
    min           1.000000
    25%           1.000000
    50%           3.000000
    75%          10.000000
    max       19152.000000
    Name: Quantity, dtype: float64

### 4. Memisahkan data sesuai dengan wilayah transaksi


```python
# Mengecek berapa negara berbeda yang terdapat pada database
df["Country"].unique()
```


    array(['United Kingdom', 'France', 'USA', 'Belgium', 'Australia', 'EIRE',
           'Germany', 'Portugal', 'Denmark', 'Netherlands', 'Poland',
           'Channel Islands', 'Spain', 'Cyprus', 'Greece', 'Norway',
           'Austria', 'Sweden', 'United Arab Emirates', 'Finland', 'Italy',
           'Switzerland', 'Japan', 'Unspecified', 'Nigeria', 'Malta',
           'Bahrain', 'RSA', 'Bermuda', 'Hong Kong', 'Singapore', 'Thailand',
           'Israel', 'Lithuania', 'West Indies', 'Lebanon', 'Korea', 'Brazil',
           'Canada', 'Iceland'], dtype=object)

Setelah data dibersihkan selanjutnya adalah membuat keranjang belanja yang dikenali berdasarkan nomor invoice,

Misalnya kita akan membatasi data dengan hanya menggunakan transaksi pada negara **Japan**


```python
# Mengatur agar hanya menggunakan transaksi satu negara saja
df_country = (df[df["Country"] == "Sweden"])
df_country.head()
```

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Invoice</th>
      <th>StockCode</th>
      <th>Description</th>
      <th>Quantity</th>
      <th>InvoiceDate</th>
      <th>Price</th>
      <th>Customer ID</th>
      <th>Country</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>20893</th>
      <td>491059</td>
      <td>21731</td>
      <td>RED TOADSTOOL LED NIGHT LIGHT</td>
      <td>144</td>
      <td>2009-12-09 11:36:00</td>
      <td>1.45</td>
      <td>12487.0</td>
      <td>Sweden</td>
    </tr>
    <tr>
      <th>20894</th>
      <td>491059</td>
      <td>21252</td>
      <td>SET OF MEADOW  FLOWER STICKERS</td>
      <td>30</td>
      <td>2009-12-09 11:36:00</td>
      <td>2.55</td>
      <td>12487.0</td>
      <td>Sweden</td>
    </tr>
    <tr>
      <th>47215</th>
      <td>493806</td>
      <td>POST</td>
      <td>POSTAGE</td>
      <td>1</td>
      <td>2010-01-07 11:31:00</td>
      <td>18.00</td>
      <td>17404.0</td>
      <td>Sweden</td>
    </tr>
    <tr>
      <th>47216</th>
      <td>493806</td>
      <td>22348</td>
      <td>TEA BAG PLATE RED SPOTTY</td>
      <td>1</td>
      <td>2010-01-07 11:31:00</td>
      <td>0.85</td>
      <td>17404.0</td>
      <td>Sweden</td>
    </tr>
    <tr>
      <th>47217</th>
      <td>493806</td>
      <td>22357</td>
      <td>KINGS CHOICE BISCUIT TIN</td>
      <td>1</td>
      <td>2010-01-07 11:31:00</td>
      <td>4.25</td>
      <td>17404.0</td>
      <td>Sweden</td>
    </tr>
  </tbody>
</table>

```python
# Membuat dataframe baru dengan Invoice sebagai index, Description sebagai Column, dan Valuenya berdasarkan Quantity
df_basket = df_country.pivot_table(index='Invoice',columns='Description', values='Quantity', aggfunc='sum')

# Dapat juga menggunakan
# df_basket = df_japan.groupby(["Invoice", "Description"])["Quantity"].sum().unstack()
df_basket
```



<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>Description</th>
      <th>10 COLOUR SPACEBOY PEN</th>
      <th>12 COLOURED PARTY BALLOONS</th>
      <th>12 IVORY ROSE PEG PLACE SETTINGS</th>
      <th>12 PENCIL SMALL TUBE WOODLAND</th>
      <th>12 PENCILS SMALL TUBE RED RETROSPOT</th>
      <th>12 PENCILS SMALL TUBE RED SPOTTY</th>
      <th>12 PENCILS SMALL TUBE SKULL</th>
      <th>12 PENCILS TALL TUBE SKULLS</th>
      <th>12 PENCILS TALL TUBE WOODLAND</th>
      <th>12 PINK ROSE PEG PLACE SETTINGS</th>
      <th>12 RED ROSE PEG PLACE SETTINGS</th>
      <th>20 DOLLY PEGS RETROSPOT</th>
      <th>36 DOILIES DOLLY GIRL</th>
      <th>36 DOILIES SPACEBOY DESIGN</th>
      <th>36 DOILIES VINTAGE CHRISTMAS</th>
      <th>36 PENCILS TUBE RED RETROSPOT</th>
      <th>4 TRADITIONAL SPINNING TOPS</th>
      <th>6 RIBBONS RUSTIC CHARM</th>
      <th>6 ROCKET BALLOONS</th>
      <th>60 CAKE CASES DOLLY GIRL DESIGN</th>
      <th>60 CAKE CASES VINTAGE CHRISTMAS</th>
      <th>60 TEATIME FAIRY CAKE CASES</th>
      <th>72 SWEETHEART FAIRY CAKE CASES</th>
      <th>75 GREEN FAIRY CAKE CASES</th>
      <th>ACRYLIC JEWEL ICICLE, BLUE</th>
      <th>ADVENT CALENDAR GINGHAM SACK</th>
      <th>AIRLINE BAG VINTAGE JET SET RED</th>
      <th>AIRLINE BAG VINTAGE WORLD CHAMPION</th>
      <th>ASSORTED CAKES FRIDGE MAGNETS</th>
      <th>ASSORTED COLOURS SILK FAN</th>
      <th>ASSORTED ICE CREAM FRIDGE MAGNETS</th>
      <th>ASSORTED TUTTI FRUTTI LARGE PURSE</th>
      <th>ASSORTED TUTTI FRUTTI NOTEBOOK</th>
      <th>ASSORTED TUTTI FRUTTI ROUND BOX</th>
      <th>ASSTD DESIGN BUBBLE GUM RING</th>
      <th>BABUSHKA LIGHTS STRING OF 10</th>
      <th>BAG 250g SWIRLY MARBLES</th>
      <th>BAKING SET 9 PIECE RETROSPOT</th>
      <th>BAKING SET SPACEBOY DESIGN</th>
      <th>BALLOON PUMP WITH 10 BALLOONS</th>
      <th>...</th>
      <th>TV DINNER TRAY AIR HOSTESS</th>
      <th>VINTAGE HEADS AND TAILS CARD GAME</th>
      <th>VINTAGE KITCHEN PRINT PUDDINGS</th>
      <th>VINTAGE RED TEATIME MUG</th>
      <th>VINTAGE SNAKES &amp; LADDERS</th>
      <th>WALL TIDY RETROSPOT</th>
      <th>WASH BAG VINTAGE ROSE PAISLEY</th>
      <th>WATERING CAN BLUE ELEPHANT</th>
      <th>WATERING CAN GARDEN MARKER</th>
      <th>WATERING CAN GREEN DINOSAUR</th>
      <th>WATERING CAN PINK BUNNY</th>
      <th>WEEKEND BAG VINTAGE ROSE PAISLEY</th>
      <th>WELCOME  WOODEN BLOCK LETTERS</th>
      <th>WHITE HANGING HEART T-LIGHT HOLDER</th>
      <th>WOOD BLACK BOARD ANT WHITE FINISH</th>
      <th>WOOD STOCKING CHRISTMAS SCANDISPOT</th>
      <th>WOODEN ADVENT CALENDAR CREAM</th>
      <th>WOODEN ADVENT CALENDAR RED</th>
      <th>WOODEN BOX ADVENT CALENDAR</th>
      <th>WOODEN BOX OF DOMINOES</th>
      <th>WOODEN CROQUET GARDEN SET</th>
      <th>WOODEN HAPPY BIRTHDAY GARLAND</th>
      <th>WOODEN HEART CHRISTMAS SCANDINAVIAN</th>
      <th>WOODEN OWLS LIGHT GARLAND</th>
      <th>WOODEN REGATTA BUNTING</th>
      <th>WOODEN SCHOOL COLOURING SET</th>
      <th>WOODEN STAR CHRISTMAS SCANDINAVIAN</th>
      <th>WOODEN TREE CHRISTMAS SCANDINAVIAN</th>
      <th>WOODEN UNION JACK BUNTING</th>
      <th>WOODLAND  HEIGHT CHART STICKERS</th>
      <th>WOODLAND ANIMAL  WRITING SET</th>
      <th>WOODLAND CHARLOTTE BAG</th>
      <th>WOODLAND DESIGN  COTTON TOTE BAG</th>
      <th>WOODLAND PARTY BAG + STICKER SET</th>
      <th>WOODLAND WATER TRANSFER TATTOOS</th>
      <th>WOOLLY HAT SOCK GLOVE ADVENT STRING</th>
      <th>WORLD WAR 2 GLIDERS ASSTD DESIGNS</th>
      <th>ZINC HEART LATTICE T-LIGHT HOLDER</th>
      <th>ZINC METAL HEART DECORATION</th>
      <th>ZINC WILLIE WINKIE  CANDLE STICK</th>
    </tr>
    <tr>
      <th>Invoice</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>491059</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>493806</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>494919</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>240.0</td>
      <td>240.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>496326</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>497496</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>530180</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>12.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>24.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>530206</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>48.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>533818</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>48.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>12.0</td>
      <td>12.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>534190</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>16.0</td>
      <td>NaN</td>
      <td>12.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>12.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>535433</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>8.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>69 rows × 449 columns</p>

```python
df_basket.shape
```


    (69, 449)




```python
# Mengubah NaN menjadi 0
df_basket_clean = df_basket.fillna(0)
df_basket_clean.head()
```

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>Description</th>
      <th>10 COLOUR SPACEBOY PEN</th>
      <th>12 COLOURED PARTY BALLOONS</th>
      <th>12 IVORY ROSE PEG PLACE SETTINGS</th>
      <th>12 PENCIL SMALL TUBE WOODLAND</th>
      <th>12 PENCILS SMALL TUBE RED RETROSPOT</th>
      <th>12 PENCILS SMALL TUBE RED SPOTTY</th>
      <th>12 PENCILS SMALL TUBE SKULL</th>
      <th>12 PENCILS TALL TUBE SKULLS</th>
      <th>12 PENCILS TALL TUBE WOODLAND</th>
      <th>12 PINK ROSE PEG PLACE SETTINGS</th>
      <th>12 RED ROSE PEG PLACE SETTINGS</th>
      <th>20 DOLLY PEGS RETROSPOT</th>
      <th>36 DOILIES DOLLY GIRL</th>
      <th>36 DOILIES SPACEBOY DESIGN</th>
      <th>36 DOILIES VINTAGE CHRISTMAS</th>
      <th>36 PENCILS TUBE RED RETROSPOT</th>
      <th>4 TRADITIONAL SPINNING TOPS</th>
      <th>6 RIBBONS RUSTIC CHARM</th>
      <th>6 ROCKET BALLOONS</th>
      <th>60 CAKE CASES DOLLY GIRL DESIGN</th>
      <th>60 CAKE CASES VINTAGE CHRISTMAS</th>
      <th>60 TEATIME FAIRY CAKE CASES</th>
      <th>72 SWEETHEART FAIRY CAKE CASES</th>
      <th>75 GREEN FAIRY CAKE CASES</th>
      <th>ACRYLIC JEWEL ICICLE, BLUE</th>
      <th>ADVENT CALENDAR GINGHAM SACK</th>
      <th>AIRLINE BAG VINTAGE JET SET RED</th>
      <th>AIRLINE BAG VINTAGE WORLD CHAMPION</th>
      <th>ASSORTED CAKES FRIDGE MAGNETS</th>
      <th>ASSORTED COLOURS SILK FAN</th>
      <th>ASSORTED ICE CREAM FRIDGE MAGNETS</th>
      <th>ASSORTED TUTTI FRUTTI LARGE PURSE</th>
      <th>ASSORTED TUTTI FRUTTI NOTEBOOK</th>
      <th>ASSORTED TUTTI FRUTTI ROUND BOX</th>
      <th>ASSTD DESIGN BUBBLE GUM RING</th>
      <th>BABUSHKA LIGHTS STRING OF 10</th>
      <th>BAG 250g SWIRLY MARBLES</th>
      <th>BAKING SET 9 PIECE RETROSPOT</th>
      <th>BAKING SET SPACEBOY DESIGN</th>
      <th>BALLOON PUMP WITH 10 BALLOONS</th>
      <th>...</th>
      <th>TV DINNER TRAY AIR HOSTESS</th>
      <th>VINTAGE HEADS AND TAILS CARD GAME</th>
      <th>VINTAGE KITCHEN PRINT PUDDINGS</th>
      <th>VINTAGE RED TEATIME MUG</th>
      <th>VINTAGE SNAKES &amp; LADDERS</th>
      <th>WALL TIDY RETROSPOT</th>
      <th>WASH BAG VINTAGE ROSE PAISLEY</th>
      <th>WATERING CAN BLUE ELEPHANT</th>
      <th>WATERING CAN GARDEN MARKER</th>
      <th>WATERING CAN GREEN DINOSAUR</th>
      <th>WATERING CAN PINK BUNNY</th>
      <th>WEEKEND BAG VINTAGE ROSE PAISLEY</th>
      <th>WELCOME  WOODEN BLOCK LETTERS</th>
      <th>WHITE HANGING HEART T-LIGHT HOLDER</th>
      <th>WOOD BLACK BOARD ANT WHITE FINISH</th>
      <th>WOOD STOCKING CHRISTMAS SCANDISPOT</th>
      <th>WOODEN ADVENT CALENDAR CREAM</th>
      <th>WOODEN ADVENT CALENDAR RED</th>
      <th>WOODEN BOX ADVENT CALENDAR</th>
      <th>WOODEN BOX OF DOMINOES</th>
      <th>WOODEN CROQUET GARDEN SET</th>
      <th>WOODEN HAPPY BIRTHDAY GARLAND</th>
      <th>WOODEN HEART CHRISTMAS SCANDINAVIAN</th>
      <th>WOODEN OWLS LIGHT GARLAND</th>
      <th>WOODEN REGATTA BUNTING</th>
      <th>WOODEN SCHOOL COLOURING SET</th>
      <th>WOODEN STAR CHRISTMAS SCANDINAVIAN</th>
      <th>WOODEN TREE CHRISTMAS SCANDINAVIAN</th>
      <th>WOODEN UNION JACK BUNTING</th>
      <th>WOODLAND  HEIGHT CHART STICKERS</th>
      <th>WOODLAND ANIMAL  WRITING SET</th>
      <th>WOODLAND CHARLOTTE BAG</th>
      <th>WOODLAND DESIGN  COTTON TOTE BAG</th>
      <th>WOODLAND PARTY BAG + STICKER SET</th>
      <th>WOODLAND WATER TRANSFER TATTOOS</th>
      <th>WOOLLY HAT SOCK GLOVE ADVENT STRING</th>
      <th>WORLD WAR 2 GLIDERS ASSTD DESIGNS</th>
      <th>ZINC HEART LATTICE T-LIGHT HOLDER</th>
      <th>ZINC METAL HEART DECORATION</th>
      <th>ZINC WILLIE WINKIE  CANDLE STICK</th>
    </tr>
    <tr>
      <th>Invoice</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>491059</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>493806</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>494919</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>240.0</td>
      <td>240.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>496326</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>497496</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 449 columns</p>


### 5. Encode Data

Kita ingin mengencode data basket menjadi data biner. Jadi didefinisikan suatu fungsi yang akan mengubah semua nilai diatas 0 (Terdapat transaksi) menjadi 1, dan yang sama dengan 0 (Tidak terdapat transaksi) tetap 0.


```python
def encode_units(x):
  if x <= 0:
    return 0
  if x >= 1:
    return 1
```

Menerapkan encode data ke dataset basket


```python
df_basket_encode = df_basket_clean.applymap(encode_units)
df_basket_encode.head()
```

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>Description</th>
      <th>10 COLOUR SPACEBOY PEN</th>
      <th>12 COLOURED PARTY BALLOONS</th>
      <th>12 IVORY ROSE PEG PLACE SETTINGS</th>
      <th>12 PENCIL SMALL TUBE WOODLAND</th>
      <th>12 PENCILS SMALL TUBE RED RETROSPOT</th>
      <th>12 PENCILS SMALL TUBE RED SPOTTY</th>
      <th>12 PENCILS SMALL TUBE SKULL</th>
      <th>12 PENCILS TALL TUBE SKULLS</th>
      <th>12 PENCILS TALL TUBE WOODLAND</th>
      <th>12 PINK ROSE PEG PLACE SETTINGS</th>
      <th>12 RED ROSE PEG PLACE SETTINGS</th>
      <th>20 DOLLY PEGS RETROSPOT</th>
      <th>36 DOILIES DOLLY GIRL</th>
      <th>36 DOILIES SPACEBOY DESIGN</th>
      <th>36 DOILIES VINTAGE CHRISTMAS</th>
      <th>36 PENCILS TUBE RED RETROSPOT</th>
      <th>4 TRADITIONAL SPINNING TOPS</th>
      <th>6 RIBBONS RUSTIC CHARM</th>
      <th>6 ROCKET BALLOONS</th>
      <th>60 CAKE CASES DOLLY GIRL DESIGN</th>
      <th>60 CAKE CASES VINTAGE CHRISTMAS</th>
      <th>60 TEATIME FAIRY CAKE CASES</th>
      <th>72 SWEETHEART FAIRY CAKE CASES</th>
      <th>75 GREEN FAIRY CAKE CASES</th>
      <th>ACRYLIC JEWEL ICICLE, BLUE</th>
      <th>ADVENT CALENDAR GINGHAM SACK</th>
      <th>AIRLINE BAG VINTAGE JET SET RED</th>
      <th>AIRLINE BAG VINTAGE WORLD CHAMPION</th>
      <th>ASSORTED CAKES FRIDGE MAGNETS</th>
      <th>ASSORTED COLOURS SILK FAN</th>
      <th>ASSORTED ICE CREAM FRIDGE MAGNETS</th>
      <th>ASSORTED TUTTI FRUTTI LARGE PURSE</th>
      <th>ASSORTED TUTTI FRUTTI NOTEBOOK</th>
      <th>ASSORTED TUTTI FRUTTI ROUND BOX</th>
      <th>ASSTD DESIGN BUBBLE GUM RING</th>
      <th>BABUSHKA LIGHTS STRING OF 10</th>
      <th>BAG 250g SWIRLY MARBLES</th>
      <th>BAKING SET 9 PIECE RETROSPOT</th>
      <th>BAKING SET SPACEBOY DESIGN</th>
      <th>BALLOON PUMP WITH 10 BALLOONS</th>
      <th>...</th>
      <th>TV DINNER TRAY AIR HOSTESS</th>
      <th>VINTAGE HEADS AND TAILS CARD GAME</th>
      <th>VINTAGE KITCHEN PRINT PUDDINGS</th>
      <th>VINTAGE RED TEATIME MUG</th>
      <th>VINTAGE SNAKES &amp; LADDERS</th>
      <th>WALL TIDY RETROSPOT</th>
      <th>WASH BAG VINTAGE ROSE PAISLEY</th>
      <th>WATERING CAN BLUE ELEPHANT</th>
      <th>WATERING CAN GARDEN MARKER</th>
      <th>WATERING CAN GREEN DINOSAUR</th>
      <th>WATERING CAN PINK BUNNY</th>
      <th>WEEKEND BAG VINTAGE ROSE PAISLEY</th>
      <th>WELCOME  WOODEN BLOCK LETTERS</th>
      <th>WHITE HANGING HEART T-LIGHT HOLDER</th>
      <th>WOOD BLACK BOARD ANT WHITE FINISH</th>
      <th>WOOD STOCKING CHRISTMAS SCANDISPOT</th>
      <th>WOODEN ADVENT CALENDAR CREAM</th>
      <th>WOODEN ADVENT CALENDAR RED</th>
      <th>WOODEN BOX ADVENT CALENDAR</th>
      <th>WOODEN BOX OF DOMINOES</th>
      <th>WOODEN CROQUET GARDEN SET</th>
      <th>WOODEN HAPPY BIRTHDAY GARLAND</th>
      <th>WOODEN HEART CHRISTMAS SCANDINAVIAN</th>
      <th>WOODEN OWLS LIGHT GARLAND</th>
      <th>WOODEN REGATTA BUNTING</th>
      <th>WOODEN SCHOOL COLOURING SET</th>
      <th>WOODEN STAR CHRISTMAS SCANDINAVIAN</th>
      <th>WOODEN TREE CHRISTMAS SCANDINAVIAN</th>
      <th>WOODEN UNION JACK BUNTING</th>
      <th>WOODLAND  HEIGHT CHART STICKERS</th>
      <th>WOODLAND ANIMAL  WRITING SET</th>
      <th>WOODLAND CHARLOTTE BAG</th>
      <th>WOODLAND DESIGN  COTTON TOTE BAG</th>
      <th>WOODLAND PARTY BAG + STICKER SET</th>
      <th>WOODLAND WATER TRANSFER TATTOOS</th>
      <th>WOOLLY HAT SOCK GLOVE ADVENT STRING</th>
      <th>WORLD WAR 2 GLIDERS ASSTD DESIGNS</th>
      <th>ZINC HEART LATTICE T-LIGHT HOLDER</th>
      <th>ZINC METAL HEART DECORATION</th>
      <th>ZINC WILLIE WINKIE  CANDLE STICK</th>
    </tr>
    <tr>
      <th>Invoice</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>491059</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>493806</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>494919</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>496326</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>497496</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 449 columns</p>


### 6. Memfilter Transaksi: Hanya untuk Pembelian yang Lebih dari 1 Item

Karena akan dilihat hubungan antara 2 atau lebih item. Jadi kurang bermanfaat jika transaksi hanya membeli satu item. Oleh karena itu, langkah selanjutnya adalah menyaring transaksi yang membeli lebih dari 1 item.


```python
# Filter bekerja dengan melihat jumlah kolom yang nilainya 1 pada tiap baris
# dan Hanya akan mengambil yang nilanya lebih besar atau sama dengan 2 
df_basket_filter = df_basket_encode[(df_basket_encode > 0).sum(axis=1) >= 2]
df_basket_filter.shape
```




    (63, 449)



Visualisasi Jumlah transaksi berdasarkan item yang paling banyak terjual


```python
count = df_basket_filter.loc[:,:].sum()
pop_item = count.sort_values(0, ascending = False).head(10)
pop_item = pop_item.to_frame()
pop_item = pop_item.reset_index()
pop_item = pop_item.rename(columns = {"Description": "items", 0: "count"})

plt.rcParams['figure.figsize'] = (10, 6)
plt.style.use('dark_background')
ax = pop_item.plot.barh(x = 'items', y = 'count')
plt.title('Item paling populer')
plt.gca().invert_yaxis()
```


​    
![png](Tugas01_ML_H071191049_files/Tugas01_ML_H071191049_36_0.png)
​    


### 7. Menerapkan algoritma Apriori


Selanjutnya adalah membuat variabel dimana terdiri dari beberapa barang yang sering terbeli dari seluruh transaksi menggunakan apriori, dengan min_support 0.06.

secara default, apriori mengembalikan index colom item, olehnya ditambahkan parameter use_columnames=True untuk merubah nilai integer ke nama item masing-masing:


```python
# hasil apriori diurutkan berdasarkan nilai support secara menurun
# reset index dan menghapus index yang lama
frq_itemsets = apriori(df_basket_filter, 
                       min_support=0.06,
                       use_colnames=True).sort_values(
                           'support',
                           ascending=False
                       ).reset_index(drop=True)
frq_itemsets.head()
```



<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>support</th>
      <th>itemsets</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0.380952</td>
      <td>(POSTAGE)</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0.222222</td>
      <td>(PACK OF 60 MUSHROOM CAKE CASES)</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0.190476</td>
      <td>(60 TEATIME FAIRY CAKE CASES)</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0.158730</td>
      <td>(SET/20 WOODLAND PAPER NAPKINS)</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0.158730</td>
      <td>(LUNCH BAG SUKI  DESIGN)</td>
    </tr>
  </tbody>
</table>


Menambahkan colom panjang itemset


```python
frq_itemsets['length'] = frq_itemsets["itemsets"].apply(lambda x: len (x))
frq_itemsets.head()
```



<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>support</th>
      <th>itemsets</th>
      <th>length</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0.380952</td>
      <td>(POSTAGE)</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0.222222</td>
      <td>(PACK OF 60 MUSHROOM CAKE CASES)</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0.190476</td>
      <td>(60 TEATIME FAIRY CAKE CASES)</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0.158730</td>
      <td>(SET/20 WOODLAND PAPER NAPKINS)</td>
      <td>1</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0.158730</td>
      <td>(LUNCH BAG SUKI  DESIGN)</td>
      <td>1</td>
    </tr>
  </tbody>
</table>



```python
# Melihat panjang maximal itemset yang terbentuk
frq_itemsets["length"].max()
```


    13



Contoh, Menampilkan kriteria tertentu


```python
# Length 2 support 0.15
frq_itemsets[(frq_itemsets["length"]==2) & (frq_itemsets["support"]>=0.1)]
```



<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>support</th>
      <th>itemsets</th>
      <th>length</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>12</th>
      <td>0.111111</td>
      <td>(60 TEATIME FAIRY CAKE CASES, PACK OF 60 SPACE...</td>
      <td>2</td>
    </tr>
    <tr>
      <th>14</th>
      <td>0.111111</td>
      <td>(TROPICAL  HONEYCOMB PAPER GARLAND, LUNCH BAG ...</td>
      <td>2</td>
    </tr>
    <tr>
      <th>15</th>
      <td>0.111111</td>
      <td>(MAGIC DRAWING SLATE SPACEBOY, MAGIC DRAWING S...</td>
      <td>2</td>
    </tr>
    <tr>
      <th>21</th>
      <td>0.111111</td>
      <td>(PACK OF 60 DINOSAUR CAKE CASES, PACK OF 60 SP...</td>
      <td>2</td>
    </tr>
    <tr>
      <th>22</th>
      <td>0.111111</td>
      <td>(PACK OF 60 MUSHROOM CAKE CASES, PACK OF 60 SP...</td>
      <td>2</td>
    </tr>
    <tr>
      <th>23</th>
      <td>0.111111</td>
      <td>(RED TOADSTOOL LED NIGHT LIGHT, POSTAGE)</td>
      <td>2</td>
    </tr>
    <tr>
      <th>24</th>
      <td>0.111111</td>
      <td>(60 TEATIME FAIRY CAKE CASES, SET/20 WOODLAND ...</td>
      <td>2</td>
    </tr>
  </tbody>
</table>





```python
# Menampilkan entri berdasarkan kolom intemset
frq_itemsets[frq_itemsets["itemsets"] == {"RED TOADSTOOL LED NIGHT LIGHT","POSTAGE"}]
```

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>support</th>
      <th>itemsets</th>
      <th>length</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>23</th>
      <td>0.111111</td>
      <td>(RED TOADSTOOL LED NIGHT LIGHT, POSTAGE)</td>
      <td>2</td>
    </tr>
  </tbody>
</table>




### 8. Mencari Asosiasi antara *frequently itemset*

Membangun sebuah variabel yang memiliki aturan aturan asosiasi dari masin-masing barang, variabel rules merupakan hasil dari fungsi yang mencari asosiasi dimana data yang di gunakan berasal dari frq_itemsets , dengan nilai minium dari lift ratio nya adalah 1



```python
rules = association_rules(frq_itemsets, 
                  metric='lift', 
                  min_threshold=1)
rules = rules.sort_values(["confidence", "lift"],ascending=[False,False]).reset_index(drop=True)
rules.head()
```



<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>antecedents</th>
      <th>consequents</th>
      <th>antecedent support</th>
      <th>consequent support</th>
      <th>support</th>
      <th>confidence</th>
      <th>lift</th>
      <th>leverage</th>
      <th>conviction</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>(PACK OF 60 MUSHROOM CAKE CASES, EASTER CRAFT ...</td>
      <td>(FELTCRAFT DOLL EMILY)</td>
      <td>0.079365</td>
      <td>0.079365</td>
      <td>0.079365</td>
      <td>1.0</td>
      <td>12.6</td>
      <td>0.073066</td>
      <td>inf</td>
    </tr>
    <tr>
      <th>1</th>
      <td>(PACK OF 60 MUSHROOM CAKE CASES, EASTER CRAFT ...</td>
      <td>(PINK BLUE FELT CRAFT TRINKET BOX)</td>
      <td>0.079365</td>
      <td>0.079365</td>
      <td>0.079365</td>
      <td>1.0</td>
      <td>12.6</td>
      <td>0.073066</td>
      <td>inf</td>
    </tr>
    <tr>
      <th>2</th>
      <td>(PACK OF 60 MUSHROOM CAKE CASES, EASTER CRAFT ...</td>
      <td>(EASTER CRAFT IVY WREATH WITH CHICK)</td>
      <td>0.079365</td>
      <td>0.079365</td>
      <td>0.079365</td>
      <td>1.0</td>
      <td>12.6</td>
      <td>0.073066</td>
      <td>inf</td>
    </tr>
    <tr>
      <th>3</th>
      <td>(PACK OF 60 MUSHROOM CAKE CASES, EASTER CRAFT ...</td>
      <td>(EASTER CRAFT 4 CHICKS)</td>
      <td>0.079365</td>
      <td>0.079365</td>
      <td>0.079365</td>
      <td>1.0</td>
      <td>12.6</td>
      <td>0.073066</td>
      <td>inf</td>
    </tr>
    <tr>
      <th>4</th>
      <td>(PACK OF 60 MUSHROOM CAKE CASES, EASTER CRAFT ...</td>
      <td>(FELTCRAFT DOLL EMILY, DINOSAUR PARTY BAG + ST...</td>
      <td>0.079365</td>
      <td>0.079365</td>
      <td>0.079365</td>
      <td>1.0</td>
      <td>12.6</td>
      <td>0.073066</td>
      <td>inf</td>
    </tr>
  </tbody>
</table>


Kita dapat melakukan filter untuk nilai lift ratio minimal 6 dan tingkat confidence minimal 0.8


```python
rules = rules[(rules['lift'] >= 6) &
       (rules['confidence'] >= 0.8)]
rules
```



<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>antecedents</th>
      <th>consequents</th>
      <th>antecedent support</th>
      <th>consequent support</th>
      <th>support</th>
      <th>confidence</th>
      <th>lift</th>
      <th>leverage</th>
      <th>conviction</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>(PACK OF 60 MUSHROOM CAKE CASES, EASTER CRAFT ...</td>
      <td>(FELTCRAFT DOLL EMILY)</td>
      <td>0.079365</td>
      <td>0.079365</td>
      <td>0.079365</td>
      <td>1.000000</td>
      <td>12.6000</td>
      <td>0.073066</td>
      <td>inf</td>
    </tr>
    <tr>
      <th>1</th>
      <td>(PACK OF 60 MUSHROOM CAKE CASES, EASTER CRAFT ...</td>
      <td>(PINK BLUE FELT CRAFT TRINKET BOX)</td>
      <td>0.079365</td>
      <td>0.079365</td>
      <td>0.079365</td>
      <td>1.000000</td>
      <td>12.6000</td>
      <td>0.073066</td>
      <td>inf</td>
    </tr>
    <tr>
      <th>2</th>
      <td>(PACK OF 60 MUSHROOM CAKE CASES, EASTER CRAFT ...</td>
      <td>(EASTER CRAFT IVY WREATH WITH CHICK)</td>
      <td>0.079365</td>
      <td>0.079365</td>
      <td>0.079365</td>
      <td>1.000000</td>
      <td>12.6000</td>
      <td>0.073066</td>
      <td>inf</td>
    </tr>
    <tr>
      <th>3</th>
      <td>(PACK OF 60 MUSHROOM CAKE CASES, EASTER CRAFT ...</td>
      <td>(EASTER CRAFT 4 CHICKS)</td>
      <td>0.079365</td>
      <td>0.079365</td>
      <td>0.079365</td>
      <td>1.000000</td>
      <td>12.6000</td>
      <td>0.073066</td>
      <td>inf</td>
    </tr>
    <tr>
      <th>4</th>
      <td>(PACK OF 60 MUSHROOM CAKE CASES, EASTER CRAFT ...</td>
      <td>(FELTCRAFT DOLL EMILY, DINOSAUR PARTY BAG + ST...</td>
      <td>0.079365</td>
      <td>0.079365</td>
      <td>0.079365</td>
      <td>1.000000</td>
      <td>12.6000</td>
      <td>0.073066</td>
      <td>inf</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>1712750</th>
      <td>(60 TEATIME FAIRY CAKE CASES, PACK OF 60 MUSHR...</td>
      <td>(FELTCRAFT DOLL MOLLY)</td>
      <td>0.095238</td>
      <td>0.126984</td>
      <td>0.079365</td>
      <td>0.833333</td>
      <td>6.5625</td>
      <td>0.067271</td>
      <td>5.238095</td>
    </tr>
    <tr>
      <th>1712751</th>
      <td>(60 TEATIME FAIRY CAKE CASES, PACK OF 60 MUSHR...</td>
      <td>(PACK OF 60 DINOSAUR CAKE CASES)</td>
      <td>0.095238</td>
      <td>0.126984</td>
      <td>0.079365</td>
      <td>0.833333</td>
      <td>6.5625</td>
      <td>0.067271</td>
      <td>5.238095</td>
    </tr>
    <tr>
      <th>1712767</th>
      <td>(JUMBO STORAGE BAG SUKI)</td>
      <td>(TROPICAL  HONEYCOMB PAPER GARLAND)</td>
      <td>0.079365</td>
      <td>0.111111</td>
      <td>0.063492</td>
      <td>0.800000</td>
      <td>7.2000</td>
      <td>0.054674</td>
      <td>4.444444</td>
    </tr>
    <tr>
      <th>1712768</th>
      <td>(JUMBO STORAGE BAG SUKI, LUNCH BAG SUKI  DESIGN)</td>
      <td>(TROPICAL  HONEYCOMB PAPER GARLAND)</td>
      <td>0.079365</td>
      <td>0.111111</td>
      <td>0.063492</td>
      <td>0.800000</td>
      <td>7.2000</td>
      <td>0.054674</td>
      <td>4.444444</td>
    </tr>
    <tr>
      <th>1712769</th>
      <td>(JUMBO STORAGE BAG SUKI)</td>
      <td>(TROPICAL  HONEYCOMB PAPER GARLAND, LUNCH BAG ...</td>
      <td>0.079365</td>
      <td>0.111111</td>
      <td>0.063492</td>
      <td>0.800000</td>
      <td>7.2000</td>
      <td>0.054674</td>
      <td>4.444444</td>
    </tr>
  </tbody>
</table>
<p>1704577 rows × 9 columns</p>


### Visualisasi Hasil

Support Vs Confidence


```python
plt.scatter(rules['support'], rules['confidence'], alpha=0.6, color = 'red')
plt.xlabel('support')
plt.ylabel('confidence')
plt.title('Support vs Confidence')
plt.show()
```


​    
![png](Tugas01_ML_H071191049_files/Tugas01_ML_H071191049_53_0.png)
​    


Support vs Lift


```python
plt.scatter(rules['support'], rules['lift'], alpha=0.5)
plt.xlabel('support')
plt.ylabel('lift')
plt.title('Support vs Lift')
plt.show()
```


​    
![png](Tugas01_ML_H071191049_files/Tugas01_ML_H071191049_55_0.png)
​    


Lift vs Cofidence


```python
fit = np.polyfit(rules["lift"], rules["confidence"], 1)
fit_fn = np.poly1d(fit)
plt.plot(rules["lift"], rules["confidence"], "yo", rules["lift"], 
fit_fn(rules["lift"]))
```




    [<matplotlib.lines.Line2D at 0x7fb8b611d0d0>,
     <matplotlib.lines.Line2D at 0x7fb8b60d9f50>]


![png](Tugas01_ML_H071191049_files/Tugas01_ML_H071191049_57_1.png)
​    


## Contoh 2, Dataset Groceries Store

Data yang digunakan merupakan data transaksi toko makanan

Data Source : https://www.kaggle.com/irfanasrullah/groceries

### 1. Meload dan Mengeksplor data


```python
file_2 = 'drive/My Drive/Dataset/groceries_store.csv'
df_2 = pd.read_csv(file_2)
df_2.head()
```



<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Item(s)</th>
      <th>Item 1</th>
      <th>Item 2</th>
      <th>Item 3</th>
      <th>Item 4</th>
      <th>Item 5</th>
      <th>Item 6</th>
      <th>Item 7</th>
      <th>Item 8</th>
      <th>Item 9</th>
      <th>Item 10</th>
      <th>Item 11</th>
      <th>Item 12</th>
      <th>Item 13</th>
      <th>Item 14</th>
      <th>Item 15</th>
      <th>Item 16</th>
      <th>Item 17</th>
      <th>Item 18</th>
      <th>Item 19</th>
      <th>Item 20</th>
      <th>Item 21</th>
      <th>Item 22</th>
      <th>Item 23</th>
      <th>Item 24</th>
      <th>Item 25</th>
      <th>Item 26</th>
      <th>Item 27</th>
      <th>Item 28</th>
      <th>Item 29</th>
      <th>Item 30</th>
      <th>Item 31</th>
      <th>Item 32</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>4</td>
      <td>citrus fruit</td>
      <td>semi-finished bread</td>
      <td>margarine</td>
      <td>ready soups</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>3</td>
      <td>tropical fruit</td>
      <td>yogurt</td>
      <td>coffee</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>whole milk</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>pip fruit</td>
      <td>yogurt</td>
      <td>cream cheese</td>
      <td>meat spreads</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>other vegetables</td>
      <td>whole milk</td>
      <td>condensed milk</td>
      <td>long life bakery product</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>


```python
df_2.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 9835 entries, 0 to 9834
    Data columns (total 33 columns):
     #   Column   Non-Null Count  Dtype 
    ---  ------   --------------  ----- 
     0   Item(s)  9835 non-null   int64 
     1   Item 1   9835 non-null   object
     2   Item 2   7676 non-null   object
     3   Item 3   6033 non-null   object
     4   Item 4   4734 non-null   object
     5   Item 5   3729 non-null   object
     6   Item 6   2874 non-null   object
     7   Item 7   2229 non-null   object
     8   Item 8   1684 non-null   object
     9   Item 9   1246 non-null   object
     10  Item 10  896 non-null    object
     11  Item 11  650 non-null    object
     12  Item 12  468 non-null    object
     13  Item 13  351 non-null    object
     14  Item 14  273 non-null    object
     15  Item 15  196 non-null    object
     16  Item 16  141 non-null    object
     17  Item 17  95 non-null     object
     18  Item 18  66 non-null     object
     19  Item 19  52 non-null     object
     20  Item 20  38 non-null     object
     21  Item 21  29 non-null     object
     22  Item 22  18 non-null     object
     23  Item 23  14 non-null     object
     24  Item 24  8 non-null      object
     25  Item 25  7 non-null      object
     26  Item 26  7 non-null      object
     27  Item 27  6 non-null      object
     28  Item 28  5 non-null      object
     29  Item 29  4 non-null      object
     30  Item 30  1 non-null      object
     31  Item 31  1 non-null      object
     32  Item 32  1 non-null      object
    dtypes: int64(1), object(32)
    memory usage: 2.5+ MB


### 2. Mentransformasi bentuk dataframe


```python
df_2.shape
```


    (9835, 33)



Merubah bentuk dari dataframe ke list, agar bisa dibentuk ulang ke dataframe yang baru.
Disini saya membatasi jumlah baris dari 9835 ke 1000 karena memori saya tidak sanggup mengolahnya


```python
records = []
for i in range (0, 1000):
  records.append([str(df_2.values[i,j]) for j in range(1,33) if str(df_2.values[i,j])!='nan'])
```


```python
records[0]
```


    ['citrus fruit', 'semi-finished bread', 'margarine', 'ready soups']



Transformasi data frame dengan TransactionEncoder()


```python
TE = TransactionEncoder()
arr = TE.fit(records).transform(records)
df_2_transf = pd.DataFrame(arr, columns = TE.columns_)
df_2_transf
```



<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Instant food products</th>
      <th>UHT-milk</th>
      <th>abrasive cleaner</th>
      <th>artif. sweetener</th>
      <th>baby cosmetics</th>
      <th>baking powder</th>
      <th>bathroom cleaner</th>
      <th>beef</th>
      <th>berries</th>
      <th>beverages</th>
      <th>bottled beer</th>
      <th>bottled water</th>
      <th>brandy</th>
      <th>brown bread</th>
      <th>butter</th>
      <th>butter milk</th>
      <th>cake bar</th>
      <th>candles</th>
      <th>candy</th>
      <th>canned beer</th>
      <th>canned fish</th>
      <th>canned fruit</th>
      <th>canned vegetables</th>
      <th>cat food</th>
      <th>cereals</th>
      <th>chewing gum</th>
      <th>chicken</th>
      <th>chocolate</th>
      <th>chocolate marshmallow</th>
      <th>citrus fruit</th>
      <th>cleaner</th>
      <th>cling film/bags</th>
      <th>cocoa drinks</th>
      <th>coffee</th>
      <th>condensed milk</th>
      <th>cookware</th>
      <th>cream cheese</th>
      <th>curd</th>
      <th>curd cheese</th>
      <th>decalcifier</th>
      <th>...</th>
      <th>root vegetables</th>
      <th>rubbing alcohol</th>
      <th>rum</th>
      <th>salad dressing</th>
      <th>salt</th>
      <th>salty snack</th>
      <th>sauces</th>
      <th>sausage</th>
      <th>seasonal products</th>
      <th>semi-finished bread</th>
      <th>shopping bags</th>
      <th>skin care</th>
      <th>sliced cheese</th>
      <th>snack products</th>
      <th>soap</th>
      <th>soda</th>
      <th>soft cheese</th>
      <th>softener</th>
      <th>soups</th>
      <th>sparkling wine</th>
      <th>specialty bar</th>
      <th>specialty cheese</th>
      <th>specialty chocolate</th>
      <th>specialty fat</th>
      <th>spices</th>
      <th>spread cheese</th>
      <th>sugar</th>
      <th>sweet spreads</th>
      <th>syrup</th>
      <th>tea</th>
      <th>tropical fruit</th>
      <th>turkey</th>
      <th>vinegar</th>
      <th>waffles</th>
      <th>whipped/sour cream</th>
      <th>white bread</th>
      <th>white wine</th>
      <th>whole milk</th>
      <th>yogurt</th>
      <th>zwieback</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>...</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>1</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>...</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
    </tr>
    <tr>
      <th>2</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>...</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>3</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>...</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
    </tr>
    <tr>
      <th>4</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>...</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>995</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>...</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>996</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>...</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>True</td>
      <td>False</td>
      <td>True</td>
      <td>True</td>
      <td>False</td>
    </tr>
    <tr>
      <th>997</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>...</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>998</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>...</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>999</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>...</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
    </tr>
  </tbody>
</table>
<p>1000 rows × 156 columns</p>

```python
df_2_transf.isna().sum().sum()
```


    0



### 3. Memfilter transaksi dan hanya mengambil yang melakukan pembelian lebih dari 1 item


```python
df_2_filter = df_2_transf[(df_2_transf > 0).sum(axis=1) >= 2]
df_2_filter.shape
```


    (784, 156)

Visualisasi tipe makanan yang paling banyak di jual


```python
count = df_2_filter.loc[:,:].sum()
pop_item = count.sort_values(0, ascending = False).head(10)
pop_item = pop_item.to_frame()
pop_item = pop_item.reset_index()
pop_item = pop_item.rename(columns = {"index": "items", 0: "count"})

plt.rcParams['figure.figsize'] = (10, 6)
plt.style.use('dark_background')
ax = pop_item.plot.barh(x = 'items', y = 'count')
plt.title('Item paling populer')
plt.gca().invert_yaxis()
```


![png](Tugas01_ML_H071191049_files/Tugas01_ML_H071191049_74_0.png)
​    


### 4. Menerapkan algoritma apriori

Selanjutnya adalah membuat variabel dimana terdiri dari beberapa barang yang sering terbeli dari seluruh transaksi menggunakan apriori, dengan min_support 0.05.

secara default, apriori mengembalikan index colom item, olehnya ditambahkan parameter use_columnames=True untuk merubah nilai integer ke nama item masing-masing:


```python
# hasil apriori diurutkan berdasarkan nilai support secara menurun
# reset index dan menghapus index yang lama
frq_is = apriori(df_2_filter, 
                       min_support=0.05,
                       use_colnames=True).sort_values(
                           'support',
                           ascending=False
                       ).reset_index(drop=True)
frq_is['length'] = frq_is["itemsets"].apply(lambda x: len (x))
frq_is.head()
```

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>support</th>
      <th>itemsets</th>
      <th>length</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0.326531</td>
      <td>(whole milk)</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0.271684</td>
      <td>(rolls/buns)</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0.227041</td>
      <td>(other vegetables)</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0.182398</td>
      <td>(soda)</td>
      <td>1</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0.158163</td>
      <td>(bottled water)</td>
      <td>1</td>
    </tr>
  </tbody>
</table>

```python
# Melihat panjang maximal itemset yang terbentuk
frq_is["length"].max()
```


    2



### 5. Mencari asosiasi diantara *Frequent itemsets*


```python
rul = association_rules(frq_is, 
                  metric='lift', 
                  min_threshold=1).sort_values(["confidence", "lift"],ascending=[False,False]).reset_index(drop=True)
rul.head()
```

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>antecedents</th>
      <th>consequents</th>
      <th>antecedent support</th>
      <th>consequent support</th>
      <th>support</th>
      <th>confidence</th>
      <th>lift</th>
      <th>leverage</th>
      <th>conviction</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>(yogurt)</td>
      <td>(whole milk)</td>
      <td>0.154337</td>
      <td>0.326531</td>
      <td>0.071429</td>
      <td>0.462810</td>
      <td>1.417355</td>
      <td>0.021033</td>
      <td>1.253689</td>
    </tr>
    <tr>
      <th>1</th>
      <td>(root vegetables)</td>
      <td>(whole milk)</td>
      <td>0.139031</td>
      <td>0.326531</td>
      <td>0.062500</td>
      <td>0.449541</td>
      <td>1.376720</td>
      <td>0.017102</td>
      <td>1.223469</td>
    </tr>
    <tr>
      <th>2</th>
      <td>(other vegetables)</td>
      <td>(whole milk)</td>
      <td>0.227041</td>
      <td>0.326531</td>
      <td>0.091837</td>
      <td>0.404494</td>
      <td>1.238764</td>
      <td>0.017701</td>
      <td>1.130920</td>
    </tr>
    <tr>
      <th>3</th>
      <td>(root vegetables)</td>
      <td>(other vegetables)</td>
      <td>0.139031</td>
      <td>0.227041</td>
      <td>0.054847</td>
      <td>0.394495</td>
      <td>1.737553</td>
      <td>0.023281</td>
      <td>1.276554</td>
    </tr>
    <tr>
      <th>4</th>
      <td>(soda)</td>
      <td>(rolls/buns)</td>
      <td>0.182398</td>
      <td>0.271684</td>
      <td>0.062500</td>
      <td>0.342657</td>
      <td>1.261236</td>
      <td>0.012945</td>
      <td>1.107971</td>
    </tr>
  </tbody>
</table>
