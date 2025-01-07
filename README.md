# projek-uas

# OOP

Nama : ghefira azka fardani 

Kelas : TI.24.A5

NIM : 312410521

## code program 
### 1. Class ```Mahasiswa```

* Kelas ```Mahasiswa``` adalah model yang menyimpan informasi terkait mahasiswa, yaitu ```nama``` dan ```nim```.
  
* Constructor ```__init__``` digunakan untuk inisialisasi objek dengan atribut ```nama``` dan ```nim```.
  
```phython
class Mahasiswa:
    def __init__(self, nama, nim):
        self.nama = nama
        self.nim = nim

```

### 2. Class ```MahasiswaProcess```

* Kelas ini bertanggung jawab untuk memproses data mahasiswa, seperti menambah mahasiswa dan mendapatkan daftar mahasiswa.
  
* Constructor ```__init__``` menginisialisasi daftar kosong ```mahasiswa_list```.
  
* Method ```tambah_mahasiswa``` digunakan untuk menambahkan mahasiswa ke dalam daftar dengan memvalidasi data.
  
  * Validasi:
    
    * Nama dan NIM tidak boleh kosong.
      
    * NIM harus berupa angka (menggunakan .isdigit()).
      
* Method get_mahasiswa mengembalikan daftar mahasiswa yang telah ditambahkan.
  
```phython
class MahasiswaProcess:
    def __init__(self):
        self.mahasiswa_list = []

    def tambah_mahasiswa(self, nama, nim):
        if not nama or not nim:
            raise ValueError("Nama dan NIM tidak boleh kosong.")
        if not nim.isdigit():
            raise ValueError("NIM harus berupa angka.")
        mahasiswa = Mahasiswa(nama, nim)
        self.mahasiswa_list.append(mahasiswa)

    def get_mahasiswa(self):
        return self.mahasiswa_list
```

### 3. Class ```MahasiswaView```

* Kelas ini bertanggung jawab untuk menampilkan data mahasiswa ke layar.
  
* Method ```tampilkan_mahasiswa``` menerima daftar mahasiswa dan menampilkan informasi mahasiswa dalam format tabel dengan kolom ```NIM``` dan ```Nama```.
  
``` python
class MahasiswaView:
    def tampilkan_mahasiswa(self, mahasiswa_list):
        print(f"{'NIM':<10} {'Nama':<20}")
        print("-" * 30)
        for mhs in mahasiswa_list:
            print(f"{mhs.nim:<10} {mhs.nama:<20}")
```

### 4. Fungsi ```main()```

* Fungsi utama yang menggabungkan semua komponen:
  
  * Menggunakan objek dari ```MahasiswaProcess``` dan ```MahasiswaView```.
    
  * Program meminta input nama dan NIM dari pengguna dalam sebuah loop hingga pengguna mengetik ```'exit'```.
    
  * Data mahasiswa akan divalidasi dan ditambahkan ke dalam daftar jika valid.
    
  * Jika terjadi error (misalnya input NIM bukan angka atau ada kolom yang kosong), program akan menangkapnya dan menampilkan pesan kesalahan.
    
  * Setelah pengguna berhenti memasukkan data, program akan menampilkan daftar mahasiswa yang sudah dimasukkan.
    
``` python
def main():
    process = MahasiswaProcess()
    view = MahasiswaView()

    while True:
        try:
            nama = input("Masukkan nama mahasiswa (atau ketik 'exit' untuk keluar): ")
            if nama.lower() == 'exit':
                break
            nim = input("Masukkan NIM mahasiswa: ")
            process.tambah_mahasiswa(nama, nim)
        except ValueError as e:
            print(f"Error: {e}")

    # Tampilkan data mahasiswa
    mahasiswa_list = process.get_mahasiswa()
    view.tampilkan_mahasiswa(mahasiswa_list)
```

### 5. Perbaikan pada ```if _name_ == "_main_"```

* Pada bagian akhir kode, Anda mencoba untuk memeriksa apakah file dijalankan sebagai program utama menggunakan kode ```if _name_ == "_main_"```.
  
* Seharusnya menggunakan ```if __name__ == "__main__":``` (dengan dua garis bawah di kiri dan kanan ```name``` dan ```main```), karena ini adalah cara yang benar dalam Python untuk memeriksa apakah skrip dijalankan langsung atau diimpor sebagai modul.
  
```phython 
if __name__ == "__main__":
    main()
```
## video program 

https://youtu.be/l6tHe6073NA?feature=shared







