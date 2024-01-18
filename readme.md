**GIT DASAR**

--CONFIGURATION--

1. setelah kita selesai menginstall git, hal pertama yang wajib kita lakukan adalah melakukan konfigurasi
2. yang paling utama yang perlu kita konfigurasi diawal adalah user name dan user email kita. Ini berfungsi untuk nantinya setiap kita melakukan perubahan didalam project git, maka user name dan user email akan ikut disisipkan didalamnya supaya ketahuan siapa yang melakukan perubahan tersebut.
3. untuk melakukan configurasi user name, kita dapat melakukannya dengan menulis perintah berikut di dalam terminal : git config --global user.name "namanya siapa". misal : git config --global user.name "ahmad arifin"
4. untuk melakukan configurasi user email, kita dapat melakukannya dengan menulis perintah berikut di dalam terminal : git config --global user.email "emailnya". misal : git config --global user.email "ahmadarifin@gmail.com"

--INTEGRASI GIT DENGAN VISUAL STUDIO CODE--

1. Agar mempermudah dalam menggunakan git, kita akan menjadikan visual studio code sebagai default editor dan default diff tool untuk git. Ini berfungsi untuk mengkonfigurasi git kalau2 kita nantinya ingin melihat perberdaan versi git satu ke versi git yang lainnya.
2. untuk melakukan integrasi vscode caranya adalah dengan melakukan konfigurasi pada git dengan perintah :

- git config --global core.editor "code --wait"
- git config --global diff.tool "default-difftool"
- git config --global difftool.default-difftool.cmd "code --wait --diff \$LOCAL \$REMOTE"

--MELIHAT SELURUH KONFIGURASI--

1. untuk melihat seluruh konfigurasi git yang telah kita lakukan, kita hanya perlu menjalankan perintah : git config --list --show-origin

--REPOSITORY--

1. Repository merupakan sebutan project di git. Jadi kalau kita membuat project baru itu namanya kita bikin repository bari
2. kita bisa membuat folder kosong atau folder yang sudah berisi file, lalu kita akan membuatnya sebagai git repository

-- MEMBUAT REPOSITORY--

1. untuk membuat repository, kita hanya perlu menggunakan perintah : "git init" didalam folder yang yang akan kita jadikan sebagai git repository
2. setelah membuat git repository, kita bisa melihat ada folder baru dengan nama .git
3. folder .git merupakan folder yang berisikan database Git, folder ini tidak boleh di ubah dan dihapus karena akan mempengaruhi repository git yang sudah kita buat

-- MELIHAT PERUBAHAN YANG TERJADI DI DALAM GIT REPOSITORY--

1. untuk melihat perubahan apa saja yang sudah terjadi didalam git repository, kita bisa menjalankan perintah : git status

--THE THREE STATES--

1. git memiliki tiga state terhadap file kita yaitu: modified, staged dan committed
2. Modified artinya kita mengubah (menambah, mengedit, menghapus) file, namun belum disimpan secara permanen ke repository (masih di working directory)
3. staged artinya kita menandai modifikasi yang kita lakukan terhadap file akan disimpan secara permanen ke repository (perubahan sudah didalam stagging area)
4. committed artinya data sudah aman disimpan di repository (perubahan sudah didalam repository)

--THREE SECTION--

1. Tiga state sebelumnya dilakukan di section yang berbeda-beda, yaitu working directory, staging area (stagging index) dan repository
2. saat kita melakukan modifikasi file, itu dilakukan di working directory. Jadi semua kegiatan modifikasi file, itu dilakukan di working directory
3. jika kita ingin menandai 1 atau 2 file yang sudah kita modifikasi didalam working directory untuk siap dicommit kedalam repository, itu sebenarnya kita melakukan pemindahan file tersebut dari working directory ke dalam stagging area
4. Stagging area merupakan section dimana file sudah disiapkan untuk disimpan secara permanen ke dalam repository (ini masih disiapkan saja jadi masih belum disimpan secara permanen). di stagging area semua informasi perubahan file akan disimpan. Jadi saat kita melakukan modifikasi terhadap 5 file lalu menandai hanya 3 file maka 3 file berada di stagging area dan 2 file masih di working directory. kemudian saat kita melakukan commit, maka 3 file yang ada di stagging area tersebut akan disimpan secara permanen kedalam git repository.
5. Repository merupakan tempat dimana semua file dan database riwayat versi file disimpan

--DIAGRAM THREE TREE--

1. pertama kita melakukan modifikasi file di working directory
2. selanjutnya kita melakukan perintah git add pada file-file yang kita modifikasi tersebuat maka file2 tersebut akan berpindah dari working directory ke stagging area atau stagging index
3. kemudian kita melakukan perintah git commit maka semua file yang berada di stagging area atau stagging index akan disimpan ke dalam repository

--SNAPSHOT--

1. biasanya kita melakukan perubahan ke beberapa file secara bersamaan, semua perubahan yang yang kita lakukan akan direkam dan kita menyebutnya sebagai snapshot.
2. snapshot berisikan semua perubahan yang terjadi disemua file yang kita commit. jadi jika kita melakukan modifikasi 5 file dan memasukkan 5 file tersebut ke stagging index kemudian melakukan commit, maka semua modifikasi yang sudah kita lakukan di dalam 5 file tersebut disebut snapshot
3. setiap snapshot menghasilkan hash untuk memverifikasi perubahan tersebut valid atau tidak (hash ini juga bisa disebut id dari suatu snapshot). jadi jika nanti kita ingin mencari suatu snapshot maka kita tinggal memasukkan hash tersebut sebagai kata kuncinya

--HASH--

1. setiap snapshot yang kita lakukan akan menghasilkan hash sebagai identitas snapshotnya
2. hash merupakan checksum untuk menghitung perubahan yang terjadi
3. git menggunakan algoritma SHA-1 untuk menghitung hash karena algoritma ini terkenal sederhana dan ringan
4. hash dibutuhkan untuk menjaga data integrity. sehinggan tiap snapshot yang sudah kita lakukan tidak bisa diubah. Jikalau kita merubah isi dari snapshotnya maka secara otomatis merusak hash yang sudah dibuat

--HEAD--

1. head merupakan pointer menuju hash yang paling akhir (sederhananya menuju commit paling baru)
2. karena kadang sangat menyulitkan jika harus menuliskan hash value, jika kita ingin menuju ke hash paling baru kita bisa gunakan kata kunci HEAD

--MENAMBAH FILE--

1. untuk menambahkan file baru ke repository, jita cukup membuat filenya saja di dalam project git kita
2. secara otomatis file yang kita tambahkan akan berada di working directory
3. secara default saat kita menambahkan file baru, file tersebut tidak akan di track perubahannya karena git menganggap semua perubahan yang sudah kita lakukan adalah menambah file baru
4. supaya perubahan yang kita lakukan pada file di track oleh git, kita harus pindahkan file tersebut dari working directory ke stagging area (stagging index)

-- MEMINDAHKAN FILE KE STAGGING INDEX--

1. untuk menambahkan file yang sudah kita tambahkan atau modifikasi dari working directory ke dalam stagging index, kita hanya perlu menjalankan perintah : git add namaFile . Misalnya git add file1.txt
2. jika filenya lebih dari satu, kita bisa menjalankan perintah : git add file1.txt file2.txt dst

-- MENYIMPAN SEMUA YANG ADA DI STAGGING INDEX KE REPOSITORY (COMMIT)--

1. untuk menyimpan semua file atau perubahan yang ada di dalam stagging index ke dalam repository secara permanen, kita hanya perlu menjalankan perintah : git commit -m "pesan atau keterangan dari commitnya apa". Misalnya : git commit -m "menambah file1.txt"

--MERUBAH ISI FILE--

1. untuk melakukan perubahan terhadap isi dari file yang sudah dicommit ke repository, kita cukup lakukan perubahan terhadap file yang sudah ada di repository tersebut.
2. maka secara otomatis git akan mendeteksi perubahan tersebut dan memasukkan perubahan yang kita lakukan kedalam working directory
3. sama seperti menambah file, jika kita ingin menyimpan perubahan tersebut secara permanen ke dalam repository, maka kita pindahkan perubahan yang kita lakukan ke dalam stagging index dengan perintah git add namaFIleYangDirubah kemudian menyimpan perubahan yang sudah ada di stagging index ke dalam repository dengan melakukan git commit -m "keterangan commitnya"

--MELIHAT PERUBAHAN YANG DILAKUAKAN PADA SUATU FILE--

1. ketika kita melakukan perubahan pada suatu file, git secara otomatis mendeteksi bahwa file tersebut sudah berubah
2. kadang kita ingin melihat perubahan apa yang terjadi didalam suatu file, kita bisa menggunakan perintah git diff maka secara otomatis git akan menampilkan perubahan apa yang dilakukan

--MENGHAPUS FILE--

1. untuk menghapus file yang ada di dalam repository, kita cukup menghapus filenya yang ada didalam folder project kita.
2. secara otomatis git akan mendeteksi file yang hilang. Jadi jika kita mencoba menghapus salah satu file yang ada didalam folder project kita, maka git bisa tau bahwa ada file yang hilang atau dihapus
3. sama seperti menambah dan merubah, jika kita ingin menyimpan penghapusannya secara permanen di dalam repository, kita harus menambahkan operasi tersebut ke dalam stagging index, kemudian melakukan commit ke repository (kita melakukan hal ini supaya di snapshot terbaru kita, file2 yang sudah kita hapus di working directory juga ikut terhapus di repository)

--MEMBATALKAN PENAMBAHAN FILE YANG MASIH DI WORKING DIRECTORY--

1. jika kita menambahkan file di working directory, lalu kita ingin mematalkan penambahannya, caranya cukup sederhana kita hanya perlu menghapus file yang sudah kita tambahkan tersebut, atau kita juga bisa menggunakan perintah : git clean -f untuk menghapus semua file yang sudah kita tambahkan ke working directory.
2. note : perintah git clean -f hanya menghapus file-file yang baru saja kita tambahkan ke working directory saja (file-file ini belum pernah di tambahkan ke tagging index ataupun di commit ke repository). Jadi file-file yang sudah ada di stagging index atau sudah di commit ke repository tidak akan ikut terhapus.

--MEMBATALKAN PERUBAHAN FILE YANG MASIH DI WORKING DIRECTORY--

1. jika kita merubah isi dari suatu file kemudian ingin membatalkan perubahan tersebut, kita bisa menggunakan perintah : git restore namafileyangsudahdiubah
2. note : perintah git restore hanya bisa membatalkan perubahan yang masih ada di working directory saja. Jadi jika kita sudah terlanjur memindahkan perubahan tersebut ke stagging index ataupun repository, maka git restore tidak dapat membatalkan perubahan tersebut

--MEMBATALKAN PENGHAPUSAN FILE YANG MASIH DI WORKING DIRECTORY--

1. jika kita menghapus suatu file kemudian ingin membatalkan penghapusan tersebut, kita bisa menggunakan perintah : git restore namafileyangsudahdihapus
2. note : perintah git restore hanya bisa membatalkan penghapusan yang masih ada di working directory saja. Jadi jika kita sudah terlanjur memindahkan penghapusan tersebut ke stagging index ataupun repository, maka git restore tidak dapat membatalkan penghapusan tersebut

--MEMBATALKAN MODIFIKASI FILE YANG SUDAH ADA DI STAGGING INDEX--

1. perintah git restore dan git clean hanya dapat dilakukan ketika membatalkan modifikasi yang terjadi di working directory
2. itu artinya jika perubahan terlanjur kita masukkan ke stagging index, maka untuk membatalkannya kita perlu mengembalikan posisi file tersebut dari stagging index ke working directory terlebih dahulu
3. caranya adalah menggunakan perintah : git restore --staged namafileyangmaudibatalkan
4. setelah file berada di working directory, barulah kita bisa membatalkan modifikasinya menggunakan perintah git restore namafileyangmaudibatalkan

--MEMBATALKAN MODIFIKASI FILE YANG SUDAH DI COMMIT KE REPOSITORY--

1. Jika perubahan yang kita lakukan terlanjur di commit ke repository, maka perubahan tersebut tidak akan bisa di batalkan lagi.
2. yang bisa kita lakukan untuk mengatasi masalah tersebut adalah dengan rollback commit (reset commit) atau revert commit

--COMMIT LOG (MELIHAT RIWAYAT COMMIT)--

1. git adalah distributed version control, itu artinya git memiliki sebuah kekurangan yaitu semua riwayat perubahan akan disimpan secara local di dalam komputer kita.
2. ini menyebabkan semakin lama repository kita akan semakin besar ukurannya, namun keuntungannya, kita bisa melihat semua riwayat perubahan yang sudah kita commit ke dalam repository atau bisa disebut commit log.
3. untuk melihat commit log, kita bisa menggunakan perintah : git log

--COMMIT LOG SEDERHANA--

1. kadang kita hanya ingin melihat commit log messagenya saja atau istilahnya adalah versi sederhana dari commit lognya saja
2. untuk menampilkan commit log secara sederhana, kita dapat menggunakan perintah : git log --oneline

--GRAPH--

1. saat nanti kita sudah mengerti tentang git branching, kadang kita ingin melihat hubungan antar commit log
2. hal ini bisa kita lakukan menggunakan perintah : git log --oneline --graph (ini sangat membantu saat menghadapi commit yang bercabang atau commit yang sudah complex)

--MENAMPILKAN DETAIL DARI SUATU COMMIT--

1. jika kita ingin melihat detail perubahan apa saja yang terjadi pada sebuah commit, kita dapat menggunakan perintah : git show hashdaricommityanginginditampilkan

--COMPARE COMMIT--

1. git memiliki fitur untuk membandingkan antara commit satu dengan commit yang lainnya
2. namun membandingkan disini adalah membandingkan antar snapshot (commit) yang sudah kita tentukan bukan perubahan yang terjadi pada commit a sampai commit b
3. misalnya pada commit sebelumnya kita pernah menambahkan file3.txt kedalam repository lalu menghapusnya, namun jika kita membandingkan antara commit pertama dan terakhir, hasilnya hanyalah perbandingan antar file1 dan file2 karena file3 tidak ada di commit pertama maupun commit terakhir (kita sudah menghapus file3 dipertengahan commit)
4. hal ini dikarenakan membandingkan commit bukanlah membandingkan perubahan yang pernah terjadi melainkan membandingkan isi dari commit a dan commit b saja (commit selain itu tidak ikut dibandingkan)
5. untuk membandingkan commit, kita bisa gunakan perintah : git diff hash1 hash2

--COMPARE COMMIT DENGAN DIFFTOOL--

1. sebelumnya kita sudah melakukan konfigurasi git menggunakan vscode untuk melihat diff
2. jika kita ingin menggunakan vscode untuk melihat perbandingan antar commit, kita dapat menggunakan perintah : git difftool hash1 hash2

--RENAME FILE--

1. hal paling menarik dari git yaitu git dapat mendeteksi saat kita merename suatu file
2. secara sederhana rename file merupakan operasi gabungan antara menghapus file lalu menambah file baru dengan isi yang sama (ini yang terjadi saat file yang di rename masih di working directory)
3. namun git bisa otomatis mendeteksi jika terjadi perubahan nama file, karena isi file sebagian besar masih sama (ini yang terjadi saat file yang direname sudah ada di stagging index)

--RESET COMMIT--

1. sebelumnya kita sudah tahu bahwa kita tidak dapat membatalkan perubahan yang sudah terlanjut dicommit. Jadi bagaimana jika kita memang ingin tetap membatalkan perubahan tersebut?
2. untuk kasus seperti itu, kita dapat melakukan reset commit.
3. reset commit merupakan mekanisme dimana kita menggeser HEAD ponter dari commit terbaru ke posisi commit yang kita inginkan dan ketika kita melakukan commit baru setelah melakukan operasi reset, maka commit setelah head baru akan ditimpa dengan commit baru.
4. misalnya kita memiliki 5 commit kemudian kita melakukan reset commit ke commit ke 3 maka posisi HEAD pointer akan bergeser dari commit ke 5 ke commit ke 3. selanjutnya kita melakukan commit baru maka secara otomatis commit ke 4 dan ke 5 akan tertimpa oleh commit baru tersebut (sederhanya commit ke 4 dan ke 5 akan terhapus).
5. untuk melakukan reset commit, kita dapat menggunakan perintah : git reset <mode> hashdaricommityangkitamau
6. ada beberapa mode pengaturan saat kita melakukan reset commit yaitu soft, mixed dan hard

--MODE PADA GET RESET--

1. soft merupakan mode menggeser HEAD pointer pada repository tanpa melakukan perubahan apapun pada stagging index dan working directory. Ini adalah mode reset paling aman karena perubahan-perubahan yang kita lakukan masih tersimpan di stagging index dan working directory dan jika kita ingin membatalkan reset, kita tinggal melakukan commit ulang ke repository saja. format perintah : git reset --soft hashdaricommityangkitamau
2. mixed (default) merupakan mode menggeser HEAD pointer pada repository lalu merubah isi stagging index menjadi sama seperti posisi HEAD saat ini, namun tidak mengubah apapun di working directory. format perintah : git reset --mixed hashdaricommityangkitamau
3. hard merupakan mode menggeser HEAD pointer pada repository lalu merubah isi stagging index dan working directory menjadi sama seperti posisi HEAD saat ini. format perintah : git reset --hard hashdaricommityangkitamau

--REWRITE RIWAYAT COMMIT--

1. perlu diingat kita dapat menggeser kembali HEAD pointer ke posisi commit terbaru dengan catatan kita belum menambahkan commit baru apapun ke dalam repository
2. misalnya kita punya 5 commit lalu kita menggeser HEAD pointer ke posisi commit ke 3. Kita bisa menggeser kembali HEAD ponter ke posisi commit ke 5 ataupun ke 4 asalkan kita belum pernah menambahkan 1 pun commit ke dalam repository setelah kita melakukan operasi reset.

--AMEND COMMIT--

1. kadang saat kita sudah melakukan commit, kita lupa ada beberapa hal yang perlu dimodifikasi.
2. biasanya kita akan melakukan reset dengan model soft ke commit sebelumnya supaya modifikasi yang sudah kita commit tadi kembali ke stagging index, kemudian kita tambahkan modifikasi yang terlupanak tadi dan selanjutnya kita akan melakukan commit ulang.
3. dari pada melakukan reset secara manual seperti cara diatas, kita bisa menambahkan perubahan ke commit terbaru (ditambahkan ke commit yang ada HEAD Pointernya) yang sudah kita buat tanpa melakukan reset dengan menggunakan perintah git commit --amend -m "keterangan commit".
4. perlu di ingat, amend commit akan mengubah hash commit karena secara otomatis data perubahan yang dicommit bertambah (maka dari itu amend commit hanya bisa digunakan untuk menambahkan modifikasi pada commit (snapshot) terbaru saja (tidak bisa digunakan selain commit terbaru karena akan merusak commit setelahnya))
5. contoh penerapan amend commit ialah misal kita membuat file3.txt dan mencommitnya ke repository. Lalu kita lupa untuk mengisi file3.txt yang sudah kita commit tersebut. Dari pada kita mengisi file3.txt lalu membuat commit baru, kita bisa memanfaatkan amend commit ini untuk menambahkan isi dari file3.txt ke dalam commit yang sudah terlanjur kita lakukan tadi.

--KEMBALI KE VERSI FILE SEBELUMNYA (CHECKOUT)--

1. kadang kita menghadapi kasus dimana file yang sudah kita commit ke repository terjadi masalah dan kita ingin untuk melihat versi file sebelumnya dari file yang bermasalah tersebut (versi file sebelum modifikasi terakhir).
2. git memiliki fitur dimana kita dapat melihat versi file pada commit sebelum-sebelumnya (sederhananya kita dapat melihat isi dari suatu file pada commit tertentu itu seperti apa).
3. saat kita ambil versi file sebelumnya, file tersebut akan berada di stagging index (versi terbaru dari file tersebut juga akan digantikan dengan versi file yang dipilih. tapi tenang saja kita dapat mengembalikan file tersebut ke versi terbarunya dengan perintah git restore --staged namafile lalu git restore namafile)
4. untuk melihat versi sebelumnya dari suatu file, kita bisa menggunakan perintah : git checkout hashcommityangkitatentukan -- namafileyanginginkitalihatversisebelumnya
5. misalnya kita membuat file dengan nama file1.txt lalu mengisinya kemudian melakukan commit ke repository lalu kita merubah isi dari file1 tersebut lalu mencommitnya lagi ke repository kemudian tiba tiba file1 tersebut terjadi masalah kemudian kita ingin melihat versi dari file1 sebelum dilakukan perubahan maka kita dapat melakukannya dengan perintah git checkout hashdaricommitsebelumkitamelakukanperubahanpadafile1 -- file1.txt
6. note : saat kita melakukan git checkout kita tidak perlu khawatir versi file terbaru akan dihapus dari repository karena versi terbaru dari file tersebut akan tetap ada direpository

--KEMBALI KE SNAPSHOT(COMMIT) SEBELUMNYA--

1. sama seperti kembali ke versi file sebelumnya, git juga memiliki fitur seperti mesin waktu, dimana kita bisa kembali ke snapshot sebelumnya.
2. kita bisa menentukan snapshot mana yang menjadi tujuan menggunakan hash dari commit snapshot yang diinginkan
3. kita bisa menuju snapshot tertentu menggunakan perintah : git checkout hashdaricommityangdipilih
4. berbeda dengan git reset yang akan menghapus commit2 setelah commit yang dipilih secara permanen dari repository, dengan menggunakan git checkout, commit2 setelah commit yang dipilih akan tetap tersimpan di dalam repository dengan aman
5. jika ingin kembali ke commit terbaru, kita bisa menggunakan perintah git checkout namabranch

--SEKILAS TENTANG GIT BRANCH--

1. secara default saat kita membuat git repository, maka akan dibuatkan branch secara otomatis
2. untuk melihat nama branch saat ini, kita bisa menggunakan perintah git branch --show-current

--MEMBATALKAN COMMIT MENGGUNAKAN REVERT COMMIT--

1. git memiliki fitur yang namanya revert commit, fitur ini berfungsi untuk membatalkan commit yang sudah kita lakukan dengan cara membuat commit baru yang isinya melakukan kebalikan dari apa saja yang sudah kita lakukan di commit yang dibatalkan.
2. misalnya pada commit yang kita batalkan tersebut terdapat aksi menambah file maka rivert akan menghapus file tersebut dari repository, jika kita merubah isi file maka rivert akan menghapus perubahan yang kita lakukan pada file tersebut dan jika kita menghapus file maka rivert akan mengembalikan file yang sudah kita hapus tersebut ke repository.
3. contoh kasusnya adalah jika kita sudah melakukan commit data dan isi dari commit tersebut adalah melakukan perubahan text dari mark ke carl, kemudian kita melakukan rivert pada commit tersebut, maka git secara otomatis akan membuat commit baru dengan melakukan perubahan text dari carl ke mark.
4. untuk melakukan revert commit, kita bisa gunakan perintah : git revert hashdaricommityanginginkitabatalkan

--MENGABAIKAN FILE (GIT IGNORE)--

1. kadang kita tidak ingin menyimpan (track) beberapa file tidak penting ke git repository. Contohnya seperti file log, hasil kompilasi, dan lain sebagainya. kita tidak membutuhkan file2 seperti contoh diatas disimpan secara permanen direpository
2. Untungnya git memiliki fitur ignore, dimana kita dapat meminta git untuk tidak mentrack / menyimpan file-file tersebut ke dalam git repository.
3. Untuk menggunakan fitur ini, pertama-tama kita harus membuat file baru dengan nama .gitignore
4. Kemudian kita bisa mengisi file .gitignore yang telah dibuat tadi dengan nama file atau folder yang tidak kita inginkan ditrack / simpan ke dalam git repository. (lihat file .gitignore untuk lebih jelasnya)

--BLAME--

1. pada saat kita membuat kode program bersama tim, kadang kita ingin tahu siapa saja yang menambahkan baris kode program pada suatu file tertentu dan apa saja yang ditambahkan
2. untungnya git memiliki fitur yang bernama blame. Fitur ini berfungsi untuk mencari tahu, siapa saja yang menambahkan perubahan pada file dan juga untuk mengetahui commit perubahannya yang mana.
3. untuk menggunakan fitur ini, caranya cukup simple yaitu menggunakan perintah : git blame namafileyangingindiperiksa
4. urutan penampilan datanya adalah sebagai berikut : HashCommit (namaOrangYangMelakukanPerubahan tanggal diubah jam diubah) perubahanya

--ALIAS--

1. git memiliki fitur alias
2. dengan fitur alias, kita bisa menambahkan nama lain dari perintah git tertentu
3. misalnya kita bisa menambahkan perintah co atau komit untuk nama lain dari commit
4. atau misal menambahkan alias logone untuk nama lain dari log --oneline
5. untuk menambahkan alias kita dapat menggunakan perintah : git config --global alias.namaAlias namaPerintahGitYangInginDiJadikanAlias
6. misal : git config --global alias.komit commit
7. misal : git config --global alias.logone "log --oneline"

**GIT BRANCHING**

--PENGENALAN GIT BRANCHING--

1. saat ini, hampir semua version control system pasti mendukung fitur yang namanya branching
2. branching adalah kita membuat timeline baru yang berbeda dengan timeline utamanya (mudahnya branch adalah lokasi tempat kita menempatkan commit di repository)
3. biasanya timeline utama atau branch utama itu disebut dengan master atau main (sebelumnya kita melakukan beberapa commit dan commit tersebut tersimpan di branch master (branch utama))
4. saat kita membuat timeline branch baru, semua perubahan (commit) yang sudah kita lakukan di branch baru tersebut tidak akan merusak (merubah) timeline utama (gampangnya saat kita melakukan commit di branch baru, maka commit tersebut hanya akan tersimpan di branch baru tersebut (tidak akan tersimpan di branch lainnya termasuk branch utama)).
5. oleh karena itu, fitur branching ini sangat cocok digunakan ketika kita ingin menambahkan fitur baru ke dalam project kita di repository, karena jika ternyata fitur baru yang kita buat terjadi masalah dan masih belum menemukan silusinya, kita tinggal pindah ke branch utama karena di branch utama (branch lainnya), fitur baru yang bermasalah tersebut tidak tersimpan. Dengan melakukan ini, kita bisa menyelesai kan fitur lainnya tanpa ada gangguan dari fitur baru yang bermasalah tersebut. (gampangnya jika terjadi masalah, masalahnya hanya ada di branch tempat kita menyimpan fitur baru tersebut saja)
6. Git sendiri tidak membatasi jumlah branch yang bisa kita buat, jadi kita bisa bebas membuat branch sebanyak apapun

--KAPAN BRANCH ITU DIPERLUKAN?--

1. Dalam pengembangan perangkat lunak, branch biasanya dibuat ketika kita ingin menambahkan fitur baru.
2. karena saat kita menambahkan fitur baru di branch baru, kita tidak perlu takut melakukan kesalah di brach utama. (Jika terjadi kesalahan di fitur baru yang di buat, branch utama tidak akan terpengaruh)
3. Ketika fitur baru yang kita buat di branch baru tersebut sudah selesai dan siap untuk digunakan, kita dapat melakukan merge (menggabungkan) fitur baru yang sudah selesai tersebut dengan branch utama (branch master atau main).
4. Tidak hanya saat menambahkan fitur baru, kita dapat menggunakan fitur branch ini pada saat project yang sudah kita upload terjadi masalah (error). Kita dapat membuat branch baru kemudian kita melakukan perbaikan masalah di branch baru tersebut kemudian pada saat perbaikan masalah telah selesai, kita akan melakukan merge (menggabungkan) kembali branch baru tersebut dengan branch utama. Kegiatan tersebut biasa disebut hotfix

--MELIHAT BRANCH SAAT INI--

1. Secara default, saat kita memulai untuk membuat project di git, git akan secara otomatis membuat branch utama yang bernama master atau main.
2. Untuk melihat nama branch yang saat ini kita tempati, kita bisa gunakan perintah : git branch --show-current

--MEMBUAT BRANCH BARU--

1. untuk membuat branch baru, kita dapat menggunakan perintah : git branch namaBranchBaru
2. Pada saat kita membuat branch baru, secara otomatis branch baru tersebut akan dimulai dari commit terbaru dari posisi branch kita saat ini. Misal jika kita membuat branch baru saat posisi kita sedang berada di branch master, maka branch baru yang kita buat tersebut akan dimulai dari commit terbaru dari branch master. Jadi saat kita membuat branch baru branch baru tersebut akan mengacu pada commit terakhir dari branch master (disini git masih belum melakukan percabangan karena kita belum melakukan commit apapun di branch yang baru kita buat). Saat kita membuat commit baru di branch baru, maka git akan bercabang.
3. note : jika kita membuat branch baru, kita tidak akan secara otomatis berpindah dari branch kita saat ini ke branch baru yang sudah kita buat. Jika kita ingin pindah posisi dari branch kita saat ini ke branch baru yang sudah kita buat, maka kita harus melakukannya secara manual

--MELIHAT SEMUA BRANCH--

1. Untuk melihat daftar semua branch yang ada di dalam repository, kita bisa menggunakan perintah : git branch --list atau git branch
2. Perlu diingat tanda (bintang) didalam list branch yang ditampilkan menandakan posisi branch saat ini kita berada. Misal posisi kita saat ini berada di branch master, maka pada list branch yang ditampilkan, akan muncul tanda (bintang) pada branch master

--PINDAH BRANCH KE BRANCH LAIN--

1. Setelah membuat branch baru, kita tidak akan pindah ke branch baru tersebut secara otomatis
2. untuk pindah branch ke branch lain, kita dapat menggunakan perintah : git switch namaBranchYangDiInginkan atau git checkout namaBranchYangDiInginkan

--MENGUBAH NAMA BRANCH--

1. Jika kita melakukan kesalahan dalam pembuatan nama branch, kita juga dapat melakukan perubahan nama branch (rename branch).
2. namun untuk merubah nama branch, kita perlu pindah terlebih dahulu ke branch yang ingin kita ubah namanya.
3. setelah pindah ke branch yang ingin diubah, kita bisa menggunakan perintah : git branch -m namaBranchBaru untuk merubah nama dari branch

--MENGHAPUS BRANCH--

1. jika sebuah branch sudah tidak digunakan lagi, idealnya kita harus menghapus branch tersebut supaya branch mudah untuk dipelihara
2. namun untuk menghapus branch, kita perlu pindah terlebih dahulu dari branch yang ingin kita hapus tersebut. Misal kita ingin menghapus branch development, maka pertama-tama kita harus pindah dari branch development ke branch lain contohnya ke branch master kemudian kita dapat menghapus branch development tersebut.
3. setelah pindah dari branch yang ingin dihapus, kita bisa menggunakan perintah : git branch -d namaBranchYangInginDiHapus atau git branch --delete namaBranchYangInginDIHapus untuk menghapus branch yang diinginkan

--MULTIPLE BRANCH--

1. pada kenyataannya, saat kita membuat project, kita biasanya akan membuat banyak sekali branch
2. untungnya git mendukung yang namanya multiple branch, itu artinya kita dapat membuat branch sebanyak apapun tanpa khawatir karena git bisa menanganinya dengan baik

--MERGE BRANCH (MENGGABUNGKAN)--

1. merge merupakan proses dimana kita melakukan penggabungan (penyatuan) 2 buah branch. Misalnya perubahan yang dilakukan di branch a digabungkan ke branch b
2. merge biasanya dilakukan setelah kita selesai membuat fitur (kode program) di dalam sebuat branch kemudian ingin menggabungkan fitur tersebut ke branch lain, misalnya digabungkan ke branch utama (master)
3. saat kita melakukan merge, branch yang sudah digabungkan tidak akan dihapus secara otomatis, itu artinya kita masih tetap dapat melakukan commit di branch tersebut. Misalnya kita melakukan merge branch a ke branch utama (master), setelah kita melakukan merge, branch a dan branch utama tidak akan dihapus secara otomatis oleh git dan kita juga tetap bisa menambahkan commit baru di branch a maupun branch utama. Sederhananya branch a dan branch utama akan tetap ada di repository.
4. Jika kita ingin menghapus branch yang sudah di merge, kita perlu melakukannya secara manual.
5. Perlu diingat : saat melakukan merge branch, maka yang digabungkan itu perubahan-perubahan yang kita lakukan sebelum kita melakukan perintah merge itu saja yang digabungkan, itu artinya jika kita melakukan commit baru setelah melakukan merge, maka commit tersebut tidak akan secara otomatis di merge. Jadi jika kita menambahkan commit baru lalu ingin menggabungkannya, maka kita wajib melakukan merge ulang secara manual

--MELAKUKAN MERGE--

1. untuk melakukan merge, pertama kita perlu pindah ke branch dimana lokasi merge akan kita lakukan. Misalnya kita akan melakukan merge branch a ke dalam branch master, maka kita perlu pindah ke branch master terlebih dahulu sebelum melakukan proses merge.
2. setelah pindah ke branch yang diinginkan, kemudian kita dapat melakukan proses merge dengan perintah : git merge namaBranchYangInginDiMerge. Misalnya git merge a
3. artinya perubahan dari namabranchyangdiinginkan akan di merge ke dalam branch saat ini kita berada.
4. Saat kita melakukan merge, maka git secara otomatis membuat commit baru di dalam branch saat ini kita berada yang isinya penggabungan perubahan2 yang sudah kita lakukan di branch yang kita merge. Misal kita melakukan merge branch a ke dalam branch master. Maka git akan secara otomatis membuat commit baru di dalam branch master yang isinya penggabungan perubahan2 yang sudah kita lakukan di dalam branch a.

--MERGE C0NFLICT--

1. dalam pembuatan suatu project (aplikasi) bersama team, biasanya setiap engineer akan melakukan penambahan kode program di repository secara parallel
2. Biasanya setiap programmer akan membuat branch nya masing-masing kemudian setelah fitur yang dikerjakan selesai mereka akan melakukan merge branch nya ke branch utama (master)
3. Saat menulis kode program, tidak bisa dipungkiri bahwa kadang beberapa engineer akan melakukan perubahan pada file yang sama di dalam branch yang berbeda. Misalnya engineer a merubah isi dari file1.txt di dalam branch a kemudian engineer b juga merubah isi dari file1.txt di dalam branch b.
4. Dan ketika engineer tersebut melakukan merge, maka akan terjadi error atau biasa dipanggil conflict
5. Hal ini bisa terjadi karena sebuah file diubah di lebih dari 1 branch pada waktu yang bersamaan. Sehingga ketika di merge, akan muncul conflict dan kita perlu melakukan yang namanya merge conflict
6. Jika terjadi conflict, maka kita wajib memperbaikinya secara manual kemudian setelah proses perbaikan selesai, maka kita wajib untuk melakukan commit untuk menyimpan perbaikan yang sudah kita lakukan ke dalam repository
7. Saat terjadi merge conflict, seluruh file perubahan yang tidak conflict dari branch yang kita merge akan secara otomatis berada di stagging index sedangkan seluruh file perubahan yang conflict dari branch yang kita merge akan berada di working directory. Misal pada branch a kita merubah 2 file yang itu file1.txt dan file2.txt kemudian saat kita melakukan merge branch a ke branch master, ternyata terjadi pada file1.txt conflict, oleh karena itu git akan secara otomatis menempatkan file1.txt di working directory sedangkan file2.txt di stagging index.

--MEMBATALKAN MERGE YANG CONFLICT--

1. Kadang ada kasus dimana saat melakukan merge, terjadi conflict pada banyak file kemudian kita ingin membatalkan merge yang sudah kita lakukan.
2. Untuk membatalkan merge, kita bisa gunakan perintah git merge --abort
3. perlu di ingat merge hanya bisa dibatalkan hanya pada saat terjadi conflict saja

--MEMPERBAIKI CONFLICT--

1. saat terjadi conflict, kita perlu memperbaikinya secara manual
2. dan setelah perbaikan selesai dilakukan, maka kita perlu melakukan commit perbaikan tersebut ke repository

--CHERRY PICK--

1. saat kita melakukan merge, maka semua perubahan yang kita commit pada branch yang kita pilih akan digabungkan ke branch tujuan.
2. kadang ada kasus dimana saat kita membuat kode program di sebuah branch kita ingin melakukan merge, namun tidak ingin untuk menggabungkan semua perubahan yang kita commit pada branch ke dalam branch tujuan. Atau sederhananya kita cuma ingin menggabungkan beberapa commit saja.
3. Untungnya git memiliki fitur yang bernama cherry pick. Cherry pick merupakan fitur yang digunakan untuk mengambil commit dari branch manapun kemudian di merge ke dalam branch lokasi kita saat ini

--MELAKUKAN CHERRY PICK--

1. misal sekarang kita ingin melakukan merge branch a, namun kita tidak ingin merge semua commit yang kita lakukan di branch a
2. misal saja di branch a kita membuat 4 commit dan kita hanya ingin merge commit ke 1 dan commit ke 3 saja
3. maka kita bisa melakukan cherry pick untuk commit tersebut menggunakan perintah : git cherry-pick hashDariCommitYangInginDiMerge

--TAG--

1. Tag merupakan fitur dimana kita dapat menandai hash dari sebuah commit
2. Prinsip kerja dari tag mirip dengan HEAD Pointer yaitu melakukan reference ke sebuah commit
3. Jika HEAD pointer hanya melakukan reference ke commit terbaru pada branch posisi kita berada saat ini, Maka tag sedikit berbeda. Tag dapat melakukan reference ke commit manapun yang kita mau.
4. Kalau kita ingin membuat sebuah reference ke sebuah commit yang kita mau, kita dapat menggunakan fitur tag ini
5. Dalam pengembangan perangkat lunak, biasanya Tag digunakan sebagai penanda versi rilis dari aplikasi kita. Misalnya Tag 1.0.0, Tag 1.0.2, dan seterusnya.
6. Karena Tag merupakan reference ke sebuah commit, Jadi kita dapat memberi tag ke commit didalam branch manapun yang kita mau.

--MEMBUAT TAG--

1. Perlu untuk diingat, Tag adalah sesuatu yang bersifat unik. Itu artinya jika kita sudah membuat tag dengan nama A, maka kita tidak dapat membuat tag dengan nama yang sama lagi. Kita dapat membuat tag sebanyak apapun asalkan setiap tag memiliki nama yang berbeda-beda.
2. Untuk membuat tag, kita dapat menggunakan perintah : git tag namaTag hashDariCommitYangInginDiBeriTag

--MENAMPILKAN SEMUA TAG--

1. untuk menampilkan semua tag yang ada di dalam repository, kita dapat menggunakan perintah : git tag -l atau git tag --list

--CHECKOUT KE TAG--

1. seperti yang sudah dibahas sebelumnya, dengan git kita dapat melihat isi snapshot (commit) sebelumnya dengan perintah git checkout hashCommitYangInginKitaLihat.
2. Sekarang kita juga dapat melihat isi snapshot (commit) sebelumnya tanpa harus menggunakan hashCommit melainkan cukup menggunakan namaTag
3. untuk melihat snapshot sebelumnya menggunakan tag, kita dapat menggunakan perintah : git checkout namaTagYangInginDiLihatSnapshotnya
4. perlu di ingat perintah diatas hanya bisa digunakan untuk melihat snapshot (commit) yang sudah diberi tag saja. Jika suatu snapshot tidak diberi tag, maka perintah tersebut tidak dapat digunakan.

--MENGUBAH NAMA TAG--

1. Kadang saat membuat tag, ada kalanya kita salah memberi nama tag. Sayangnya tidak ada cara untuk mengubah nama tag yang sudah terlanjur dibuat.
2. Jika kita menghadapi kasus diatas, solusinya adalah kita bisa membuat tag baru ke commit yang sama, lalu menghapus tag yang lama.

--MENGHAPUS TAG--

1. Untuk menghapus tag. kita dapat menggunakan perintah : git tag -d namatagyangingindihapus atau git tag --delete namatagyangingindihapus
2. Note : menghapus tag tidak akan secara otomatis menghapus commitnya. itu artinya hanya tagnya saja yang akan dihapus.

--STASH (SIMPAN PERUBAHAN SEMENTARA)--

1. kadang ada kasus dimana kita sedang melakukan perubahan di suatu branch, namun perubahannya masih belum siap di simpan direpository (perubahan tersebut belum siap untuk dicommit), misal perubahan tersebut masih di working directory atau stagging index.
2. lalu kita ingin secepatnya melakukan perubahan di branch lain dan menunda dulu pekerjaan di branch saat ini. Misalnya kita sedang membuat suatu fitur disebuah branch lalu tiba-tiba terjadi masalah di branch utama yang harus secepatnya untuk di perbaiki. Sementara fitur yang sedang kita kerjakan masih belum siap untuk di commit ke dalam repository.
3. jika perubahan yang kita lakukan di branch saat ini belum siap di commit ke repository, kita dapat menyimpan perubahan2 tersebut secara sementara ke dalam stash
4. stash adalah sebuah tempat dimana kita dapat menyimpan perubahan yang ada di working directory atau stagging index secara sementara supaya branch saat ini menjadi bersih kembali dan kita dapat pindah ke branch lain dengan aman tanpa membawa perubahan yang ada di working directory atau stagging index yang terjadi di branch saat ini ke branch lain saat melakukan switch branch (perpindahan branch).

--ERROR KETIKA PINDAH BRANCH--

1. secara default, ketika kita melakukan perpindahan branch, git akan secara pintar membawa perubahan yang terjadi di branch saat ini ke branch tujuan pindah.
2. akan tetapi jika ternyata terdapat conflict pada branch saat ini, maka kita tidak dapat pindah ke branch lain sebelum conflict tersebut di perbaiki.
3. Jika kita ingin tetap pindah branch meskipun di branch saat ini masih terdapat conflict, maka solusinya adalah menyimpan semua perubahan di working directory dan stagging index secara sementara di dalam stash terlebih dahulu kemudian kita dapat pindah branch dengan aman tanpa terjadi error saat switch branch.

--MENYIMPAN PERUBAHAN KE STASH--

1. untuk menyimpan secara sementara semua perubahan yang terjadi di working directory dan stagging index, kita bisa menggunakan stash
2. Untuk menyimpan ke stash, kita bisa menggunakan perintah : git stash push -m "pesan stash"
3. Jika kita ingin melihat semua stash yang kita simpan, kita dapat menggunakan perintah : git stash list
4. Untuk melihat detail perubahan yang kita simpan di dalam suatu stash, kita dapat menggunakan perintah : git stash show idDariStashyanginginDilihat
5. Note : id dari stash bersifat auto increment yang dimulai dari angka 0

--MENGAMBIL PERUBAHAN DI STASH--

1. jika kita ingin mengambil kembali perubahan yang sudah kita simpan di stash, kita dapat menggunakan perintah : git stash apply idDariStashYangInginDiAmbil
2. Jika kita menjalankan perintah di atas, maka semua perubahan yang di simpan didalam stash tersebut akan dikembalikan ke working directory dan stagging index
3. Jika kita ingin menghapus stash yang sudah tidak diperlukan, kita bisa menggunakan perintah : git stash drop idDariStashYangInginDihapus
4. Jika kita ingin menghapus semua stash yang sudah kita simpan, kita bisa menggunakan perintah : git stash clear

--REBASE--

1. sebelumnya untuk menggabungkan 2 buah branch, kita dapat menggunakan yang namanya merge
2. Sebenarnya ada lain untuk menggabungkan 2 buah branch yaitu menggunakan fitur rebase
3. Akan tetapi fitur rebase ini konsepnya berbeda dari merge
4. saat menggunakan merge, misal kita ingin menggabungkan branch a yang berisi 2 commit, ke branch master, Maka git akan secara otomatis membuat sebuah commit baru di dalam branch master yang isinya penggabungan perubahan2 yang sudah kita lakukan di dalam branch a
5. berbeda dengan merge, saat kita menggunakan rebase, misal kita ingin menggabungkan branch a yang berisi 2 commit, ke branch master, maka 2 commit yang ada di branch a akan langsung dipindahkan ke branch master dan terciptalah 2 buah commit baru di dalam branch master (perlu di ingat hash dari 2 commit yang dipindahkan tersebut juga ikut berubah jadi jika kita memberi tag pada suatu commit di branch a maka tag tersebut akan otomatis hilang karena hash dari commit tersebut akan berubah).
6. jadi saat kita menggunakan rebase branch a dan branch master yang awalnya bercabang, maka akan menyatu kembali (branch a akan bersatu dengan branch master)
7. salah satu keunggulan dari rebase adalah repository kita akan lebih bersih karena tidak ada lagi branch yang bercabang

--MELAKUKAN REBASE--

1. berbeda dengan merge biasa, jika kita ingin menggabungkan 2 branch menggunakan rebase, pertama-tama kita harus pindah terlebih dahulu ke branch yang ingin di gabungkan. Misal kita ingin menggabungkan branch a ke branch master, maka kita harus pindah ke branch a terlebih dahulu baru kita dapat melakukan rebase.
2. setelah kita pindah ke branch yang ingin digabungkan maka kita dapat melakukan rebase menggunakan perintah : git rebase namaBranchTujuanPenggabungan
3. misal jika sekarang kita sudah berada di branch a, maka kita dapat menggunakan perintah : "git rebase master" untuk menggabungkan branch a ke dalam branch master

--MERGE BRANCH SETELAH REBASE--

1. setelah melakukan rebase, branch yang di rebase (branch master) sekarang posisinya masih tetap ada di commit terakhir branch tersebut (commit terakhir yang kita commit di branch master)
2. Jadi posisi pointer Head saat ini berada di commit terbaru dari branch yang melakukan rebase (posisi head pointer sekarang masih berada di commit terbaru dari branch a)
3. Supaya posisinya sama dengan branch yang melakukan rebase(branch a), maka kita wajib menjalan kan peritah : git merge namaBranchYangMelakukanRebase (misal git merge branch a)
4. Perlu di ingat, sebelum melakukan merge, pertama-tama kita wajib pindah ke branch yang di rebase terlebih dahulu (pada contoh ini kita wajib pindah ke branch master terlebih dahulu)
5. setelah melakukan merge, maka sekarang posisi branch yang di rebase (master) akan berada di commit terbaru dari branch yang melakukan rebase (branch a) dan secara otomatis head pointer nya juga berada di branch yang dirabase (branch master). Sederhananya sekarang posisi branch yang di rebase dan yang melakukan rebase adalah sejajar.

--MERGE VS REBASE--

1. rebase akan terlihat sangat rapih, karena timeline pada repository seakan terlihat hanya ada satu timeline
2. namun, rebase sebenarnya secara otomatis menulis ulang semua commit yang sudah kita lakukan di branch yang melakukan rebase (branch a), dalam artian hash dari commit pasti akan berubah (semua hash dari commit di branch a akan berubah). Itu artinya semua referensi ke hash commit di branch yang melakukan rebase (branch a) akan rusak dan hilang. Misal kita sebelumnya memberi tag pada salah satu commit di branch a, maka saat kita melakukan rebase, maka tag tersebut akan otomatis hilang.
3. jika ditanya mana yang lebih baik antara merge biasa dan rebase maka jawabannya adalah tidak ada karena semua nya tergantung dengan kebutuhannya.

-- MERGE SQUASH--

1. saat kita melakukan rebase,maka semua commit dari branch yang kita commit akan dipindahkan ke branch tujuan rebase.
2. jadi jika di branch tersebut kita melakukan commit sebanyak 10 kali. saat kita melakukan rebase maka 10 commit tersebut akan dipindahkan ke branch tujuan rebase.
3. kadang ada kasus dimana kita ingin melakukan penggabungan branch namun tidak ingin memindahkan semua commit dari branch ke branch tujuan. Sederhananya kita hanya ingin mengambil semua perubahan di semua commit pada branch yang ingin kita merge lalu menjadikannya 1 buah commit saja di branch tujuan.
4. untuk kasus diatas, kita dapat menggunakan fitur merge squash.
5. merge squash hanya akan mengambil semua perubahan pada semua commit yang ada di branch yang ingin kita merge. kemudian meletakkannya di stagging index supaya nantinya semua perubahan tersebut dapat di jadikan 1 commit saja di branch yang kita inginkan.
6. misalnya kita membuat 10 commit di branch a, lalu kita melakukan merge squash branch a ke dalam branch master, maka git akan secara otomatis mengambil semua perubahan yang kita lakukan di dalam 10 commit pada branch a kemudian memasukkannya pada stagging index, dan nantinya kita tinggal melakukan commit pada semua perubahan yang ada di dalam stagging index ke dalam branch master. Dan alhasil 10 commit di branch a akan menjadi 1 commit saja di branch master
7. perlu diingat, saat kita melakukan merge squash semua commit yang ada di branch yang di merge tidak akan hilang dan branch yang sudah di merge juga masih bisa di akses. (jadi 10 commit di branch a tidak akan hilang dan branch a juga masih bisa untuk di akses)
8. kelebihan dari merge squash adalah menjadikan timeline dari repository tampak lebih rapi (tanpa percabangan) dan menjadikan branch tidak memiliki terlalu banyak commit.

--MELAKUKAN SQUASH--

1. squash dapat kita lakukan ketika merge atau ketika rebase
2. untuk melakukan squash ketika merge, kita dapat menggunakan perintah : git merge --squash namaBranchYangInginDiMerge
3. misal kita ingin melakukan merge branch a ke dalam branch master, maka kita pindah ke branch master terlebih dahulu kemudian jalankan perintah git merge --squash branch a

--GIT BRANCHING STRATEGY POPULER--

1. gitflow workflow
2. trunk based development workflow
3. forking workflow

--GITFLOW--

1. gitflow adalah stategi git branching yang paling tua dan paling banyak diadopsi
2. untuk lebih jelasnya kita dapat melihat dokumentasinya di https://nvie.com/posts/a-successful-git-branching-model/

--TRUNK BASED DEVELOPMENT--

1. Trunk based development sekarang merupakan salah satu strategi git branching yang sedang populer
2. tujuan dari workflow ini adalah sederhana dan deliver pekerjaan secepat mungkin
3. untuk lebih jelasnya dapat dilihat pada link : https://trunkbaseddevelopment.com/

--FORKING WORKFLOW--

1. forking workflow merupakan salah satu strategi git branching yang populer dalam project openSource
2. forking adalah mekanisme menduplikasi repository, biasanya hal ini dilakukan karena contributor tidak memiliki akses untuk melakukan perubahan ke repository utama
3. untuk lebih jelasnya dapat dilihat pada link : https://www.atlassian.com/git/tutorials/comparing-workflows/forking-workflow

**GIT REMOTE**

--PENGENALAN GIT REMOTE--

1. Pada pembahasan sebelumnya kita sudah membahas semua fitur yang terdapat di dalam git
2. Namun semua fitur yang sudah kita bahas tersebut adalah fitur-fitur yang ada di local komputer kita masing-masing.
3. Saat nanti kita akan bekerja dengan tim atau berkolaborasi, kita tidak hanya akan menyimpan repository git kita pada satu komputer saja.
4. Pada kasus ini, tiap anggota tim akan menyalin repository git yang sudah kita buat dan juga melakukan kontribusi (modifikasi) ke dalam git repository kita.
5. Untuk mengatasi ini, untungnya git mendukung centralized server dimana kita dapat menyimpan perubahan pada git repository yang ada di dalam local komputer ke git server (project git akan di simpan ke server cloud)
6. Seperti yang di bahas di awal bab, git merupakan distributed version control. Jadi walaupun kita menyimpan semua perubahan yang ada di git repository local komputer kita ke git server, tapi git repository yang ada di local komputer kita akan tetap ada. Jadi kita tidak wajib untuk terkoneksi dengan internet (tidak wajib mengakses git server) ketika ingin mengelola (memodifikasi) git repository
7. Kita perlu terkoneksi internet hanya pada saat mengirim perubahan yang kita lakukan di git repository local komputer kita ke git server atau mengambil perubahan yang ada di git server ke dalam git repository local komputer kita.
8. Misalnya ketika kita menambah atau merubah suatu file lalu melakukan commit ke git repository local kemudian kita ingin mengirim commit yang sudah kita lakukan di git repository local kita ke git repository yang ada di server maka kita wajib untuk terkoneksi ke internet (wajib terkoneksi dengan git repository yang ada di server)
9. Misalnya teman kita melakukan commit baru ke dalam git repository kita yang ada di local computernya dan mengirim commit tersebut ke git repository yang ada di server. Jika kita ingin untuk mengambil perubahan yang telah dilakukan teman kita (mengambil perubahan yang dikirim ke git server) tersebut maka kita waji untuk terkoneksi ke internet (wajib terkoneksi dengan git repository yang ada di server)

--MULTIPLE GIT SERVER--

1. Karena git merupakan distributed system, jadi kita tidak hanya bisa menggunakan satu git server saja.
2. jika kita mau, kita juga bisa menggunakan beberapa git server sekaligus ketika membuat git repository (walaupun ini sangat jarang dilakukan). Misal pada git repository yang kita buat kita menambahkan 2 git server yaitu github dan gitlab itu bisa dilakukan.
3. dengan memiliki lebih dari 1 git server, maka nantinya kita bisa memilih mau mengirim perubahan yang sudah kita lakukan ke git server manapun yang kita mau.

--GIT SERVER--

1. Git server merupakan server yang digunakan untuk menyimpan repository git yang sudah kita biat di local komputer (gampangnya seperti cloud storagenya git)
2. Terdapat banyak sekali penyedia git server baik itu yang gratis ataupun yang berbayar.
3. Salah satu kelebihan ketika kita menggunakan git server adalah data repository akan aman tersimpan di server. Sehingga ketika kita menghapus git repository yang di local komputer kita, repository tersebut akan tetap aman di server

--CONTOH GIT SERVER--

1. Ada banyak sekali penyedia layanan git server yang bisa kita gunakan diantaranya adalah:
2. github : github.com
3. gitlab : gitlab.com
4. bitbucket : bitbucket.org
5. dan lain sebagainya

--GITHUB--

1. pada pembahasan kali ini, kita akan menggunakan git server yang paling populer dan banyak digunakan yaitu github
2. github ini memiliki versi gratis dan versi berbayar
3. Terdapat banyak sekali project open source yang menggunakan github untuk menyimpan git repositorynya.
4. untuk menggunakan github, kita wajib melakukan registrasi akun terlebih dahulu di website resminya

--GIT SERVER REPOSITORY--

1. Setiap git server biasanya memiliki fitur untuk membuat git repository
2. Jadi sebenarnya kita tidak harus membuat git repository di local computer telebuh dahulu lalu menyimpan nya ke git server.
3. Jika ingin kita juga dapat membuat git repository di dalam git server kemudian nantinya kita dapat clone repository yang telah dibuat tersebut ke dalam local komputer kita.

--SSH--

1. SSH merupakan singkatan dari secure shell
2. SSH adalah protokol jaringan untuk komunikasi jaringan yang aman dan terenkripsi
3. Jika kita pengguna sistem operasi linux atau mac pastinya sudah sangat familiar dengan SSH ini karena di sistem operasi tersebut sudah ada SSH nya. Jadi kita tidak perlu untuk menginstallnya.
4. SSH merupakan aplikasi berbasis terminal
5. Untuk sistem operasi windows, ketika kita menginstall git, maka git juga akan secara otomatis menginstall ssh. Jadi kita dapat menggunakan ssh ini melalui git bash
6. Note : untuk windows ssh hanya bisa di akses melalui git bash saja (jadi kita tidak dapat mengakses ssh melalui cmd)

--GIT SSH--

1. Git sendiri memiliki beberapa mekanisme untuk berkomunikasi dengan git server, ada yang menggunakan http dan ada juga yang menggunakan SSH
2. note : komunikasi disini maksudnya cara yang digunakan untuk mengirim perubahan ke git server dan mengambil perubahan dari git server.
3. pada pembahasan kali ini, kita akan menggunakan SSH untuk berkomunikasi dengan git server.
4. Hal ini karena SSH merupakan protokol yang direkomendasikan ketika berkomunikasi dengan git server.
5. Salah satu keuntungan terbesar dari menggunakan SSH adalah kita tidak perlu untuk memasukkan username dan password akun git server setiap kali kita ingin mengirim perubahan ke git server atau mengambil perubahan dari git server
6. note : jika kita menggunakan protokol http untuk berkomunikasi dengan git server, maka kita wajib memasukkan username dan password akun git server setiap kali kita ingin mengirim perubahan ke git server atau mengambil perubahan dari git server

--SSH KEY--

1. Hal pertama yang perlu kita lakukan ketika ingin menggunakan ssh adalah membuat SSH key terlebih dahulu.
2. SSH key merupakan kunci yang digunakan untuk autentikasi ke SSH server. Jadi kita bisa menganggap git server (github) itu si ssh server dan local komputer kita itu si ssh client nya
3. untuk membuat SSH key, kita bisa menggunakan perintah : "ssh-keygen" di terminal
4. setelah itu, maka secara otomatis akan terbuat 2 key yang tersimpan di dalam local computer kita. 2 key tersebut adalah private key dan public key
5. kita dapat melihat 2 key tersebut didalam folder .ssh yang ada di home directory locak komputer kita
6. disana terdapat file bernama id_rsa yang merupakan private key nya dan id_rsa.pub yang merupakan public key nya

--MENAMBAHKAN SSH PUBLIC KEY KE GITHUB (GIT SERVER)--

1. setelah kita selesai emmbuat ssh key, selanjutnya kita perlu untuk meregistrasikan SSH public key yang ada di folder .ssh ke dalam github
2. Hal ini dilakukan supaya ketika kita nanti terkoneksi ke git server di github, kita tidak perlu lagi melakukan authentikasi
3. untuk meregistrasi ssh public key ke github dapat mengunjungi link : github.com/settings/keys
4. setelah mengunjungi link tersebut lalu kita tekan tombol new ssh key kemudian isi kolom title dengan text apapun yang kita inginkan dan isi kolom key dengan public key yang di dapat dari file id_rsa.pub (buka file id_rsa.pub lalu copy semua isinya kemudian paste ke dalam kolom key) setelah semua kolom diisi lalu tekan tombol add ssh key

--TEST KONEKSI SSH KE GITHUB--

1. setelah selesai menambahkan ssh public key ke github, sekarang untuk memastikan apakah kita sudah dapat terkoneksi dengan github menggunakan SSH, kita dapat menggunakan perintah : ssh -T git@github.com di terminal
2. jika diterminal muncul pesan hi UsernameGithubKita! you've successfully authenticated maka kita sudah berhasil terkonesi ke github

--REMOTE REPOSITORY--

1. Ketika kita membaut git project di local komputer kita, secara default, git tidak tahu tentang adanya remote repository
2. Maka dari itu kita perlu untuk memberi tahu git project yang ada di local tentang lokasi remote repository yang sudah kita buat di github dengan cara menambahkan remote repository ke project github kita yang ada di local komputer kita

--MENAMBAH REMOTE REPOSITORY--

1. untuk menambahkan remote repository yang sudah kita buat ke dalam git repository yang ada di local komputer kita, kita bisa menggunakan perintah : git remote add namaRemoteRepository ssh-url-dari-remote-repository
2. salah satu kebiasaan di git, saat memberi nama remote repository yaitu menggunakan nama origin. Misalnya : git remote add origin git@github:TechWithRifin/belajar-git-remote

--MELIHAT REMOTE REPOSITORY--

1. untuk melihat semua remote repository sudah kita tambahkan ke dalam git repository kita yang ada di local komputer kita, kita dapat menggunakan perintah : git remote
2. karang ada kasus dimana kita ingin melihat url dari sebuah remote repository yang sudah di tambahkan kedalam git project kita yang ada dilocal komputer. Untuk kasus seperti ini kita dapat menggunakan perintah : git remote get-url namaRemoteRepositoryYangInginDiLihatUrlNya. Misal : git remote get-url origin

--MENGHAPUS REMOTE REPOSITORY--

1. Untuk menghapus remote repository yang sudah kita tambahkan kedalam git repository yang ada di local komputer, kita dapat menggunakan perintah : git remote rm namaRemoteRepositoryYangInginDIHapus
2. note : perintah tersebut hanya akan memutus koneksi antara git project yang ada di local dan git project yang ada di git server (github) saja. Jadi git project yang ada di git server akan tetap aman.

--PUSH--

1. walaupun kita sudah menyimpan semua perubahan yang kita lakukan pada git project kedalam git repository di local komputer kita, tapi semua perubahan tersebut tidak akan secara otomatis di kirim ke git server
2. hal ini dikarenakan sejak awal git memang di desain untuk distributed version control. Itu artinya kita bisa melakukan perubahan dimanapun dan kapanpun tanpa harus terkoneksi dengan git server (jadi kita tetap bisa melakukan perubahan ke dalam git project tanpa harus terkoneksi ke internet).
3. Oleh karena itu, jika kita ingin mengirim perubahan yang sudah kita lakukan didalam git project yang ada di local komputer kita, kita perlu mengirim perubahan tersebut secara manual ke git server (proses ini perlu untuk terkoneksi dengan internet)
4. Untuk mengirim perubahan yang kita lakukan di local komputer ke git server, kita bisa menggunakan perintah yang bernama push

--PUSH BRANCH--

1. untuk mengirim semua perubahan yang sudah dilakukan di suatu branch ke remote repository (git server) dengan nama branch yang sama, kita dapat menggunakan perintah : git push namaRemoteRepository namaBranchYangAdaDiLocal. Misalnya : git push origin main (dengan perintah ini, maka semua perubahan yang kita lakukan didalam branch main yang ada di local komputer kita akan dikirim ke remote repository dengan nama branch main juga)
2. Kadang ada kasus dimana kita ingin mengirim perubahan yang sudah kita lakukan di suatu local branch ke remote repository akan tetapi dengan nama branch yang berbeda dengan nama branch yang ada dilocal komputer kita. Untuk kasus seperti ini, kita dapat menggunakan perintah : git push namaRemoteRepository namaBranchYangAdaDiLocal:namaRemoteBranchYangDiInginkan. Misal : git push origin main:develop (dengan perintah ini, maka semua perubahan yang kita lakukan di dalam branch main yang ada di local komputer kita akan dikirim ke remote repository dengan nama branch develop)

--PUSH SEMUA BRANCH--

1. kadang ada kalanya kita membuat banyak branch di local komputer kita dan ingin mengirim semua branch tersebut sekaligus ke dalam remote repository
2. untuk kasus seperti ini, kita dapat menggunakan perintah : git push namaRemoteRepository --all. Misalnya : git push origin --all
3. note : jika kita menggunakan perintah ini maka semua branch akan dikirim ke remote repository dengan nama yang sama dengan branch yang ada di local komputer kita. Jadi jika branch yang ada di local komputer bernama main, develop dan feature/a maka di remote repository juga akan bernama main, develop dan feature/a (jika kita ingin mengirim dengan nama yang berbeda maka kita harus melakukannya satu persatu)

--MENGHAPUS BRANCH YANG ADA DI REMOTE REPOSITORY--

1. Selain untuk mengirim perubahan yang kita lakukan di local komputer ke remote repository, perintah push juga dapat digunakan untuk menghapus branch yang ada di remote repository.
2. untuk menghapus branch yang ada di remote repository, kita dapat menggunakan perintah : git push --delete namaRemoteRepository namaBranchYangInginDiHapus. Misal : git push --delete origin develop (perintah ini akan menghapus branch delelop yang berada di remote repository origin)
3. Perlu untuk di ingat, perintah ini hanya akan menghapus branch yang ada di remote repositoy saja. Jadi branch yang ada di local komputer kita tidak akan secara otomatis ikut terhapus. Jika kita ingin menghapus branch yang ada di local juga maka kita perlu menghapus branch yang ada di local tersebut secara manual.

perlu untuk diingat jika kita sudah melakukan push suatu branch yang ada di local ke remote repository lalu menambahkan commit baru di branch tersebut setelah branch di push, maka commit baru tersebut tidak akan secara otomatis dikirim ke remote repository. Untuk mengirim commit baru tersebut ke remote repository, kita perlu untuk menjalankan ulang perintah : git push namaRemoteRepository namaBranchTempatKitaMenambahKanCommit

--CLONE--

1. Apa yang harus kita lakukan jika kita ingin mendownload project git yang berada di git server (github) ke local komputer baru?
2. Untuk kasus seperti ini, kita dapat menggunakan fitur clone
3. Dengan menggunakan fitur clone, kita dapat mendownload git project yang berada di remote repository ke dalam local komputer kita yang baru dan secara otomatis akan diidentifikasi sebagai git project (jadi kita tidak perlu menjalankan perintah git init lagi untuk git project yang sudah didownload tersebut).

--MELAKUKAN CLONE--

1. untuk melakukan clone project git yang ada di git server (github), kita dapat menggunakan perintah : git clone UrlDariRemoteRepositoryYangInginDiDownload. Misalnya : git clone git@github:TechWithRifin/belajar-git-remote
2. clone secara default akan membuat git project di dalam local komputer kita dengan nama folder yang sama dengan nama git repository yang ada di remote repository (belajar-git-remote)
3. jika kita ingin melakukan clone dengan nama folder yang berbeda denagn nama project remote repository yang ada di git server, kita dapat menggunakan perintah : git clone UrlDariRemoteRepositoryYangInginDiDownload namaFolderYangDiInginkan . Misal : git clone git@github:TechWithRifin/belajar-git-remote remote-user2 (secara otomatis membuat git project dilocal komputer kita dengan nama folder remote-user2)

--DEFAULT HASIL CLONE--

1. setelah kita melakukan clone, maka git project yang sudah kita download di local komputer akan secara otomatis terdapat remote repository bernama origin dengan url yang sama dengan url saat kita melakukan clone
2. setelah kita melakukan clone, maka git project yang sudah kita download di local komputer akan secara otomatis berisikan branch utama dari remote repository yang kita clone.
3. note : saat kita melakukan clone, maka branch yang didownload secara otomatis hanya branch utamanya saja. jadi branch selain branch utama tidak akan secara otomatis di download ketika kita melakukan clone.

--MELIHAT REMOTE BRANCH--

1. secara default, saat kita melakukan clone, branch yang di download hanyalah branch utamanya saja (branch main atau branch master).
2. Jadi jika kita ingin melihat semua branch yang ada di remote repository git server, kita dapat menggunakan perintah : git branch -r
3. atau jika kita ingin melihat semua branch baik di local maupun di remote repository, kita dapat menggunakan perintah : git branch -a (branch remote berwarna merah dan branch local berwarna putih (jika branch local aktif berwarna hijau))

--MEMBUAT BRANCH BARU DI LOCAL DARI REMOTE BRANCH--

1. karena secara default hanya branch utama saja yang di buat (didownload) di local komputer kita ketika melakukan clone, maka jika kita ingin membuat local branch yang berisikan data dari branch yang ada di remote repositorym kita dapat menggunakan perintah : git checkout -b namaBranchYangDiInginkanDiLocal namaRemoteRepository/namaBranchYangInginDiDownloadDatanya
2. misal kita ingin mendownload data yang ada di branch develop yang berada di remote repository origin kemudian menyimpannya di repository local dengan nama develop juga maka kita dapat menjalankan perintah : git checkout -b develop origin/develop
3. atau jika kita ingin untuk menyimpan data nya di local repository dengan nama branch yang berbeda dengan yang di remote repository misal ingin disimpan di branch yang bernama development maka kita dapat menjalankan perintah : git checkout -b development origin/develop

--FETCH--

1. fetch merupakan fitur di dalam git yang digunakan untuk mendapatkan (melihat) perubahan terbaru dari remote repository. Misal salah satu teman kita telah membuat perubahan pada project git kita di local komputernya kemudian mengirim perubahan tersebut ke remote repository. Jika kita ingin melihat apa saja yang sudah dirubah oleh teman kita tersebut maka kita dapat menggunakan fitur fetch ini.
2. fitur fetch sangat berguna ketika misal kita ingin mengetahui perubahan apa saja yang sudah terjadi pada remote repository, mungkin rekan kita sudah menambahkan perubahan ke remote repository.
3. tapi tenang saja fitur fetch ini tidak akan merubah isi dari git project kita yang ada di local komputer kita (sederhananya fetch hanya akan menampilkan informasi apa saja yang berubah di dalam terminal saja jadi isi dari git project kita yang ada di local akan tetap sama dengan saat kita belum melakukan perintah fetch)

--MELAKUKAN FETCH--

1. untuk melakukan fetch pada semua branch yang ada di remote repository, kita dapat menggunakan perintah : git fetch namaRemoteRepository. Misal : git fetch origin (akan menampilkan semua perubahan yang ada di semua branch dari remote repository origin)
2. atau jika kita ingin melakukan fetch untuk branch tertentu saja yang ada di dalam remote repository, kita dapat menggunakan perintah : git fetch namaRemoteRepository namaBranchYangInginDiFetch. Misal : git fetch origin main (ini akan menampilkan semua perubahan yang terjadi di branch main saja)
3. jika ingin melihat apa saja yang berubah di suatu branch secara detail, kita dapat membandingkan branch yang di local dengan branch yang diremote yang sudah kita fetch menggunakan fitur diff. misal kita ingin membandingkan branch main di local komputer kita dan branch main di remote repository, kita dapat melakukannya dengan perintah : git diff main..origin/main (format perintah adalah git diff namabranchYangDILocal..namaRemoteRepository/namaBranchYangDiRemoteRepository)

--PULL--

1. jika fetch berfungsi untuk mendapatkan perubahan yang ada di remote repository tanda merubah isi dari local repository yang ada di laptop kita (hanya berfungsi untuk melihat apa saja yang sudah berubah)
2. Jika kita menggunakan fitur full, git akan secara otomatis mengambil perubahan yang ada diremote repository kemudian menggabungkan perubahan tersebut ke dalam local repository yang ada di komputer kita (sederhananya fitur ini akan merubah isi dari local repository di komputer kita).
3. Jadi kita harus hati-hati jangan sampai terjadi merge-conflic ketika kita menggunakan fitur ini. Jika terjadi merge conflict, kita harus memperbaikinya secara manual seperti yang sudah kita bahas pada pembahasan sebelumnya. Misal jika kita melakukan perubahan di branch main yang ada di local repository kita kemudian melakukan pull branch main yang ada di remote repository, maka itu akan menyebabkan merge-conflict
4. Saat kita melakukan pull, maka git akan secara otomatis melakukan fetch terlebih dahulu kemudian melakukan merge perubahan yang ada diremote repository ke local repository yang ada di komputer kita.

--MELAKUKAN PULL--

1. sebelum kita melakukan pull, pertama-tama kita harus pindah ke local branch yang ingin kita terapkan perubahannya saat melakukan pull
2. setelah pindah branch, kita dapat melakukan pull dengan perintah : git pull namaRemoteRepository namaBranchDiRemoteRepositoryYangInginDiPull .
3. Misal lokasi kita sekarang berada di local branch yang bernama main kemudian kita menjalankan perintah : git pull origin main, maka semua perubahan di branch main pada remote repository origin akan di merge ke dalam branch main yang ada di local komputer kita.

--TAG--

1. saat kita mengirim perubahan di local komputer ke remote repository menggunakan push, semua tag yang sudah kita buat di local komputer kita tidak akan secara otomatis ikut dikirim ke remote repository.
2. Jadi jika kita ingin mengirim tag yang sudah kita buat di local komputer kita ke dalam remote repository, maka kita harus melakukan push tag tersebut secara manual.

--MENGIRIM TAG YANG ADA DI LOCAL KOMPUTER KE REMOTE REPOSITORY--

1. untuk mengirim tag yang sudah kita buat di local komputer ke dalam remote repository, kita dapat menggunakan perintah git push namaRemoteRepository namaTagYangInginDiKirim . Misal : git push origin 1.0.0 (perintah ini akan mengirim tag yang bernama 1.0.0 ke dalam remote repository origin)
2. atau jika kita ingin mengirim semua tag yang sudah kita buat di local komputer kita ke dalam remote repository, kita dapat menggunakan perintah : git push namaRemoteRepository --tags

--MENGAMBIL TAG YANG ADA DI REMOTE REPOSITORY--

1. jika kita ingin mengambil tag yang ada diremote repository kemudian memasukkan tag tersebut ke local repository komputer kita, kita dapat menggunakan perintah : git fetch namaRemoteRepository namaTagYangInginDiAmbil . Misal : git fetch origin 1.0.0 (maka git akan mengambil tag yang bernama 1.0.0 dari remote repository origin kemudian memasukkannya ke local repository komputer kita).
2. atau jika kita ingin mengambil semua tag yang ada di remote repository kemudian memasukkannya ke local repository komputer kita, kita dapat menggunakan perintah : git fetch namaRemoteRepository . Misal : git fetch origin (maka git akan mengambil semua tag yang ada di remote repository origin kemudian memasukkannya ke local repository komputer kita).

--MENGHAPUS TAG YANG ADA DI REMOTE REPOSITORY--

1. Saat kita menghapus tag yang ada di local repository, maka data tag tersebut yang ada di remote repository tidak akan ikut terhapus begitu juga dengan sebaliknya. Misal kita menghapus tag 1.0.0 yang ada di di local repository komputer kita, maka tag 1.0.0 yang ada di remote repository akan tetap ada (tidak ikut terhapus).Sederhananya yang terhapus hanya tag yang ada dilocal repository branch kita saja dan yang di remote repository akan tetap ada.
2. Jika kita ingin menghapus juga tag tersebut dari remote repository maka kita hapus melakukannya secara manual dengan perintah : git push --delete namaRemoteRepository namaTagYangInginDiHapus . Misal : git push --delete origin 1.0.0 (perintah ini akan menghapus tag 1.0.0 yang ada di remote repository origin).

--PULL REQUEST--

1. saat kita bekerja dengan tim, saat akan melakukan perubahan biasanya kita akan menyimpan perubahan tersebut di branch yang berbeda dengan branch utamanya.
2. kemudian setelah selesai melakukan perubahan, kita akan melakukan yang namanya merge ke branch utamanya
3. Terdapat beberapa fitur yang dimiliki git repository yan mendukung proses diatas. fitur tersebut bernama pull request (di github) atau merge request (di gitlab)
4. fitur ini sangat cocok digunakan untuk melakukan reviews kode di dalam remote repository, tanpa harus melakukan harus melakukan pull ke local terlebuh dahulu lalu menggunakan fitur git diff untuk melakukan reviews
5. pull request akan memudahkan kita untuk melakukan reviews (easy to read)

--MEMBUAT PULL REQUEST--

1. buka repository kita yang ada di git server (github)
2. pilih menu pull request
3. tekan tombol new pull request
4. pada kolom base isi dengan branch lokasi dimana kita akan menerapkan merge branch dan pada kolom compare isi dengan branch yang ingin kita merge. misal kita akan melakukan merge branch feature/a ke dalam branch main, maka kita harus mengisi kolom base dengan main dan kolom compare dengan feature/a
5. tekan tombol create pull request
6. lalu isi kolom atas dengan nama pull request (bebas isi apa saja)
7. lalu isi kolom ke 2 dengan keterangan atau catatan untuk yang melakukan review (kolom ini boleh tidak di isi (opsional))
8. tekan tombol create pull request
9. untuk melihat apa saja yang sudah berubah di branch yang ingin di merge, kita bisa pergi ke menu files changed
10. untuk melakukan merge branch, kita dapat pergi ke menu conversation kemudian tekan tombol merge pull request lalu tekan tombol confirm merge
11. untuk mendownload hasil merge yang sudah dilakukan di remote repository, kita dapat menggunakan perintah : git pull namaRemoteRepository namaRemoteBranch . misal kita ingin mendownload hasil merge dari branch main yang ada di remote repository origin, maka kita dapat menggunakan perintah : git pull origin main (note : sebelum menjalankan perintah tersebut, kita harus pindah dulu ke branch main yang ada di local repository komputer kita)

--MERGE CONFLICT PADA FITUR PULL REQUEST--

1. ketika kita melakukan pull request, kadang akan terjadi yang namanya merge conflict yang akan menyebabkan kita tidak bisa melakukan proses merge di remote repository.
2. jika kita menghadapi kasus demikian, kita perlu untuk melakukan merge terlebih dahulu branch remote repository yang akan kita gunakan untuk menerapkan merge branch (base) dengan branch local repository komputer kita yang akan kita merge (compare). Kemudian kita dapat memperbaiki conflict secara manual di local repository komputer kita setelah itu melakukan commit dan kita push lagi perbaikan tersebut ke remote repository.
3. misal kita ingin melakukan merge branch a ke dalam branch main menggunakan fitur pull request, akan tetapi terjadi conflict antara branch a dan branch main. Untuk mengatasi mesalah tersebut kita dapat melakukan merge branch a yang ada di local dengan branch main yang ada di remote repository dengan perintah : git merge origin/main (sebelum melakukan merge kita harus melakukan fetch branch main terlebih dahulu dan lokasi kita saat ini harus berada di branch a). Setelah melakukan merge maka kita tinggal memperbaiki file yang conflict nya dan setelah diperbaiki lalu melakukan commit dan terakhir melakukan push branch a yang ada di local komputer ke branch a yang ada di remote repository. Dengan ini merge conflict dapat teratasi.

--SUBMODULE--

1. saat kita membuat sebuah project (aplikasi), kadang kita ingin membuat suatu library yang berisikan kode program yang nantinya library tersebut ingin kita gunakan pada beberapa project (aplikasi) di dalam repository yang berbeda-beda.
2. untuk kasus seperti ini, kita dapat menggunakan fitur git yang bernama git submodule
3. git submodule memungkinkan kita untuk menambahkan git repository lain didalam git repository yang sudah kita buat. Sederhananya kita menambahkan git repository lain ke dalam git repository kita saat ini.
4. dengan menggunakan submodule, kita bisa melakukan management git repository lain secara terpisah. Sederhananya kita dapat melakukan modifikasi library yang sudah kita buat di dalam git repositorynya sendiri (bukan di dalam git repository dari project aplikasi kita)
5. keuntungan dari menggunakan submodule adalah jika kita ingin memodifikasi isi dari library yang sudah di buat, kita tidak perlu melakukan perubahan di setiap project aplikasi yang menggunakan library tersebut. Kita cukup melakukan modifikasi di dalam git repository dari librarynya saja dan secara otomatis semua library di dalam project aplikasi akan ikut berubah juga.
6. Misal kita membuat git repository baru yang berisikan library a kemudian kita menambahkan git repository library a tersebut ke git repository project b dan git repository project c. Jika kita ingin memodifikasi isi dari library a, kita hanya perlu memodifikasi git repository dari library a nya saja, maka secara otomatis git repository library a yang ada di dalam git repository project b dan git repository project c akan ikut berubah juga.

--MENAMBAHKAN SUBMODULE--

1. untuk menambah submodule ke dalam git repository project kita, kita dapat menggunakan perintah : git submodule add urlGitRepositoryDariLibraryYangInginKitaTambahkanKeSubmodule namaFolderTempatUntukMenyimpanSubmoduleTersebut . Misal : git submodule git@github:TechWithRifin/contoh-library.git script (perintah tersebut akan menyimpan submodule (library) yang bernama contoh-library ke dalam folder script didalam root repository project kita).
2. saat kita menambahkan submodule ke dalam git repository project, maka secara otomatis semua git repository dari submodule(library) tersebut akan ikut di clone (download) ke dalam folder yang sudah kita tentukan. Sederhanya saat kita menambahkan submodule, maka submodule tersebut akan di download sebagai git project. Jadi commit2 yang sudah kita lakukan di dalam git repository submodule akan ikut terdownload juga.
3. Sekarang pertanyaannya, bagaimana git repository project kita dapat mendeteksi suatu folder itu adalah sebuah submodule ?
4. Git akan mendeteksinya dari file yang bernama .gitmodules yang akan secara otomatis terbuat saat kita menambahkan submodules ke dalam git repository project kita.
5. note : kita dapat menambahkan submodule sebanyak apapun yang kita mau tanpa ada batasan.

--SUBMODULE REPOSITORY--

1. saat kita masuk ke dalam folder tempat kita menyimpan submodule, sebenarnya kita sedang mengakses git repository dari submodule tersebut. Sederhananya saat kita menjalankan git log di dalam folder submodule, maka commit2 yang ditampilkan bukanlah commit2 yang sudah kita lakukan di dalam git repository project kita melainkan commit2 yang berasal dari git repository submodule yang sudah kita download.
2. Jadi sebenarnya kita dapat melakukan modifikasi data dari git repository submodule didalam folder tempat kita menyimpan submodule. Seperti melakukan commit, mengelola branch, dll
3. akan tetapi cara ini sangat tidak disarankan, Jika kita memang ingin melakukan modifikasi isi dari submodule, maka sangat di sarankan untuk melakukakan modifikasi di git repository sumber aslinya (bukan didalam submodule nya). Anggap saja submodule ini hanya digunakan untuk menduplikasi perubahan yang terjadi di git repository sumber aslinya.

--UPDATE SUBMODULE--

1. jika terjadi perubahan di dalam git repository sumber asli dari submodule, kita bisa mendapatkan (mendownload) perubahannya dengan menggunakan perintah : git submodule update --remote namaFolderTempatKitaMenyimpanSubModule . misal : git submodule update --remote script
2. atau jika kita ingin mendapatkan perubahan dari semua submodule yang sudah kita tambahkan, kita dapat menggunakan perintah : git submodule update --remote
3. atau jika kita ingin mendapatkan perubahan dari submodule secara manual, kita bisa masuk ke dalam folder submodule yang ingin kita dapatkan perubahannya lalu melakukan pull ke git remote repository submodule tersebut (cara ini tidak disarankan).

--CLONE SUBMODULE--

1. saat kita melakukan clone sebuah git repository yang didalamnya terdapat submodule, maka isi dari submodule tidak akan secara otomatis ter clone juga. Sederhananya submodule-submodule tersebut masih sebuah folder kosong tanpa isi.
2. Jadi setelah kita melakukan clone sebuah git repository yang didalamnya terdapat submodule, kita perlu mengaktifkan submodule-submodule tersebut dengan perintah : git submodule init
3. perintah ini akan membaca file .gitmodule lalu mengaktifkan submodule sesuai isi dari file tersebut.
4. kemudian untuk mendownload isi dari submodule dari git repository sumbernya, kita bisa gunakan perintah : git submodule update --remote

--MENGUBAH BRANCH SUBMODULE--

1. saat kita melakukan tambah submodule, maka secara default submodule tersebut akan menggunakan branch utamanya
2. jadi jika kita ingin mengubah branch submodule tersebut (melakukan switch branch), kita dapat menggunakan perintah : git submodule set-branch --branch namaBranchYangDiInginkan namaFolderTempatMenyimpanSubmoduleYangInginKitaUbahBranchnya . misal : git submodule set-branch --branch release script (perintah ini akan merubah branch dari submodule yang disimpan didalam folder script ke branch release).
3. note : nama branch harus ada di dalam git repository sumber asli dari submodulenya
4. setelah menjalankan perintah tersebut kemudian jalankan perintah git submodule update --remote untuk mendowload isi data branch tersebut (isi data branch release) dari git repository sumber asli submodulenya.

--MENGHAPUS SUBMODULE--

1. untuk menghapus submodule, kita dapat menghapus folder submodulenya kemudian hapus submodulenya yang ada didalam file .gitmodules

--FORK--

1. salah satu git workflow yang sebelumnya kita bahas di git branching adalah forking workflow
2. forking workflow biasanya digunakan ketika kita ingin berkontribusi ke project opensource, dimana kita tidak memiliki akses langsung ke dalam git repository aslinya, sehingga kita melakukan forking (duplikasi) git repository asli ke dalam git server kita (di duplikasi ke akun github). Sederhananya menyalin project github yang kita inginkan kemudian menempatkannya ke dalam git server (github) kita
3. Misalnya kita melakukan forking sebuah git repository dari akun techwithrifin ke akun github kita.

--PULL REQUEST KE REPOSITORY ASLINYA--

1. setelah melakukan forking, maka setiap modifikasi yang kita lakukan akan tersimpan di git repository yang sudah kita salin ke dalam github profile kita.
2. dan setelah kita selesai melakukan modifikasi, dan kita ingin melakukan penggabungan (merge) modifikasi yang sudah kita lakukan tersebut ke dalam repository aslinya maka kita dapat menggunakan pull request.
3. konsep pull requestnya sama seperti yang sudah di jelaskan sebelumnya hanya saja pada base repository kita isi dengan namaAkunGithubRepositoryAslinya kemudian pada base kita isi dengan namaBranchTujuanMerge selanjutnya pada head repository kita isi dengan namaAkunGithubKita lalu compare kita isi dengan namaBranchYangInginKitaMerge
