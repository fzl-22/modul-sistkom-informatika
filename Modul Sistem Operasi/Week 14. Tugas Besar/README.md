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

Coming Soonn
