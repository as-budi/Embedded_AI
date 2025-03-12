<!-- ---
marp: true
theme: gaia
_class: lead
paginate: true
backgroundColor: #fff
backgroundImage: url('https://marp.app/assets/hero-background.svg')

--- -->

# AI Hardware for Embedded Systems



---
#### **1. Overview of Hardware Platforms**  
- Embedded AI hardware terdiri dari berbagai platform yang mendukung komputasi kecerdasan buatan dengan keterbatasan daya dan sumber daya. Beberapa platform utama meliputi:  
---
- **Microcontrollers (MCUs)**:  
  - Contoh: STM32, ESP32, Arduino (ARM Cortex-M series)  
  - Memiliki daya komputasi rendah tetapi efisien untuk aplikasi AI ringan seperti klasifikasi sederhana dan pengenalan pola.  
  - Biasanya mendukung TinyML dan model AI yang telah dioptimalkan dengan framework seperti TensorFlow Lite for Microcontrollers.  
---
- **Graphics Processing Units (GPUs)**:  
  - Contoh: NVIDIA Jetson Nano, Raspberry Pi 5 dengan VideoCore GPU  
  - Dapat menangani komputasi paralel yang lebih kompleks, cocok untuk deep learning dan computer vision.  
  - Digunakan dalam aplikasi yang membutuhkan inferensi real-time seperti deteksi objek dan segmentasi gambar.  
---
- **Tensor Processing Units (TPUs)**:  
  - Contoh: Google Edge TPU (Coral Dev Board), NVIDIA Jetson Xavier  
  - Dirancang khusus untuk akselerasi AI dengan konsumsi daya rendah.  
  - Dapat menjalankan model deep learning lebih efisien dibandingkan CPU atau GPU dengan latensi rendah.  

---
#### **2. AI Computation Constraints**  
- **Memory Limitations**:  
  - Mikrocontroller sering kali memiliki RAM terbatas (<1MB), sehingga memerlukan model yang sangat ringan.  
  - Teknik seperti quantization (mengubah model dari 32-bit float ke 8-bit integer) digunakan untuk mengurangi kebutuhan memori.  
---
- **Power Constraints**:  
  - AI untuk perangkat IoT dan wearable harus hemat daya karena sering berjalan pada baterai.  
  - Edge TPU dan AI-dedicated chips seperti Coral TPU dirancang untuk efisiensi daya dibandingkan GPU.  
---
- **Processing Power**:  
  - Embedded AI harus menyeimbangkan akurasi dengan kecepatan inferensi karena keterbatasan daya komputasi.  
  - Optimalisasi model dengan pruning dan distillation digunakan untuk meningkatkan performa pada hardware terbatas.  
---
#### **3. Example: AI on Arduino, Raspberry Pi, and ESP32**  

- **AI on Arduino (TinyML)**:  
  - Bisa menggunakan **Arduino Nano 33 BLE Sense** dengan TensorFlow Lite.  
  - Contoh: Deteksi suara sederhana (keyword spotting), klasifikasi gerakan dengan sensor IMU.  
---
- **AI on Raspberry Pi**:  
  - Bisa menjalankan model deep learning dengan OpenCV dan TensorFlow Lite.  
  - Contoh: Deteksi wajah dengan Raspberry Pi Camera + OpenCV, pengenalan objek dengan MobileNet.  
---
- **AI on ESP32**:  
  - ESP32 dapat menjalankan inferensi AI ringan dengan **TensorFlow Lite for Microcontrollers**.  
  - Contoh: Deteksi anomali pada sensor (IoT predictive maintenance), pengenalan suara sederhana.  
