# Pancaniti-PhysAI: Physics-Constrained Corrosion Simulation System v1.0

![Timeline](https://img.shields.io/badge/Timeline-April_2026-8A2BE2)
![Framework](https://img.shields.io/badge/Architecture-PINNs_%2F_Deep_Learning-blue)
![Tools](https://img.shields.io/badge/Hardware-Google_Colab_T4_GPU-orange)
![Status](https://img.shields.io/badge/Status-Completed-success)

**Pancaniti-PhysAI** adalah sebuah sistem AI prediktif untuk simulasi perambatan korosi (karat) non-linear guna mendukung strategi *predictive maintenance* pada komponen manufaktur dan mesin. Nama "PhysAI" merujuk pada arsitektur cerdas yang memaksa model kecerdasan buatan untuk 100% mematuhi hukum fisika absolut dan termodinamika *irreversibility*—menjamin bahwa karat bersifat menetap dan tidak dapat sembuh secara alami seiring berjalannya waktu.

> **Waktu Pengerjaan:** April 2026

---

## ✨ Fitur Utama Analisis & Pemodelan

1. **Arsitektur Patuh Fisika (100% Thermodynamic Compliance)** 🔬 <br> 
   Merancang *CNN Surrogate Model* berbasis *Residual Learning* dan aktivasi *Softplus* pada layer output untuk menjamin nilai pertumbuhan karat (Δ) selalu bernilai positif atau nol (Δ ≥ 0), mencegah anomali prediksi fisis.

2. **Fungsi Loss Spasial Kustom (Active Front Weighted Loss)** 🎯 <br> 
   Mengembangkan fungsi loss kustom dengan bobot penalti 26x lebih berat pada ujung perambatan karat (*active front*) agar AI secara presisi mendeteksi dinamika penyebaran karat secara spasial.

3. **Validasi Mandiri (15-Step Autoregressive Rollout)** 🔄 <br> 
   Menguji ketangguhan model melalui skenario *Autoregressive Rollout* hingga 15 langkah ke depan tanpa menggunakan data asli, membuktikan model mampu melakukan prediksi jangka panjang yang stabil dan konsisten.

4. **Pencegahan Kebocoran Data (Group-based Splitting)** 🔒 <br> 
   Menerapkan metode pemisahan data berbasis ID simulasi (*Group-based Splitting*) untuk memastikan evaluasi model sepenuhnya bersih dan bebas dari risiko *data leakage*.

5. **Akurasi Tinggi & Komputasi Efisien** ⚡ <br> 
   Mencapai tingkat akurasi hingga 96% pada simulasi 2D, dengan seluruh *pipeline* pelatihan dioptimalkan menggunakan akselerasi GPU T4.

---

## 📊 Hasil Visualisasi & Performa Model

### 1. Kurva Akurasi & Loss Pelatihan
Menunjukkan tingkat konvergensi model yang stabil dan optimalisasi *Active Front Weighted Loss* selama proses training menggunakan GPU T4.
![Metrik Akurasi dan Loss](Documentation/accuracy_loss_curves.png)

### 2. Perbandingan Simulasi Perambatan Karat (2D Simulation)
Visualisasi komparatif berdampingan (*side-by-side*) antara data asli (*Ground Truth*) dan hasil estimasi model *PhysAI* yang berhasil mempertahankan akurasi spasial sebesar 95.9%.
![Perbandingan Simulasi Real vs Prediksi](Documentation/simulation_comparison.png)

### 3. Evaluasi Prediksi Jangka Panjang (15-Step Autoregressive Rollout)
Pengujian mandiri tanpa pasokan data eksternal untuk melihat konsistensi hukum fisis (Δ ≥ 0) dan stabilitas akumulasi error sepanjang 15 langkah ke depan.
![Hasil Rollout Autoregressive](Documentation/autoregressive_rollout.gif)

---

## 🛠️ Alat & Metodologi

* **Arsitektur Utama:** Physics-Informed Neural Networks (PINNs), CNN Surrogate Model, Residual Learning.
* **Fungsi Loss Kustom:** Active Front Weighted Loss (Penalti Spasial 26x).
* **Lingkungan Komputasi:** Google Colab dengan Akselerasi Hardware GPU T4.

---

## 🔄 Alur Pemrosesan Data & Pelatihan (Data Pipeline)

```mermaid
graph TD
    A[(Data Simulasi 2D Korosi)] -->|Group-based Splitting via ID| B(Pipeline Bebas Leakage)
    B -->|Training Input| C[CNN Surrogate Model <br> Residual Learning + Softplus]
    C -->|Optimasi Spasial & Fisika| D{Active Front Weighted Loss <br> Penalti 26x + Hukum Δ ≥ 0}
    D -->|Akselerasi GPU T4| E[Model Matang / Terlatih]
    E -->|Evaluasi Jangka Panjang| F[Autoregressive Rollout 15 Langkah]
    F -->|Hasil Akhir| G[Akurasi 96% & Konsisten secara Fisis]

    style A fill:#20beff,stroke:#fff,stroke-width:2px,color:#fff
    style D fill:#ff8c00,stroke:#fff,stroke-width:2px,color:#fff
    style G fill:#2ecc71,stroke:#fff,stroke-width:2px,color:#fff
