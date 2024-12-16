<div align="center">**Source: `RHCSA® Red Hat® Enterprise Linux® 8 (UPDATED) Training and Exam Preparation Guide, EX200, Edisi Kedua, November 2020`** 
`Hal: 131-133` </div>

### **Penjelasan Singkat**  
**Compression** dan **Archiving** adalah dua proses yang sering digunakan bersama untuk mengelola file dan direktori.  

1. **Compression**: Mengurangi ukuran file agar lebih hemat ruang.  
2. **Archiving**: Menggabungkan banyak file atau direktori menjadi satu file arsip.  

Kombinasi ini memudahkan proses **backup**, **transfer file**, dan **pengelolaan penyimpanan**.  

### **Alat yang Umum Digunakan**  
1. **gzip** dan **gunzip**:  
   - Digunakan untuk **mengompres** file dengan format `.gz`.  
   - **gunzip** digunakan untuk **mendekompres** file.  

2. **bzip2** dan **bunzip2**:  
   - Mirip gzip tetapi lebih efisien dalam kompresi, menghasilkan format `.bz2`.  

3. **tar**:  
   - Digunakan untuk **mengarsipkan** file/direktori menjadi satu file.  
   - Bisa dikombinasikan dengan kompresi (`gzip` atau `bzip2`).  

4. **star**:  
   - Versi lanjutan dari `tar` yang mendukung atribut khusus seperti **ACL** dan **SELinux contexts**.  

---

### **Contoh Simpel**  

#### **1. Kompresi dengan gzip**  
Misalnya, Anda memiliki file bernama `data.txt`:  
- **Kompresi** file:  
   ```bash
   gzip data.txt
   ```  
   - Output: File akan menjadi `data.txt.gz`.  
   - Ukurannya lebih kecil.  

- **Dekompresi** file:  
   ```bash
   gunzip data.txt.gz
   ```  
   - File kembali menjadi `data.txt`.  

---

#### **2. Arsipkan File dan Kompres dengan tar**  
Misalkan Anda memiliki direktori `myfolder` berisi banyak file.  
- **Membuat arsip sekaligus kompresi menggunakan gzip**:  
   ```bash
   tar -czvf archive.tar.gz myfolder
   ```  
   - Penjelasan:  
     - `c` → create (buat arsip)  
     - `z` → kompresi dengan gzip  
     - `v` → tampilkan prosesnya (verbose)  
     - `f` → nama file arsip (archive.tar.gz)  

- **Ekstrak arsip terkompresi**:  
   ```bash
   tar -xzvf archive.tar.gz
   ```  
   - Direktori `myfolder` akan dikembalikan.  

---

#### **3. Menggunakan bzip2 dengan tar**  
- **Membuat arsip dengan kompresi bzip2**:  
   ```bash
   tar -cjvf archive.tar.bz2 myfolder
   ```  
   - Output: `archive.tar.bz2` dengan ukuran lebih kecil.  

- **Ekstrak arsip bzip2**:  
   ```bash
   tar -xjvf archive.tar.bz2
   ```  

---

### **Contoh Menggunakan star**  
`star` mendukung **extended attributes** seperti ACL dan SELinux contexts.  
- **Buat arsip**:  
   ```bash
   star -c -f archive.star myfolder
   ```  
- **Ekstrak arsip**:  
   ```bash
   star -x -f archive.star
   ```  

---

### **Kesimpulan**  
**Compression dan Archiving** digunakan untuk menghemat ruang, mempercepat transfer file, dan memudahkan backup.  
- **gzip**: Kompresi cepat.  
- **bzip2**: Kompresi lebih efisien.  
- **tar/star**: Menggabungkan file/direktori menjadi satu arsip, dengan kemampuan mempertahankan atribut file.  

**Contoh Kombinasi Cepat**:  
```bash
tar -czvf backup.tar.gz /home/user/data
```  
Perintah ini membuat arsip `backup.tar.gz` dari direktori `/home/user/data`.

### **Penjelasan Singkat Tentang `tar`**  
**`tar`** adalah perintah yang digunakan untuk:  
1. **Mengarsipkan** file/direktori menjadi satu file yang disebut **tarball** atau **tarfile**.  
2. **Mengkompresi** arsip menggunakan alat tambahan seperti **gzip** atau **bzip2**.

**Format tarball** biasanya berakhiran **`.tar`**, sedangkan jika dikompres, bisa menjadi **`.tar.gz`** (gzip) atau **`.tar.bz2`** (bzip2).

---

### **Menggunakan Sintaks Umum `tar` (Using Tar)**  
```bash
tar [opsi] nama_arsip.tar nama_file/direktori
```
**Opsi yang Sering Digunakan**:  
- **`c`**: Create → Membuat arsip.  
- **`x`**: Extract → Mengekstrak arsip.  
- **`v`**: Verbose → Menampilkan proses.  
- **`f`**: File → Menentukan nama arsip.  
- **`z`**: Gunakan kompresi **gzip**.  
- **`j`**: Gunakan kompresi **bzip2**.  

---

### **Contoh Penggunaan `tar`**

#### **1. Membuat Arsip Sederhana (.tar)**  
Misalkan ada folder bernama `data_folder`.  
- **Perintah**:  
   ```bash
   tar -cvf archive.tar data_folder
   ```  
- **Penjelasan**:  
   - `c` → Buat arsip.  
   - `v` → Tampilkan proses.  
   - `f` → Nama arsip (`archive.tar`).  
   - `data_folder` → Direktori yang diarsipkan.  

- **Hasil**: File `archive.tar` berisi arsip dari `data_folder`.  

---

#### **2. Membuat Arsip dengan Kompresi Gzip (.tar.gz)**  
- **Perintah**:  
   ```bash
   tar -czvf archive.tar.gz data_folder
   ```  
- **Penjelasan**:  
   - `z` → Menggunakan kompresi **gzip**.  

- **Hasil**: File `archive.tar.gz` yang lebih kecil ukurannya.  

---

#### **3. Mengekstrak Arsip (.tar)**  
Untuk mengekstrak arsip `archive.tar` ke direktori saat ini:  
- **Perintah**:  
   ```bash
   tar -xvf archive.tar
   ```  
- **Penjelasan**:  
   - `x` → Ekstrak arsip.  

---

#### **4. Mengekstrak Arsip yang Dikompres (.tar.gz)**  
Untuk mengekstrak arsip `archive.tar.gz`:  
- **Perintah**:  
   ```bash
   tar -xzvf archive.tar.gz
   ```  
- **Penjelasan**:  
   - `z` → Untuk file terkompresi **gzip**.  

---

#### **5. Melihat Isi Arsip Tanpa Mengekstrak**  
Untuk melihat isi dari arsip `archive.tar.gz`:  
- **Perintah**:  
   ```bash
   tar -tzvf archive.tar.gz
   ```  
- **Penjelasan**:  
   - `t` → List isi arsip.  

---

### **Kesimpulan**  
Perintah **`tar`** digunakan untuk:  
- Menggabungkan banyak file/direktori menjadi satu arsip (tarball).  
- Mengkompresi arsip agar ukurannya lebih kecil.  

**Contoh Cepat**:  
- **Buat Arsip Terkompresi**:  
   ```bash
   tar -czvf backup.tar.gz /path/to/files
   ```  
- **Ekstrak Arsip Terkompresi**:  
   ```bash
   tar -xzvf backup.tar.gz
   ```
