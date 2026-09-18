#  Analisis Penjualan & Breakeven Point Gerai Donat

##  Deskripsi
Proyek ini merupakan analisis data penjualan donat harian pada 5 gerai (Gerai A–E). Analisis difokuskan pada hubungan antara volume penjualan dan revenue, pemodelan tren menggunakan regresi, serta penentuan titik impas (Breakeven Point) masing-masing gerai berdasarkan struktur biaya (fixed cost & variable cost) dan harga jualnya. Data yang digunakan mencakup jumlah unit terjual, harga jual, biaya variabel, fixed cost harian, dan revenue harian dari kelima gerai.

##  Tujuan
1. Memvisualisasikan hubungan antara jumlah penjualan dan revenue untuk masing-masing gerai.
2. Menentukan bentuk tren/model matematis yang paling sesuai untuk menggambarkan hubungan revenue terhadap volume penjualan (linear, polynomial, atau eksponensial).
3. Menghitung volume penjualan minimum (Breakeven Point) yang dibutuhkan setiap gerai agar mencapai titik impas antara revenue dan total biaya.

##  Metode
Analisis dilakukan menggunakan Python (`pandas`, `numpy`, `matplotlib`, `scikit-learn`, `scipy`) dengan tahapan sebagai berikut:

1. **Eksplorasi & Visualisasi Data**
   Membuat scatter plot jumlah penjualan (unit) vs revenue (Rp) untuk masing-masing gerai guna melihat pola hubungan secara visual.

2. **Pemodelan Regresi**
   Menguji tiga bentuk model terhadap data revenue vs volume penjualan:
   - Regresi linear (`y = a·x + b`)
   - Regresi polynomial derajat 2
   - Regresi eksponensial (`y = a·e^(b·x)`, dilinearisasi melalui transformasi logaritma)

   Model terbaik dipilih berdasarkan nilai koefisien determinasi (R²) tertinggi.

3. **Perhitungan Breakeven Point (BEP)**
   BEP dihitung dengan mencari titik potong antara fungsi Revenue(x) hasil regresi dan fungsi Total Cost(x) = Fixed Cost + (Biaya Variabel per Unit × x), menggunakan metode numerik `scipy.optimize.brentq`. Hasil BEP kemudian divalidasi terhadap data aktual (perubahan tanda pada kolom Balance harian).

##  Hasil

### 1. Pola Revenue vs Penjualan
Kelima gerai menunjukkan hubungan yang sangat linear antara jumlah penjualan dan revenue — sesuai dugaan awal, karena harga jual per unit di setiap gerai bersifat konstan.

### 2. Model Regresi Terbaik
Model **linear** terpilih sebagai model terbaik di seluruh gerai dengan **R² = 1.0000**, mengonfirmasi bahwa revenue = harga jual × jumlah penjualan secara deterministik, tanpa penyimpangan (noise).

| Gerai | Persamaan Regresi | R² |
|---|---|---|
| A | Revenue = 25.000 × Penjualan | 1.0000 |
| B | Revenue = 8.000 × Penjualan | 1.0000 |
| C | Revenue = 11.000 × Penjualan | 1.0000 |
| D | Revenue = 20.000 × Penjualan | 1.0000 |
| E | Revenue = 15.000 × Penjualan | 1.0000 |

### 3. Breakeven Point per Gerai

| Gerai | Harga Jual (Rp) | Biaya Variabel/unit (Rp) | Fixed Cost Harian (Rp) | BEP (unit/hari) |
|---|---|---|---|---|
| A | 25.000 | 8.500 | 1.683.333 | ≈ 102 |
| B | 8.000 | 4.160 | 733.333 | ≈ 191 |
| C | 11.000 | 4.840 | 1.733.333 | ≈ 281 |
| D | 20.000 | 7.200 | 2.666.666 | ≈ 208 |
| E | 15.000 | 6.300 | 800.000 | ≈ 92 |

**Kesimpulan:** Gerai E memiliki BEP terendah (margin kontribusi per unit tinggi, fixed cost rendah), sedangkan Gerai C memiliki BEP tertinggi (margin kontribusi rendah, fixed cost besar). Validasi terhadap data aktual menunjukkan kesesuaian tinggi antara BEP hasil regresi dan pola untung/rugi historis masing-masing gerai.

##  Tools
`Python` · `pandas` · `numpy` · `matplotlib` · `scikit-learn` · `scipy`

