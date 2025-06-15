# Praktikum-1
---
title: "Metode Regula Falsi"
author: "Ja'far Abdurrahman Shidiq"
---

# 📘 Pendahuluan

Metode *Regula Falsi* atau *False Position* adalah salah satu metode numerik untuk mencari akar dari suatu fungsi nonlinier. Metode ini mengandalkan dua titik awal `a` dan `b` yang mengapit akar (artinya: $f(a) \cdot f(b) < 0$) dan menggunakan pendekatan garis lurus untuk memperkirakan letak akar.

Metode ini biasanya konvergen lebih cepat dibandingkan metode bisection jika fungsi cukup linier di antara `a` dan `b`.

---

# 🧮 Fungsi yang Digunakan

Dalam laporan ini, fungsi yang digunakan adalah:

$$
f(x) = x^3 - 4x - 9
$$

Fungsi ini bersifat kontinu dan memiliki akar real dalam interval $[2, 3]$.

---

# 🔢 Implementasi Python

Kode berikut adalah implementasi metode Regula Falsi **tanpa import tambahan** (kecuali untuk visualisasi).

```python
# Definisi fungsi
def f(x):
    return x**3 - 4*x - 9

# Implementasi metode Regula Falsi
def regula_falsi(a, b, tol, max_iter):
    if f(a) * f(b) >= 0:
        print("f(a) dan f(b) harus memiliki tanda berbeda.")
        return None

    xs = []
    fs = []

    for i in range(max_iter):
        x = (a * f(b) - b * f(a)) / (f(b) - f(a))
        fx = f(x)
        xs.append(x)
        fs.append(fx)

        print(f"Iterasi {i+1}: x = {x:.6f}, f(x) = {fx:.6f}")

        if abs(fx) < tol:
            print("\nAkar ditemukan pada x =", x)
            return x

        if f(a) * fx < 0:
            b = x
        else:
            a = x

    print("\nAkar tidak ditemukan dalam iterasi maksimal.")
    return x
