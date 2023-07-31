# Tugas Besar: FUSE by API Requests (PokeAPI)



## Konfigurasi Workspace

Buat 1 direktori dengan nama `pokemon_fs`. Kemudian masuk ke direktori tersebut. Di dalam direktori ini, source code dan folder library `librequests` dan `json-parser` akan disimpan. Struktur folder nantinya adalah sebagai berikut (ikuti langkah di section selanjutnya terlebih dahulu):

```
pokemon_fs
  |
  |-- json-parser/
  |
  |-- librequests/
  |
  |-- librequests.a
  |
  |-- request.h
  |
  |-- json.c
  |
  |-- json.h
  |
  |-- main.c
```

## Package Requirements

1. `git`

    Git merupakan sebuah *version control system*. Pada tugas ini, git akan digunakan untuk mengambil package (`clone`) dari Github. Cara instalasinya adalah sebagai berikut:

    ```bash
    sudo apt update
    sudo apt install git
    ```

    Pastikan git sudah terinstall menggunakan command berikut:

    ```bash
    git --version
    ```

    Setelah itu, lakukan konfigurasi tambahan dengan command berikut:

    ```bash
    git config --global user.name "<nama lengkap>" # git config --global user.name "John Doe"
    git config --global user.email "<email>" # git config --global user.email "example@gmail.com"
    ```

2. `librequests`

    `librequests` merupakan open source package untuk melakukan API request ke https://pokeapi.co. Pertama-tama, install dependency dari library ini terlebih dahulu:

    ```
    sudo apt-get install libcurl4-openssl-dev
    ```

    Di dalam direktori `pokemon_fs`, clone source code dari Github menggunakan command berikut:

    ```
    git clone https://github.com/offlinemark/librequests.git
    ```

    Masuk ke dalam direktory `librequests`:

    ```
    cd librequests
    ``` 

    Lakukan build library ini dengan beberapa command berikut:

    ```
    mkdir build && cd build
    cmake ..
    cmake --build .
    ```

    Setelah itu, pindahkan file `librequests.a` dan `requests.h` ke direktori project sejajar dengan `main.c`

    File `librequests.a` ada di direktori `librequests/build/src/librequests.a`. Sedangkan, `requests.h` ada di direktori `librequests/include/requests.h`.

    Untuk pengujian library ini, silakan ikuti dokumentasi yang ada di https://github.com/offlinemark/librequests.

2. `json-parser`

    Library ini digunakan untuk melakukan parsing dari JSON yang dihasilkan oleh API requests ke https://pokeapi.co.

    Pertama-tama, clone source code dari Github ke direktori project menggunakan perintah berikut:

    ```
    git clone https://github.com/json-parser/json-parser.git
    ```

    Masuk ke direktori `json-parser`, kemudian pindahkan file `json.c` dan `json.h` ke direktori project sejajar dengan `main.c`.

    Untuk pengujian library ini, silakan ikuti dokumentasi yang ada di https://github.com/json-parser/json-parser.

4. `build-essential` dan `libfuse`

    Jika belum menginstall `build-essential` dan `libfuse` di modul sebelumnya, install package ini menggunakan perintah:

    ```
    sudo apt update
    sudo apt install build-essential libfuse*
    ```
## Tugas Besar

![](./assets/cute-pikachu-6o.jpg)

Buat program FUSE untuk mount `/home/{user}/Documents` ke `{nama_folder}` dimana program akan melakukan get request pokemon dari API https://pokeapi.co dengan endpoint berikut:

```
get https://pokeapi.co/api/v2/pokemon/{nama_pokemon}
```

dan **simpan informasi sebanyak mungkin data pokemon dari PokeAPI**.

**Run**

```
./pokemon_fuse {nama_folder} {nama_pokemon}
```

Maka isi dari mounted folder adalah sebagai berikut:

```
{nama_folder}/{nama_pokemon}/forms/{all_form}.png
{nama_folder}/{nama_pokemon}/moves/mega-punch.txt -> version_details
{nama_folder}/{nama_pokemon}/forms/
{nama_folder}/{nama_pokemon}/moves/
{nama_folder}/{nama_pokemon}/{all_folder_based_on_api_information}
```

Cara konsumsi dari API dapat menggunakan `librequests` untuk mengambil data JSON dari API. Kemudian, JSON yang diterima di dalam program bisa di-parsing menggunakan library `json-parser`.

**Ketentuan**:

1. Pengerjaan tugas besar dapat menggunakan satu di antara dua bahasa pemrograman (C atau Python), dengan ketentuan berikut:
        
    * Bahasa C, mendapat nilai maksimum $A \geq 80.0$
    * Bahasa Python, mendapat nilai maksimum $AB < 80.0$

2. Deadline : 11 Agustus 2023
3. Template Laporan Tugas Besar: [Template Laporan Tugas Besar](./assets/Template%20Laporan%20Tugas%20Besar%20-%20Pemrograman%20Sistem%20Komputer.docx)
4. Dikumpulkan di form berikut: [Form Pengumpulan Laporan Tugas Besar](https://forms.gle/hPjZcdy1EZ8Dh7CB8)


