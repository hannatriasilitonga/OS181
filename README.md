# ZCZC Sistem Operasi 2018 Week01

1. a01-READ-ME

-  $0 : nama file yang di-run

-  $RESULT : hasil grep berdasarkan prefix yang sudah di define di awal pada setiap filename (disimpan di $0)

-  jika $RESULT tidak null, maka print "[a01-READ-ME]: # R: Just run "bash a01-README" (berdasarkan fungsi substring yang digunakan dari $0 dan $RESULT)

-  grep : mencari string atau kata pada setiap baris data

-  echo : hanya menampilkan plain text

-  printf : bisa menggunakan substring dll

-  cat - << NNNN "........................." NNNN : untuk view text (diawali NNNN dan diakhiri NNNN untuk spesifik text)

-  ls -AF : melihat semua isi directory

-  head : menampilkan 10 line pertama dalam sebuah file


2. a02-sort-n-prepare

Mempersiapkan file file yang dibutuhkan untuk demo demo selanjutnya

-  chmod : memberikan akses kepada user berhak melakukan apa saja sesuai dengan angka yang di define

-  cat > "nama file" << "masukkan isi file yang diinginkan" : create file baru

-  rm -rf : delete direktori beserta dengan isi directory-nya

-  mkdir -p : membuat direktori parent


3. a03-command-lines-demo

-  ls : menampilkan file dan direktori tanpa details (ex. file types, modified date time, dll)

-  ls -a : menampilkan semua file dan direktori termasuk yang 'hidden'

-  ls -aF : menampilkan semua file dan direktori termasuk yang 'hidden'

-  ls -al | head -8 ; echo "(...)"; ls -al | tail -8 : menampilkan 8 line teratas dan 8 line terbawah dengan inputan "hasil dari ls-al"

-  ls -a .TESTFROM ; echo ":::::::::" ; ls -aF .TESTFROM : menampilkan isi file bahkan yang 'hidden' juga

-  cat : view only isi file

-  ./[nama folder/nama file] : direktori atau filename hidden

-  cd .. : keluar 1 kali dari current direktori

-  cd [nama folder] : masuk ke dalam folder yang diinginkan

-  diff : mencari perbedaan line antara file1 dan file2

-  sort [filename] : sorting line per line sesuai urutan abjad

-  wc : print jumlah new line, jumlah kata, jumlah byte pada sebuah file

-  wc -l : print jumlah new line saja pada sebuah file

-  wc -c : print jumlah byte pada sebuah file

-  date : menampilkan date time saat ini

-  date +%y : 2 digit terakhir dari tahun hari ini

-  date +%Y : curren date (4 digit)

-  date +%d\ %b\ %Y\ at\ %H:%M:%S : 18 Feb 2018 at 13:39:51 (menampilkan date time sesuai dengan format yang diinginkan)

-  top -b -n 1 | head -15 : menampilkan list proses yang sedang berjalan dalam sistem (proses yang ditampilkan tidak realtime) 
dan dijadikan inputan untuk command head, yaitu hanya menampilkan 15 line teratas saja

-  top -b -n 1 | head -9; echo "... etc ..."; top -b -n 1 | tail -7 :
	menampilkan list proses yang sedang berjalan dalam sistem (proses yang ditampilkan tidak realtime) 
    dan dijadikan inputan untuk command head, yaitu hanya menampilkan 9 line teratas saja dan 7 line terbawah

-  find . -type d -print : cari dan tampilkan folder di current direktori dengan type . (hidden) (-d : menunjukkan direktori)

-  echo $MYVAR : menampilkan isi variable MYVAR (tanpa ada '' atau "" diantarany)

-  PATH=[%s]\nHOME=[%s]\nSHELL=[%s]\n" $PATH $HOME $SHELL  : menampilkan path, home dan shell

-  $$ : view pid (id process)

-  $1, $2, $3, $3, $4, places of argument

-  function dummy { printf "BASH PID = %s\n" $$ ; return 99 ; } ; FOR CREATE FUNCTION untuk print pid proses

-  dummy ; printf "Return value = %s\n" $? 
    CALL FUNCTION 'dummy' and print return value, 99

-  function doawk { awk -f .TESTFROM/file.awk /etc/passwd ; } ;
	CREATE FUNCTION untuk mengganti isi file .TESTFROM/file.awk dengan isi dari /etc/passwd

-  doawk | head -6 ; echo "(...)" ; doawk | tail -6 ;
	CALL FUNCTION 'doawk' dan menampilkan isi 6 line teratas dan 6 line terbawah

-  sleep : delay for spesific time

-  /bin/bash --version : gnu bash version yang digunakan


4. a04-loop

looping nilai yang dimasukkan pada argumen saat menjalankan script

-  $* dan $@ berguna untuk menyimpan argumen yang akan di passing ke script


5. a05-tester

program yang digunakan untuk melakukan pengecekan terhadap 3 masukan, yaitu : .TESTFROM,  .thisfile.tx, dan  Nothing
pengecekan apakah tipe masukan tersebut, apakah file/direktori/tidak keduanya

-  -f untuk pengecekan file

-  -d untuk pengecekan direktori


6. a06-does-it-exist

Program untuk melakukan pengecekan apakah file ini ada atau tidak 

-  -f untuk pengecekan file pada current direktori


7. a07-finding-EXIST

Program yang digunakan untuk mencari file yang di dalamnya terdapat kata 'EXIST'

-  file in ls a[01]* : list semua nama file dan simpan ke variable 'file'

-  grep -q EXIST $file : validasi file 


8. a08-append-a-file

Program ini digunakan untuk append value dalam file yang diinginkan, jika file belum ada akan di-create otomatis

-  Word(JJ=$((JJ + 1))) : 
	- JJ=$((JJ + 1)) : counter++ untuk looping isi file
	- Word : ambil semua kata yang ada

-  for ii in f1 f2 : f1 dan f2 merupakan value yang dipassing sebagai parameter looping

-  "[new value]" >> [nama file yang di append] : append nilai dalam sebuah file

-  /bin/rm -f [nama file]: remove file dari folder bin

9. bash a09-add-numbers

Program ini memiliki paramater 'nama file' yang ingin diproses. Digunakan untuk memperkenalkan awk sebagai fungsi yang menyerupai cut.
Script ini membentuk 1 file baru dengan .thisfile.tx sebagai dasar pembuatan file, dan memecah masing masing line dengan spasi.
Pada file baru Array ke-0 pada masing masing line '01' diganti '001', '02' diganti '002', dst

-  printf "%3.3d %s\n", lll++, $0 : array ke 0(dipisah oleh spasi, awk yang mengerjakan) masing masing line diganti menjadi 3 karakter '001 - 00n'

-  [param_fileName] > [param_fileName].txt : terbentuk file baru, dengan nilai yang sudah di modifikasi


10. bash a10-mysha1

Program ini digunakan untuk terima inputan dari depan beserta pengecekan apakah inputan tersebut adalah 'number', pengecekan panjang (harus 10),
menampilkan checksum sha1 dari inputan, trim hasil checksum sepanjang 10 karakter, serta hashing(hexadecimal) dari hasil trim.

-   ${#variable} : panjang value dari variable

-  =~ : equals

-  cut -c1-10 : trim string dari char 1 - 10

-  read ID : terima inputan dari user

-  sha1sum : Print atau cek SHA1 (160-bit) checksums.

-  0$variable : Hashing dalam bentuk hexadecimal

11. a11-banding

Program ini membandingkan isi .TESTFROM/ dan .TESTBACKUP

-  sync : mengubah blok menjadi disk, dan update super blok

12. a12-fixfs (tidak dapat dijalankan, error 'gawk')

Sebuah program recursive untuk memperbaiki nama file yang ada pada current directory maupun derived directory-nya menjadi 

- tambahkan escape \

- Ganti karakter spesial dan spasi dengan -

- ganti multiple - dengan single -

- tidak ada - sebelum .
