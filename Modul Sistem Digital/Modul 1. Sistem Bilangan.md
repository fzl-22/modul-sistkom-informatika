# 1. Sistem Bilangan



# 2. Operasi Bilangan Biner

Sama seperti bilangan desimal, bilangan biner juga memiliki operasi-operasi dasar seperti penjumlahan, pengurangan, perkalian, dan pembagian.

Dalam operasi bilangan biner, terdapat istilah penting, yaitu `carry` (bilangan yang disimpan, yang terjadi apabila hasil penjumlahan setiap digit bernilai lebih dari atau sama dengan `r`, yaitu basis bilangan yang dioperasikan). Agar tidak bingung, perhatikan contoh penjumlahan bilangan desimal berikut:

```
   01  <-- carry
   547
    25 +
   ----
   572
```

Pada penjumlahan desimal (basis $r=10$) 547 dengan 25, langkah-langkahnya adalah sebagai berikut:
1. Jumlahkan $7+5$, hasilnya adalah 12. Karena $12\geq r$, maka hasilnya adalah 2 dengan *carry* 1 untuk penjumlahan pada digit berikutnya.
2. Jumlahkan $4+2$ kemudian jumlahkan dengan $carry$ yang dihasilkan pada operasi sebelumnya ($carry=1$), hasilnya adalah $7$. Karena $7<r$, maka tidak memiliki $carry$ atau $carry=0$. 
3. Jumlahkan $5+0$ kemudian jumlahkan dengan $carry$ yang dihasilkan pada operasi sebelumnya ($carry=0$), hasilnya adalah $5$.
4. Karena sudah tidak ada digit yang dioperasikan lagi, maka hasilnya adalah $572$.

Konsep diatas akan dipakai juga pada operasi bilangan biner. Yuk simak penjelasan beberapa subbab di bawah ini :)

## 2.1 Penjumlahan Bilangan Biner

Dalam operasi penjumlahan bilangan biner, beberapa fakta berikut perlu diketahui:
- $0+0=0$
- $0+1=1$
- $1+0=1$
- $1+1=10$ ⟶ $0$ dan carry $1$ ditempatkan pada posisi berikutnya
- $1+1+1=11$ ⟶ $1$ dan carry $1$ ditempatkan pada posisi berikutnya.

Sebagai contoh, $1101+101$ apabila dijumlahkan akan menghasilkan $10010$.

```
   101  <-- carry
   1101
    101 +
   -----
  10010
```

Langkah-langkahnya adalah sebagai berikut:
1. Jumlahkan $1+1$, hasilnya adalah $10$. Maka, ambil hasil $0$ dan tempatkan $carry=1$ pada posisi berikutnya.
2. Jumlahkan $0+0$, hasilnya adalah $0$. Maka, ambil hasil $0$ tanpa carry (atau $carry=0$).
3. Jumlahkan $1+1$, hasilnya adalah $10$. Maka, ambil hasil $0$ dan tempatkan $carry=1$ pada posisi berikutnya.
4. Jumlahkan $1+0$ kemudian jumlahkan juga dengan $carry$ yang dihasilkan dari posisi sebelumnya ($carry=1$), hasilnya adalah $10$.
5. Karena sudah tidak ada digit yang dioperasikan lagi, maka hasilnya adalah $10010$.

## 2.2 Pengurangan Bilangan Biner

Pengurangan bilangan biner dapat direpresentasikan menjadi penjumlahan bilangan biner yang memiliki tanda *(sign)* yang berbeda. Sebagai contoh pada bilangan desimal, kita dapat merepresentasikan $55-45$  menjadi $55+(-45)$. Untuk itu, kita perlu belajar terlebih dahulu mengenai bilangan bertanda (*signed number*).

### 2.2.1 Bilangan Bertanda

Sebagian besar komputer digital menangani bilangan negatif sebagai bilangan positif, sehingga diperlukan tanda (*sign*) bilangan $+$ (positif) atau $-$ (negatif). Tanda tersebut diwakili oleh satu bit yang dinamakan *sign bit* dan terletak di posisi bit paling kiri atau MSB (*most significant bit*). *Sign bit* ini digunakan untuk merepresentasikan bilangan positif dan negatif dalam bentuk biner.

Pada gambar di bawah ini, terlihat bahwa bilangan $45$ dan $-45$ terdiri dari 1 *sign bit* dan 7 *magnitude bit*. *Magnitude bit* ini merupakan bilangan biner yang nilainya sama dengan bilangan desimal yang mewakilinya. Prinsip ini dikenal dengan nama "*sign magnitude system*" untuk menyatakan bilangan biner bertanda.

![[sign_and_magnitude-white.png]]

Karena untuk melakukan pengurangan bilangan biner kita perlu mengubah suatu bilangan biner positif menjadi bilangan negatif, maka kita memerlukan prinsip ini. Untuk itu, sistem yang digunakan adalah sistem *2's complement* karena umum digunakan Langkah-langkahnya adalah sebagai berikut:

1. **Ubah ke bentuk 1's complement**. Komplemen 1 dari sebuah bilangan biner diperoleh dari menukar nilai setiap bit dari 0 ke 1, dan sebaliknya. Sebagai contoh:
	```
	101101   <-- bilangan biner asal (45)
	⬇⬇⬇⬇⬇⬇
	010010   <-- bentuk 1's komplemen dari bilangan biner asal
	```
2. **Ubah ke bentuk 2's complement**. Komplemen 2 dari sebuah bilangan biner diperoleh dari hasil 1's complement ditambah dengan 1 pada posisi LSB (*least significant bit*).
	```
	101101   <-- bilangan biner asal (45)
	⬇⬇⬇⬇⬇⬇
	010010   <-- bentuk 1's komplemen dari bilangan biner asal
	
	010010
	     1 + <-- jumlahkan dengan 1 pada posisi LSB
	-------
	010011   <-- bentuk 2's komplemen dari bilangan biner asal
	```

Sistem 2's complement ini digunakan untuk menyatakan bilangan bertanda dengan ketentuan berikut (**Catatan:** ketentuan ini perlu diingat):
1. Jika bilangan positif, magnitude dinyatakan dalam bentuk bilangan biner asli dan *sign bit* bernilai 0 pada MSB.
2. Jika bilangan negatif, magnitude dinyatakan dalam bentuk *2's complement* dan *sign bit* bernilai 1 pada MSB.

Dua ketentuan di atas dapat dilihat secara lebih jelas pada gambar di bawah ini.
![[2's complement system.png]]

### 2.2.2 Pengurangan Bilangan Bertanda

Setelah mengetahui konsep sistem *2's complement*. Kita kembali untuk menyelesaikan pengurangan $55-45$ dalam bentuk biner. Kira representasikan pengurangan tersebut menjadi penjumlahan, yaitu $55+(-45)$. Pertama-tama, cari bentuk *2's complement* dari -45 dulu:

```
+45 -->  0101101 (sign bit = 0)
1'c -->  1010010
2'c -->  1010011 (sign bit = 1)
```

Setelah itu, jumlahkan +55 dengan 2's complement dari -45:

```
         +------> sign bit
         |
+55 -->  0 110111
-45 -->  1 010011 +
------------------
        10 001010
        |
        +---> carry ini diabaikan dan sign bit 0, sehingga hasilnya adalah 0001010 (+10) sesuai ketentuan (1)
```

**Catatan: Apabila sign bit = 0 (positif), ingat ketentuan 1!**

Bagaimana jika pengurangan $45 - 55$? Mudah saja, kita representasikan ekspresi tersebut menjadi $45+(-55)$.  Pertama, cari bentuk *2's complement* dari -55 terlebih dahulu:

```
+55 -->  0110111 (sign bit = 0)
1'c -->  1001000
2'c -->  1001001 (sign bit = 1)
```

Kemudian, coba jumlahkan +45 dengan *2's complement* dari -55:
```
         +------> sign bit
         |
+45 -->  0 101101
-55 -->  1 001001 +
------------------
        x1 110110
        |
        +---> tidak ada carry dan sign bit = 1 sehingga hasilnya adalah 1110110
```

Dari perhitungan di atas, didapat hasil 1110110. Perhatikan bahwa sign bit = 1 (negatif), sehingga magnitudenya (110110) masih dinyatakan dalam bentuk *2's complement* (**ingat ketentuan 2**). Ubah ke bentuk bilangan biner aslinya dengan cara mengubahnya ke bentuk *2's complement* lagi.

```
magnitude (2'c) --> 110110
1'c             --> 001001
                         1 +
	                ------
asli            --> 001010 
```

Didapatkan sebelumnya sign bit = 1 dan bentuk bilangan biner aslinya adalah 001010. Sehingga hasil akhirnya adalah 1001010 ($-10_{10}$)

**Catatan: Apabila sign bit = 1 (negatif), ingat ketentuan 2!**

## 2.3 Perkalian Bilangan Biner

Perkalian bilangan biner dilakukan dengan cara yang sama dengan perkalian bilangan desimal, hanya saja lebih mudah karena hanya melibatkan digit 0 dan digit 1.

Namun, ada beberapa hal yang perlu diingat yaitu:
- $0\times 0= 0$
- $0\times 1=0$
- $1\times 0=0$
- $1\times 1=1$

Sebagai contoh adalah perkalian bilangan biner dari $99_{10}$ dengan $11_{10}$:

```
      1001     <-- multiplicand = 9
      1011 x   <-- multiplier = 11
      ----
      1001
     1001
    0000
   1001   +
   -------
   1100011     <-- hasil akhir = 99
```

## 2.4 Pembagian Bilangan Biner

Pembagian bilangan biner dengan bilangan biner lainnya juga sama mudahnya karena hanya melibatkan digit 0 dan 1. Beberapa hal berikut perlu diingat:
- $0\div 1= 0$
- $1\div1=1$ 
- Selain itu, pembagian oleh 0 terdefinisi.

Sebagai contoh, berikut ada operasi pembagian bilangan biner dari 99 dengan 11.

```
           0001001  <-- hasil bagi
          ________
    1011 / 1100011
           1011 -
           ----
           0001011
              1011 -
           -------
           0000000
```

# Tugas
1. Konversikan bilangan-bilangan di bawah ini menjadi bilangan dengan basis yang diminta oleh soal:
		a. $101011_2=\quad ? \quad (\text{basis}\ 16)$
		b. $3F_{16}=\quad ? \quad (\text{basis}\ 8)$
		c. $34_8=\quad ?\quad (\text{basis}\ 10)$
		d. $28_{16}=\quad ? \quad (\text{basis}\ 2)$

2. Carilah *1's complement* dan *2's complement* dari bilangan-bilangan berikut ini:
		a. $100111_2$
		b. $1100111_2$

3. Selesaikanlah operasi-operasi aritmatika di bawah ini dengan menggunakan operasi bilangan biner:
		a. $11011_2+1111_2=\quad ? \quad$
		b. $10101_2-11011=\quad ? \quad$
		c. $1101\times 11=\quad ? \quad$
		d. $111000\div 101=\quad ? \quad$

Note:
1. Kerjakan dalam waktu 60 menit di kertas beserta cara/proses perhitungan, apabila kesulitan silakan panggil asisten praktikum untuk bantuan.
2. Apabila sudah selesai, berikan kertas jawaban ke asisten praktikum untuk diberi nilai.