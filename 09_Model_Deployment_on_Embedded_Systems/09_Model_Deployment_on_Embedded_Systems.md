---
marp: true
theme: gaia
_class: lead
paginate: true
backgroundColor: #fff
backgroundImage: url('../bg.png')

---
<style>
img[alt~="center"] {
  display: block;
  margin: 0 auto;
}
</style>

### Model Deployment on Embedded Systems
https://github.com/as-budi/Embedded_AI.git

---

#### 1. **Apa itu EloquentTinyML?**
- **EloquentTinyML** adalah library Arduino/C++ yang memungkinkan kita untuk menjalankan model machine learning berukuran kecil di **mikrokontroler** seperti **ESP32**, **ESP8266**, **Arduino Uno**, **Nano**, dll.
- Library ini membungkus **TensorFlow Lite for Microcontrollers (TFLite Micro)** dan membuat penggunaannya **jauh lebih simpel**.
- Tujuan utamanya: membuat proses deployment **ringan**, **cepat**, dan **tidak memerlukan TensorFlow kompleksitas penuh**.

---

#### 2. **Alur Umum Deployment ML ke ESP32**

- **Latih Model** di komputer/laptop (menggunakan TensorFlow/Keras/Sklearn)
- **Pruning & Kuantisasi** model jika diperlukan
- **Ekspor Model** menjadi array C-byte menggunakan **everywhereml**
- **Gunakan EloquentTinyML** untuk memuat model ke ESP32
- **Inferensi**: berikan input sensor/data, dapatkan output prediksi

---

#### ✨ A. Training Model
- Model dilatih di PC/laptop menggunakan Keras atau Tensorflow.
- Biasanya modelnya sederhana: **MLP (Multilayer Perceptron)**, **Decision Tree**, **SVM**, **Random Forest**, atau bahkan **small CNN**.
---
- Contoh model kecil:
  ```python
  import tensorflow as tf
  from tensorflow.keras.models import Sequential
  from tensorflow.keras.layers import Dense

  model = Sequential([
      Dense(8, activation='relu', input_shape=(3,)), 
      Dense(4, activation='relu'),
      Dense(1, activation='sigmoid')
  ])

  model.compile(optimizer='adam', loss='binary_crossentropy', metrics=['accuracy'])
  # Lanjutkan training...
  ```
---

#### ✨ B. Pruning & Kuantisasi (Opsional tapi Penting)
- Quantisasi membuat model lebih kecil, lebih cepat, dan kompatibel dengan memori terbatas.
- Tambahkan opsi quantization saat konversi:
  ```python
  converter.optimizations = [tf.lite.Optimize.DEFAULT]
  tflite_quant_model = converter.convert()
  ```
- Biasanya akan mengubah float32 → int8.
- **Lihat Materi sebelumnya tentang Pruning dan Kuantisasi**

---

#### ✨ C. Konversi ke TensorFlow Lite
- Setelah model selesai, dikonversi ke **TFLite**.
  ```python
  converter = tf.lite.TFLiteConverter.from_keras_model(model)
  tflite_model = converter.convert()

  with open('model.tflite', 'wb') as f:
      f.write(tflite_model)
  ```


---

#### ✨ D. Ubah menjadi C-array
- Model `.tflite` perlu diubah menjadi array C-byte agar bisa di-include ke dalam program Arduino.
- Menggunakan `xxd`:
  ```bash
  xxd -i model.tflite > model.h
  ```
- Hasilnya berupa file `model.h` yang berisi:
  ```c
  unsigned char model_tflite[] = {0x1c, 0x00, 0x00, ...};
  unsigned int model_tflite_len = 1234;
  ```

---

#### ✨ E. Deployment di ESP32 dengan EloquentTinyML
- Di Arduino IDE, include `EloquentTinyML.h`.
- Contoh basic code:
  ```cpp
  #include "model.h"  // file model.h hasil xxd
  #include <EloquentTinyML.h>

  // Sesuaikan ukuran input dan output
  #define INPUTS 3
  #define OUTPUTS 1
  #define TENSOR_ARENA_SIZE 2*1024  // Size RAM Arena (tweak sesuai model)

  Eloquent::TinyML::TinyML<INPUTS, OUTPUTS, TENSOR_ARENA_SIZE> ml;

  void setup() {
    Serial.begin(115200);
    ml.begin(model_tflite);
  }

  void loop() {
    float input[INPUTS] = {1.2, 3.4, 5.6};  // Data input sensor, misalnya
    float prediction = ml.predict(input);

    Serial.print("Prediksi: ");
    Serial.println(prediction);
    delay(1000);
  }
  ```

---
