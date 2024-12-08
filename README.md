# Cara mengupdate lokal dengan branch yang ditambahkan oleh collaborator

### 1. Periksa daftar branch lokal dan remote:
   Cek terlebih dahulu daftar branch yang ada di repository lokal dan remote Anda dengan menggunakan perintah:
   ```bash
   git branch         # Menampilkan branch lokal
   git branch -r      # Menampilkan branch remote
   ```

   Jika Anda tidak melihat `origin/presensi` dalam daftar branch remote, berarti branch tersebut belum diambil (fetched) ke lokal Anda.

### 2. Fetch perubahan dari remote:
   Untuk mengambil semua perubahan terbaru dari remote, termasuk branch yang baru ditambahkan, jalankan perintah:
   ```bash
   git fetch origin
   ```

   Ini akan memperbarui referensi untuk semua branch remote yang ada di remote repository tanpa mengubah status branch lokal Anda.

### 3. Checkout branch `presensi`:
   Setelah melakukan `fetch`, Anda bisa membuat branch lokal untuk contoh: `presensi` dan langsung beralih ke branch tersebut dengan perintah:
   ```bash
   git checkout -b <nama-branch> origin/<nama-branch>
   ```
  contoh:
   ```bash
   git checkout -b presensi origin/presensi
   ```

   Perintah ini akan membuat branch lokal baru dengan nama `presensi` yang mengikuti branch remote `origin/presensi` dan langsung beralih ke branch tersebut.

### 4. Verifikasi bahwa branch `presensi` sudah ada secara lokal:
   Cek kembali daftar branch lokal dengan perintah:
   ```bash
   git branch
   ```

   Jika berhasil, branch `presensi` sekarang akan muncul dalam daftar branch lokal Anda.

### 5. Melakukan Merge ke branch `main`:
   Setelah berhasil checkout ke branch `presensi`, Anda bisa melakukan merge ke branch `main` dengan langkah-langkah yang ada di bawah.

---

### Summary:
1. Periksa branch lokal dan remote:
   ```bash
   git branch         # Lokal
   git branch -r      # Remote
   ```

2. Fetch perubahan terbaru:
   ```bash
   git fetch origin
   ```

3. Checkout branch `presensi`:
   ```bash
   git checkout -b presensi origin/presensi
   ```



# Langkah-langkah untuk melakukan merge:

### 1. Pastikan Anda berada di branch `main`:
   Sebelum melakukan merge, pastikan Anda berada di branch `main`. Untuk beralih ke branch `main`, gunakan perintah:
   ```bash
   git checkout main
   ```

### 2. Tarik perubahan terbaru dari remote repository (opsional, tetapi disarankan):
   Untuk memastikan bahwa branch `main` Anda terkini, lakukan `git pull` untuk menarik perubahan terbaru dari remote repository:
   ```bash
   git pull origin main
   ```

### 3. Merge branch `presensi` ke `main`:
   Setelah berada di branch `main`, Anda bisa menggabungkan (merge) perubahan dari branch `presensi` milik teman Anda. Gunakan perintah berikut untuk melakukan merge:
   ```bash
   git merge origin/<nama-branch>
   ```
   contoh:
   ```bash
   git merge origin/presensi
   ```

   Perintah ini akan menggabungkan perubahan yang ada di branch `presensi` ke dalam branch `main`.

### 4. Menangani Konflik (Jika Ada):
   Jika ada konflik antara kode di branch `main` dan branch `presensi`, Git akan memberi tahu Anda dan meminta Anda untuk menyelesaikan konflik tersebut. Anda perlu membuka file yang mengalami konflik, memperbaiki masalah tersebut, dan kemudian melakukan commit perubahan.

   Setelah menyelesaikan konflik, lakukan commit untuk menyelesaikan merge:
   ```bash
   git add .
   git commit -m"<pesan-deskripsi-singkat>"
   ```
   contoh:
   ```bash
   git add .
   git commit -m "Menggabungkan branch presensi ke main"
   ```

### 5. Push perubahan ke remote repository:
   Setelah berhasil melakukan merge, jangan lupa untuk mengirimkan (push) perubahan ke remote repository agar perubahan tersebut dapat terlihat oleh orang lain. Gunakan perintah:
   ```bash
   git push origin main
   ```

### Summary:
1. `git checkout main` – Beralih ke branch `main`.
2. `git pull origin main` – Tarik perubahan terbaru dari branch `main` di remote.
3. `git merge origin/presensi` – Gabungkan branch `presensi` ke dalam branch `main`.
4. `git push origin main` – Push perubahan yang telah digabungkan ke remote repository.
