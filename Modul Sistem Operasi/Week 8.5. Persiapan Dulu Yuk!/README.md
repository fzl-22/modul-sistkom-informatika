# Persiapan Dulu Yuk!

## Daftar Isi
- [1. Mengenal Sistem Operasi](#1-mengenal-sistem-operasi)
  - [1.1 Sistem Operasi Berbasis Linux](#11-sistem-operasi-berbasis-linux)
  - [1.2 Ubuntu Server](#12-ubuntu-server)
  - [1.3 Opsi-Opsi untuk Menginstall Sistem Operasi](#13-opsi-opsi-untuk-menginstall-sistem-operasi)
- [2. Virtualisasi](#2-virtualisasi)
  - [2.1 Oracle VirtualBox](#21-oracle-virtualbox)
  - [2.2 Cara Menginstall Oracle VirtualBox](#22-cara-menginstall-oracle-virtualbox)
- [3. Virtual Machine dan Guest OS](#3-virtual-machine-dan-guest-os)
  - [3.1 Membuat Virtual Machine Baru](#31-membuat-virtual-machine-baru)
  - [3.2 Menginstall Ubuntu Server di Virtual Machine](#32-menginstall-ubuntu-server-di-virtual-machine)
- [Penutup](#penutup)

## 1. Mengenal Sistem Operasi

Sistem operasi adalah program atau perangkat lunak yang mengatur jalannya aplikasi dan juga bertindak sebagai antarmuka (penghubung) antara aplikasi dan perangkat keras.

![](./assets/a.%20Arsitektur%20komputer.png)

Pada saat ini, beberapa sistem operasi yang populer digunakan adalah sebagai berikut:

1. Windows
2. Mac OS X
3. Linux (sistem operasi berbasis Linux; seperti Ubuntu, Debian, Fedora, OpenSUSE, Arch Linux, dll)
4. BSD (Free BSD, OpenBSD, dll)
5. Fuchsia OS (sebagai info sadja, OS keren yang masih dalam tahap pengembangan oleh Google)

Namun, sebenarnya ada banyak sekali sistem operasi di dunia ini. Hanya saja, sebagian kurang populer atau setidaknya populer hanya untuk kepentingan tertentu saja. Sebagai contoh, sistem operasi berbasis Linux kurang populer di sisi desktop tetapi hampir semua server di dunia menggunakan Linux. Bahkan, di umur berapakah kamu tahu bahwa Android adalah fork dari Linux?

### 1.1 Sistem Operasi Berbasis Linux

Linux adalah sistem operasi bebas dan sumber terbuka (Free and Open Source Software) serupa-UNIX (UNIX-like operating system). Sehingga, sistem operasi bebas digunakan (dan tentu saja gratis) serta source codenya dapat dilihat dan kita dapat ikut berkontribusi dalam pengembangannya. Jika penasaran, source code kernel Linux dapat diakses di [www.linux.org](https://www.linux.org/).

Walaupun terkadang sebagian orang menyebut Linux sebagai sistem operasi, Linux lebih tepatnya adalah sebuah kernel. Kernel sendiri adalah bagian inti dari sebuah sistem operasi yang bertanggung jawab dalam pengelolaan memori, proses, device driver, dan system call serta keamanan. Gambar di bawah menggambarkan arsitektur dari sistem operasi berbasis Linux (kadang-kadang juga disebut GNU/Linux karena sistem operasinya merupakan gabungan dari kernel Linux dan utilitas GNU):

Bebas mau nyebutnya yg mana wkwk

![](./assets/b.%20Arsitektur%20Linux.png)

Karena Linux hanyalah sebuah kernel, berikut adalah sistem-sistem operasi berbasis Linux yang sering digunakan di dunia:

1. Debian (https://www.debian.org/)
2. Ubuntu (https://ubuntu.com/)
3. Red Hat Enterprise Linux (https://www.redhat.com/en)
4. Fedora (https://fedoraproject.org/)
5. Arch Linux (https://archlinux.org/)
6. EndeavourOS (https://endeavouros.com/)
7. Nitrux (https://nxos.org/)
8. BlankOn (https://blankon.id/), ini OS karya anak bangsa :)

### 1.2 Ubuntu Server

Untuk keperluan praktikum mata kuliah Pemrograman Sistem Komputer - Informatika, kita akan menggunakan sistem operasi Ubuntu, tepatnya adalah Ubuntu Server.

Sebelum menggunakannya, download terlebih dahulu file ISO-nya melalui link di bawah ini:

Link Download: https://ubuntu.com/download/server.

Setelah masuk, tampilan websitenya adalah seperti gambar di bawah ini. Kemudian, klik tulisan "Download Ubuntu Server 22.04.2 LTS". 

![](./assets/Download%20ISO%20File%20Ubuntu%20Server/1.%20Download%20Ubuntu%20ISO%20Files.png)

Sekarang, pertanyaan baru muncul. Kenapa tidak menggunakan Ubuntu Desktop saja? Jawabannya adalah karena Ubuntu Server jauh lebih ringan karena tampilannya secara default berbasis CLI (Command Line Interface) sehingga minimum hardware requirement dapat ditekan.

Sebenarnya, sistem operasi berbasis Linux relatif lebih ringan daripada Windows. Tetapi karena sistem operasi akan dijalankan menggunakan virtualisasi, maka konsekuensinya adalah beban resourcenya menjadi semakin besar. Tetapi, keuntungannya adalah instalasi OS tidak akan mengganggu file-file yang sudah ada di host OS. Tetapi, berikut asisten praktikum sediakan opsi-opsi instalasi OS.

### 1.3 Opsi-Opsi untuk Menginstall Sistem Operasi

1. **Fresh Install** (mengganti total sistem operasi, hanya jika benar-benar ingin total-experience memanfaatkan Linux dan tidak membutuhkan software khusus Windows seperti MS Word, Adobe Photoshop, dll).
2. **Dual Boot** (terdapat lebih dari 1 OS dalam 1 komputer, tetapi hanya berjalan salah satunya saja. Keuntungannya adalah dapat merasakan dan langsung mempelajari OS-nya secara full-experience. Tetapi, tidak direkomendasikan untuk yg memiliki storage kecil dan harus hati-hati saat menginstall karena ada potensi kehilangan data jika ada kesalahan konfigurasi).
3. **Virtualisasi** (menjalankan OS tamu (guest OS) di atas OS utama (host OS). Metode paling aman, tetapi juga paling berat karena ada lebih dari 1 OS yang berjalan bersamaan. Metode ini akan digunakan dalam praktikum).
4. **Install WSL (Windows Subsystem for Linux)**. Teknologi cukup baru dari Microsoft yang mengintegrasikan lingkungan Windows dengan Linux, bisa baca lebih lanjut di sini: https://learn.microsoft.com/en-us/windows/wsl/install

## 2. Virtualisasi

Virtualisasi merupakan teknologi yang memungkinkan satu buah komputer untuk dapat menjalankan beberapa OS secara bersamaan (simultan) dengan cara berbagi sumber daya hardware secara terisolasi. Dalam teknologi ini, ada host OS yang dijalankan oleh mesin fisik dari komputer dan guest OS yang merupakan OS yang berjalan di dalam virtual machine melalui bantuan dari Virtual Machine Monitor (biasanya disebut dengan Hypervisor). Gambar di bawah merupakan gambaran sederhana dari teknologi virtualisasi.

![](./assets/c.%20Arsitektur%20virtual%20machine.png)

Dengan menggunakan virtualisasi, kita bisa menjalankan Ubuntu Server di atas sistem operasi Windows. Tidak hanya satu, bahkan bisa beberapa Ubuntu Server sekaligus. Sebaliknya, kita juga bisa menjalankan Windows di atas Ubuntu Desktop. Atau bisa juga Ubuntu yang menjalankan Windows, Arch Linux, Red Hat, dan Debian sekaligus.

Walaupun berbagi sumber daya hardware, kita tidak perlu takut kehilangan data karena Hypervisor memiliki mekanismenya sendiri untuk mengisolasi setiap VM yang kita miliki. Oleh sebab itu, metode virtualisasi disebut sebagai metode paling aman untuk menjalankan OS lain di luar OS yang biasa kita gunakan.

### 2.1 Oracle VirtualBox

Untuk melakukan virtualisasi, kita memerlukan sebuah hypervisor untuk membuat dan menjalankan VM. Ada beberapa pilihan hypervisor yang umum digunakan, yaitu Oracle VirtualBox dan VMWare Workstation. Namun, untuk keperluan praktikum, kita akan menggunakan VirtualBox.

### 2.2 Cara Menginstall Oracle VirtualBox

Sebagai catatan, cara menginstall VirtualBox dalam modul ini menggunakan Windows. Silakan menyesuaikan dengan OS masing-masing yaa.

1. Download installer VirtualBox melalui link berikut: [Download Installer VirtualBox](https://www.oracle.com/id/virtualization/technologies/vm/downloads/virtualbox-downloads.html). Jika sudah masuk, pilih installer sesuai OS yang digunakan (dalam hal ini adalah "Windows Installer").

    ![](./assets/Instalasi%20Oracle%20VirtualBox/2.%20Download%20Oracle%20VirtualBox%20installer.png)

2. Jika sudah selesai download, klik file installer di folder Downloads. Maka, akan muncul tampilan seperti di bawah ini. Klik "Next".

    ![](./assets/Instalasi%20Oracle%20VirtualBox/3.%20Klik%20file%20.exe%2C%20installer%20akan%20dieksekusi.png)

3. Berikutnya akan muncul pilihan set up instalasi VirtualBox. Biarkan default, kemudian klik "Next".

    ![](./assets/Instalasi%20Oracle%20VirtualBox/4.%20Biarkan%20konfigurasi%20fitur%20dalam%20konfigurasi%20default.png)

4. Selanjutnya, akan muncul peringatan bahwa akan ada pemutusan jaringan secara sementara karena di-reset. Setujui dengan klik "Yes".

    ![](./assets/Instalasi%20Oracle%20VirtualBox/5.%20Ada%20peringatan%20mengenai%20pemutusan%20jaringan%20untuk%20sementara%2C%20klik%20yes.png)

5. Jika ditemukan warning seperti gambar di bawah ini, biarkan saja. Klik "Yes".

    ![](./assets/Instalasi%20Oracle%20VirtualBox/6.%20Hiraukan%20warning%20dependency.png)

6. Selanjutnya, installer VirtualBox sudah siap untuk memulai instalasi. Klik "Install". Tunggu hingga prosesnya selesai.

    ![](./assets/Instalasi%20Oracle%20VirtualBox/7.%20Mulai%20instalasi%20Oracle%20VirtualBox.png)

7. Jika instalasi sudah selesai, centang "Start Oracle VM VirtualBox 7.0.4 after installation". Kemudian, klik "Finish".

    ![](./assets/Instalasi%20Oracle%20VirtualBox/8.%20Jika%20instalasi%20sudah%20selesai%2C%20klik%20Finish.png)

8. Setelah itu, VirtualBox akan otomatis terbuka dengan tampilan seperti gambar di bawah ini. Selamat, kamu sudah berhasil menginstall Oracle VirtualBox!!

    ![](./assets/Instalasi%20Oracle%20VirtualBox/9.%20Aplikasi%20Oracle%20VirtualBox%20otomatis%20terbuka.png)

## 3. Virtual Machine dan Guest OS

Setelah semua yang kita butuhkan (file ISO Ubuntu Server dan VirtualBox) sudah ada, saatnya kita membuat Virtual Machine baru dan menginstall Guest OS (yaitu Ubuntu Server) di dalamnya.

### 3.1 Membuat Virtual Machine Baru

Berikut adalah langkah-langkah untuk membuat Virtual Machine baru.

1. Buka aplikasi VirtualBox. Klik "New" untuk membuat VM baru.

    ![](./assets/Membuat%20VM%20Baru/10.%20Buka%20aplikasi%20Oracle%20VirtualBox.png)

2. Akan muncul tampilan di bawah ini. Isikan nama VM yang dibuat, bisa diisi dengan nama Ubuntu Server saja. Biarkan folder VM default. Kemudian, masukkan file ISO dari Ubuntu Server yang sudah di-download sebelumnya. Centang "Skip Unattended Installation". Klik "Next".

    ![](./assets/Membuat%20VM%20Baru/11.%20Pop%20up%20new%2C%20isikan%20identitas%20Guess%20OS.png)

3. Atur konfigurasi hardware dari VM. Gunakan minimum requirement dari Ubuntu Server, yaitu

    | Hardware | Minimum Requirement |
    | -- | -- |
    | Memory | 1 GB atau 1024 MB (bisa dinaikkan kalau mau) |
    |Prosesor | 1 CPU (bisa dinaikkan kalau mau) |

    Biarkan "Enable EFI" tidak tercentang. Kemudian, klik "Next".

    ![](./assets/Membuat%20VM%20Baru/12.%20Atur%20konfigurasi%20hardware%20Guess%20OS.png)

4. Virtual Hard Disk adalah storage yang digunakan oleh VM. Pilih "Create a Virtual Hard Disk now". Atur ukuran storage-nya sebesar 16 GB. Boleh ditambah jika storage mencukupi. Jika ingin dikurangi, jangan terlalu kecil untuk mencegah storage penuh saat praktikum. Klik "Next".

    ![](./assets/Membuat%20VM%20Baru/13.%20Atur%20ukuran%20Virtual%20Hard%20Disk%20yang%20dibuat.png)

5. Setelah itu, akan muncul rangkuman konfigurasi. Jika dirasa sudah benar, klik "Finish'. Aplikasi akan kembali ke menu utama. Tetapi, konfigurasi masih belum selesai :)

    ![](./assets/Membuat%20VM%20Baru/14.%20Baca%20lagi%20rangkuman%20konfigurasi%2C%20kemudian%20Finish.png)

6. Klik "Settings" untuk melakukan pengaturan tambahan.

    ![](./assets/Membuat%20VM%20Baru/15.%20Klik%20menu%20Setting.png)

7. Akan muncul tampilan Settings berikut. Masuk ke pengaturan Adapter di Network $\rightarrow$ Adapter 1. Ganti Network Adapter menjadi "Bridged Adapter" agar bisa terkoneksi ke internet. Kemudian, klik "OK" maka aplikasi akan kembali ke menu utama.

    Catatan: Sebenarnya, NAT (Network Address Translation) juga memungkinkan untuk terkoneksi ke internet namun dengan cara yang berbeda (IP Address akan disamarkan, akan kita bahas jika ada kesempatan).

    ![](./assets/Membuat%20VM%20Baru/16.%20Atur%20network%20adapter%2C%20pilih%20Bridged%20Adapter.png)

8. Klik "Start" untuk menyalakan VM Ubuntu Server. Kemudian, window baru akan muncul. Window tersebut adalah VM yang telah dibuat. VM melakukan booting terhadap file ISO yang dimasukkan sebelumnya.

    ![](./assets/Membuat%20VM%20Baru/17.%20Klik%20menu%20Start%2C%20maka%20VirtualBox%20akan%20menyalakan%20VM%20yang%20baru%20saja%20dibuat.png)

9. Karena VM belum terinstall Ubuntu Server, maka bootloader (GRUB) akan menampilkan "Try or Install Ubuntu Server". Langkah-langkah menginstall Ubuntu Server akan dilanjutkan pada subbab setelah ini.

    ![](./assets/Membuat%20VM%20Baru/18.%20Bootloader%20Ubuntu%20Server%20berhasil%20dijalankan%20oleh%20VM%2C%20tetapi%20Ubuntu%20Server%20masih%20belum%20terinstall%20ke%20Virtual%20Machine.png)

    **Catatan Penting**!

    Jika ditemukan error "Kernel Panic" saat melakukan booting ataupun setelah klik "Try or Install Ubuntu Server" seperti gambar di bawah, jangan khawatir! Error tersebut dapat disandingkan dengan Blue Screen of the Death di Windows. Kita akan perbaiki itu dengan mudah.

    ![](./assets/Menginstall%20Ubuntu%20Server%20di%20VM/19.%20Kasus%20Error%20Kernel%20Panic.png)

    Matikan VM dengan cara klik tanda silang di window. Akan muncul pop up, pilih "Power off the machine" kemudian klik "OK" sehingga akan kembali ke menu utama VirtualBox.

    Setelah itu, klik Settings $\rightarrow$ System $\rightarrow$ Processor. Lalu, naikkan jumlah CPU dari 1 menjadi 2 atau 3 seperti gambar di bawah ini.

    ![](./assets/Menginstall%20Ubuntu%20Server%20di%20VM/20.%20Perbaiki%20error%20dengan%20cara%20menaikan%20jumlah%20CPU%20yang%20digunakan.png)

    Kemudian, klik "OK" dan nyalakan lagi VM dengan klik "Start".



### 3.2 Menginstall Ubuntu Server di Virtual Machine

1. Setelah klik "Try or Install Ubuntu Server" di GRUB. Akan muncul tampilan seperti di bawah ini. Tampilan tersebut adalah proses booting dari Ubuntu Server. Tunggu saja yaa.

    ![](./assets/Menginstall%20Ubuntu%20Server%20di%20VM/21.%20Jika%20muncul%20tampilan%20seperti%20ini%2C%20artinya%20kernel%20sedang%20melakukan%20booting..png)

2. Setelah proses booting, maka installer akan dijalankan karena Ubuntu Server masih belum terinstall pada VM.

    **Catatan Penting!**
    
    Installer Ubuntu Server berjenis Text Line Interface, sehingga kita tidak bisa menggunakan mouse di sini. Hanya bisa menggunakan keyboard (UP, DOWN, dan ENTER) dan tombol lain untuk mengetik. Cursor pilihan ditandai dengan warna **hijau**.

    Setelah masuk ke installer, akan dihadapkan dengan pilihan bahasa. Pilih "English", kemudian klik ENTER. 

    ![](./assets/Menginstall%20Ubuntu%20Server%20di%20VM/22.%20Karena%20OS%20belum%20terinstall%2C%20maka%20installernya%20dijlankan.%20Pertama-tama%20pilih%20bahasa..png)

3. Kemudian akan muncul pemberitahuan bahwa ada update installer. Lewati saja dengan memilih "Continue without updating" karena tidak ada perubahan signifikan setelah update.

    ![](./assets/Menginstall%20Ubuntu%20Server%20di%20VM/23.%20Terdapat%20update%20installer%2C%20lewati%20langkah%20ini%20dengan%20cara%20pilih%20Continue%20without%20updating%20(tidak%20ada%20efek%20signifikan).png)

4. Akan ada pilihan layout keyboard. Biarkan default, kemudian pilih "Done".

    ![](./assets/Menginstall%20Ubuntu%20Server%20di%20VM/24.%20Pilih%20layout%20keyboard%2C%20biarkan%20konfigurasi%20default.png)

5. Akan ada pilihan tipe instalasi. Pilih saja opsi minimum dengan cara mengarahkan cursor ke menu "Ubuntu Server (minimized)" lalu klik ENTER. Setelah itu, pilih "Done".

    ![](./assets/Menginstall%20Ubuntu%20Server%20di%20VM/25.%20Pilih%20jenis%20instalasi%2C%20opsional.%20Tapi%20asisten%20praktikum%20merekomendasikan%20minimalis%20saja%20agar%20lebih%20ringan..png)

6. Akan ada menu konfigurasi koneksi jaringan. Bila belum ada IP address seperti yg ada di samping DHCPv4, tunggu hingga ada. Apabila sudah ada, pilih "Done".

    ![](./assets/Menginstall%20Ubuntu%20Server%20di%20VM/26.%20Atur%20koneksi%20internet.%20Bila%20belum%20ada%20IP%20address%20seperti%20yg%20%20di%20samping%20DHCPv4%2C%20tunggu%20hingga%20ada.png)

7. Akan ada menu konfigurasi proxy. Karena kita tidak memiliki proxy server, biarkan kosong kemudian pilih "Done".

    ![](./assets/Menginstall%20Ubuntu%20Server%20di%20VM/27.%20Pengaturan%20Proxy%2C%20karena%20kita%20tidak%20memiliki%20server%20proxy%2C%20lewati%20konfigurasi%20ini.png)

8. Akan ada menu konfigurasi mirror repository, biarkan default saja kemudian pilih "Done". Kita dapat ubah nanti jika memang diperlukan.

    **FYI** : Mirror repository adalah repository duplikat dari repository utama Ubuntu yang menyimpan package atau software sehingga dapat diinstall oleh user. Dengan menggunakan mirror repository (terutama yang lokal), biasanya instalasi package/software akan lebih cepat.

    Kampus-kampus dan penyedia jasa internet biasanya menyediakan mirror local tersebut. Sebagai contoh:

    | Institusi | Repository Lokal |
    | -- | -- |
    | Telkom University | https://mirror.telkomuniversity.ac.id/ubuntu |
    | Unair | https://mirror.unair.ac.id/ubuntu |
    | DataUtamaNET | https://kartolo.sby.datautama.net.id/ubuntu |
    | Biznet Gio Cloud | http://mirror.biznetgio.com/ubuntu |

    ![](./assets/Menginstall%20Ubuntu%20Server%20di%20VM/28.%20Atur%20mirror%20repository%2C%20gunakan%20default%20saja.%20Mirror%20adalah%20repository%20tempat%20menyimpan%20package%20atau%20software%20sehingga%20dapat%20diinstall%20Ubuntu.%20Pemilihan%20mirror%20dapat%20m.png)

9. Akan ada menu konfigurasi layout storage. Karena kita sedang belajar tentang sistem operasi, maka tidak afdol jika kita tidak mengkonfigurasi layout storage kita sendiri. Maka dari itu, pilih "Custom storage layout", kemudian pilih "Done".

    ![](./assets/Menginstall%20Ubuntu%20Server%20di%20VM/29.%20Atur%20layout%20storage.%20Karena%20kita%20sedang%20belajar%20sistem%20operasi%2C%20tidak%20elok%20kalau%20kita%20tidak%20mengatur%20sendiri%20layout%20storagnya.%20Sehingga%2C%20pilih%20custome%20storge%20layout%20.png)

10. Setelah itu, akan ada menu untuk mengkonfigurasi atau mempartisi sendiri bagaimana layout storage untuk Ubuntu Server kita.

    Dalam praktikum ini, kita akan membuat partisi storage seperti berikut ini:

    | Ukuran Partisi | Format | Mount Point |
    | -- | -- | -- |
    | 8 GB | ext4 | / (root directory) |
    | 7 GB | ext4 | /home (home directory) |
    | 1 GB | swap space | $-$ |

    Karena prosesnya cukup rumit dan harus hati-hati, silakan menonton video tutorial singkat dari asisten praktikum melalui link berikut: [**Tutorial Partisi Storage**](https://drive.google.com/file/d/1PQETeVENZ2F6yhzkoUln961RFlqm1T-5/view?usp=sharing).

    Silakan disimak dengan baik, yaa!

11. Setelah selesai melakukan partisi storage. Akan ada pengaturan profil user dan server. Silakan isikan sesuai dengan identitas teman-teman yaa. Setelah itu, pilih "Done".

    **Catatan Penting!**

    Jangan sampai lupa dengan username dan password karena akan digunakan untuk login, install package, update, dan hal lainnya yang memerlukan administrator (root) privilege.

    ![](./assets/Menginstall%20Ubuntu%20Server%20di%20VM/31.%20Mengatur%20identitas%20server%20dan%20user.png)

12. Akan ada pilihan untuk upgrade ke Ubuntu Pro. Lewati langkah ini karena kita tidak memerlukan upgrade tersebut. Pilih "Skip for now" kemudian "Continue".

    ![](./assets/Menginstall%20Ubuntu%20Server%20di%20VM/32.%20Pilihan%20Ubuntu%20Pro.%20Pilih%20Skip%20for%20now%20karena%20Ubuntu%20Pro%20berbayar%20untuk%20lebih%20dari%203%20komputer%20dan%20kita%20tidak%20butuh%20itu%20untuk%20mempelajari%20matkul%20ini%20.png)

12. Akan ada menu konfigurasi SSH (Secure Shell Protokol). Pilih saja "Install OpenSSH Server", kemudian  pilih "Done".

    ![](./assets/Menginstall%20Ubuntu%20Server%20di%20VM/33.%20Konfigurasi%20SSH.%20Pilih%20install%20OpenSSH%20server.png)

13. Terakhir, kita akan diberikan opsi untuk menginstall beberapa software tambahan. Saat ini, kita tidak membutuhkan software-software tersebut. Pilih "Done" tanpa memilih software apapun. Jika nanti ternyata ada software yang dibutuhkan, kita bisa melakukan instalasi secara mandiri.

    ![](./assets/Menginstall%20Ubuntu%20Server%20di%20VM/34.%20Pilihan%20install%20aplikasi%20tambahan.%20Tidak%20perlu%20pilih%20apapun%20karena%20bisa%20diinstall%20nanti%20jika%20memang%20dibutuhkan..png)

14. Setelah itu, proses instalasi sistem akan dilakukan berdasarkan semua konfigurasi yang kita buat. Tunggu saja hingga selesai yaa!

    Catatan: jika penasaran dengan apa yang terjadi saat instalasi sistem, kalian bisa pilih "View full log".

    ![](./assets/Menginstall%20Ubuntu%20Server%20di%20VM/35.%20Proses%20instalasi%20dimulai%20(pada%20gambar%20di%20atas%2C%20kernel%20sedang%20dalam%20proses%20instalasi).png)

15. Jika instalasi sudah selesai (ditandai dengan tulisan "Install Complete!" di bagian atas), pilih "Reboot Now". Tunggu hingga proses booting selesai.

    ![](./assets/Menginstall%20Ubuntu%20Server%20di%20VM/36.%20Proses%20instalasi%20berhasil%2C%20pilih%20Reboot%20Now.%20Jika%20ada%20Failed%20to%20Umounting%20CDROM%2C%20klik%20Enter.png)

16. Jika booting sudah selesai, maka kita akan dihadapkan dengan layar login. Masukkan username dan password yang telah dibuat pada proses intalasi.

    **Catatan Penting!**

    Jika kolom password tetap kosong walaupun sudah diisi, jangan khawatir! Hal tersebut adalah fitur pada semua sistem operasi berbasis Linux untuk pertimbangan keamanan sistem.

    ![](./assets/Menginstall%20Ubuntu%20Server%20di%20VM/37.%20Login%20menggunkan%20username%20dan%20password.png)

17. Selamat, Kamu telah berhasil login ke Ubuntu Server! Dengan ini, proses intalasi telah berhasil.

    ![](./assets/Menginstall%20Ubuntu%20Server%20di%20VM/38.%20Login%20berhasil.png)

## Penutup

Demikian adalah pembahasan mengenai sistem operasi secara umum, sistem operasi berbasis Linux, hingga opsi-opsi untuk menginstallnya. Opsi instalasi yang akan digunakan adalah menggunakan teknologi virtualisasi. Untuk itu, telah dijelaskan langkah-langkah mulai dari mempersiapkan file ISO Ubuntu Server & aplikasi Oracle VirtualBox hingga menginstall Ubuntu Server di dalam VM yang telah dibuat.