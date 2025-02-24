<!-- ---
marp: true
theme: gaia
_class: lead
paginate: true
backgroundColor: #fff
backgroundImage: url('https://marp.app/assets/hero-background.svg')

--- -->

# Introduction to Embedded AI



---

## Overview of Embedded AI
- Embedded Artificial Intelligence (Embedded AI) mengacu pada integrasi algoritma kecerdasan buatan ke dalam perangkat keras dengan sumber daya terbatas, seperti mikrokontroler, sensor pintar, atau sistem tertanam lainnya.
- Embedded AI memungkinkan perangkat ini untuk melakukan analisis data secara on-board tanpa perlu bergantung pada komputasi berbasis cloud.

---

Karakteristik utama Embedded AI meliputi:
- **Efisiensi daya**: Dirancang untuk bekerja dengan konsumsi daya rendah.
- **Latensi rendah**: Pemrosesan dilakukan secara lokal tanpa harus mengirim data ke cloud.
- **Keandalan tinggi**: Dapat bekerja secara independen bahkan dalam kondisi jaringan terbatas.
- **Optimasi model AI**: Model AI dikompresi dan dioptimalkan untuk berjalan di perangkat dengan daya dan memori terbatas.

---
##### Differences between Embedded AI and Edge AI
| Aspek | Embedded AI | Edge AI |
|--------|-------------|---------|
| Lokasi Pemrosesan | Dalam perangkat dengan sumber daya terbatas (misal MCU, DSP) | Pada perangkat edge seperti gateway, edge server |
| Kinerja | Sangat dioptimalkan untuk perangkat kecil | Lebih kuat, menggunakan CPU/GPU atau TPU |
| Konsumsi Daya | Sangat rendah | Lebih tinggi dari Embedded AI, tetapi lebih rendah dari cloud |
---

| Aspek | Embedded AI | Edge AI |
|--------|-------------|---------|
| Contoh Perangkat | Sensor pintar, perangkat medis portabel | Edge gateway, edge server |

---

### 1. Healthcare
- **Wearable Devices**: AI tertanam dalam perangkat seperti smartwatch dan sensor kesehatan untuk mendeteksi detak jantung, kadar oksigen, atau ritme tidur secara real-time.
- **Portable Diagnostic Devices**: Digunakan dalam alat diagnosa mandiri yang dapat mendeteksi penyakit dari sinyal biometrik.
- **Smart Prosthetics**: Menggunakan Embedded AI untuk meningkatkan kontrol dan respons protesa berdasarkan input sensor otot.

---
### 2. Automotive
- **Advanced Driver Assistance Systems (ADAS)**: Sensor mobil yang dilengkapi AI untuk mendeteksi objek, membaca rambu lalu lintas, atau melakukan pengereman otomatis.
- **Predictive Maintenance**: Menganalisis data dari sensor kendaraan untuk memprediksi kerusakan dan mengurangi biaya perawatan.
- **In-Car Voice Assistants**: Menggunakan AI tertanam untuk mengenali perintah suara tanpa perlu koneksi ke cloud.
---

### 3. Internet of Things (IoT)
- **Smart Home Devices**: AI dalam perangkat seperti kamera keamanan, termostat pintar, dan asisten suara untuk meningkatkan efisiensi energi dan keamanan.
- **Industrial IoT (IIoT)**: Sensor yang memonitor peralatan industri dan menggunakan AI untuk deteksi dini kegagalan atau perawatan prediktif.
- **Precision Agriculture**: Sensor pertanian pintar yang menggunakan AI untuk menganalisis kelembaban tanah, cuaca, dan hama secara real-time.

---
##### Constraints and Challenges in Embedded AI

- **Keterbatasan Sumber Daya:** Perangkat tertanam memiliki keterbatasan dalam daya komputasi, memori, dan penyimpanan yang membatasi kompleksitas model AI.
- **Efisiensi Energi:** Model AI harus dioptimalkan agar dapat berjalan dengan konsumsi daya yang sangat rendah, terutama untuk perangkat yang menggunakan baterai.
- **Kompresi Model:** Teknik seperti kuantisasi dan pruning diperlukan untuk mengurangi ukuran model tanpa mengorbankan akurasi secara signifikan.

---

- **Keamanan dan Privasi:** Karena data diproses secara lokal, perangkat harus memiliki mekanisme keamanan yang kuat untuk mencegah kebocoran atau serangan siber.
- **Konektivitas Terbatas:** Banyak perangkat embedded beroperasi di lingkungan dengan jaringan yang tidak stabil atau tanpa koneksi internet.
- **Kompleksitas Pengembangan:** Dibutuhkan keahlian khusus dalam optimalisasi perangkat keras dan perangkat lunak untuk memastikan performa maksimal dari Embedded AI.
- **Kendala Biaya:** Biaya pengembangan dan produksi chip khusus AI bisa menjadi tantangan bagi adopsi teknologi ini secara luas.
---

#### Aspek penting dalam *Embedded AI*:  

##### 1. **Hardware dan Software untuk Embedded AI**  
   - **Jenis Perangkat Keras**: MCU (Microcontroller Unit), MPU (Microprocessor Unit), DSP (Digital Signal Processor), FPGA (Field-Programmable Gate Array), dan ASIC (Application-Specific Integrated Circuit).  
   - **Framework dan SDK**: TensorFlow Lite, ONNX Runtime, Arm Cortex-M, NVIDIA Jetson, Edge Impulse, ESP32, dsb.  
---

##### 2. **Teknik Optimasi Model AI untuk Embedded Systems**  
   - **Quantization**: Mengubah model floating-point menjadi format yang lebih ringan (int8, fixed-point) untuk mengurangi kebutuhan memori dan meningkatkan efisiensi.  
   - **Pruning & Sparsity**: Menghilangkan bobot yang tidak signifikan dari model neural network untuk mempercepat inferensi.  
   - **Knowledge Distillation**: Menggunakan model AI yang lebih besar untuk melatih model yang lebih kecil tanpa kehilangan akurasi signifikan.  
---

##### 3. **Real-Time Processing & Deterministic AI**  
   - Mengapa real-time processing penting dalam sistem tertanam?  
   - Teknik yang digunakan untuk memastikan inferensi berlangsung dalam waktu yang dapat diprediksi.  
---

##### 4. **Benchmarking dan Evaluasi Performa**  
   - **Metode Pengukuran Performa**: Latensi inferensi, konsumsi daya, throughput, akurasi model.  
   - **Dataset dan Uji Coba**: Dataset standar seperti ImageNet untuk visi komputer atau Speech Commands untuk pemrosesan suara.  
---

##### 5. **Regulasi dan Standarisasi dalam Embedded AI**  
   - Peraturan terkait keamanan data dan privasi (misalnya GDPR untuk perangkat IoT yang memproses data pengguna).  
   - Standarisasi industri terkait AI di perangkat tertanam. 
---

#### Diskusi Kelompok
1. Bayangkan Anda seorang insinyur AI yang mengembangkan embedded system untuk mendeteksi kesehatan jantung. Tantangan teknis apa yang mungkin Anda hadapi?
2. Dalam industri otomotif, bagaimana Embedded AI dapat meningkatkan keamanan dan efisiensi kendaraan? Berikan contoh nyata.
---
3. Dalam skenario Industrial IoT (IIoT), bagaimana Embedded AI dapat digunakan untuk predictive maintenance?
4. Jika Anda ingin mengembangkan sistem AI pada sensor pintar dengan keterbatasan daya dan memori, teknologi atau teknik apa yang akan Anda gunakan?
