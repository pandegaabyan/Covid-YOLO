# Deteksi Objek pada Citra X-Ray dari COVID-19 Menggunakan Model YOLOv4 dan YOLOv5

Deteksi objek merupakan bagian dari Computer Vision dengan tujuan menemukan dan mengklasifikasikan objek tertentu yang ada pada suatu citra. Di bidang medis, deteksi objek dapat diterapkan pada citra X-Ray dada sehingga dapat membantu mendeteksi dan melokalisasi penyakit pernafasan, salah satunya yaitu COVID-19. 

Pada proyek ini, kami menggunakan model YOLOv4 dan YOLOv5 untuk melakukan deteksi objek pada citra X-Ray dada terkait COVID-19. Berdasarkan pengujian, ukuran citra dan ukuran model tidak terlalu memberikan pengaruh sehingga kami menggunakan yang kecil agar lebih ringan. 

Hasilnya secara umum masih kurang baik dengan mAP yang masih berada di angka 0.2. Bagaimana pun juga, proyek ini memberikan berbagai pembelajaran baru terkait penggunaan YOLOv4 dan YOLOv5 pada citra X-Ray dada. Kami mendapati bahwa penggunaan pre-trained weight memang mampu membuat model belajar dengan lebih cepat, namun sangat rawan akan terjadinya over-fitting. Kami juga mendapati bahwa YOLOv4 mampu mengimbangi YOLOv5 dari segi hasil akhir, meski memang YOLOv5 mampu belajar lebih cepat dan lebih ringan.

---

### Dataset
Data yang digunakan berasal dari kaggle: [SIIM-FISABIO-RSNA COVID-19 Detection](https://www.kaggle.com/c/siim-covid19-detection/overview). Namun, data itu berbentuk file dicom, berukuran sangat besar, dan tidak dapat diakses dengan mudah. Untungnya, telah ada beberapa pihak yang membuat akses datanya menjadi lebih mudah. Saya akhirnya menggunakan data [SIIM COVID-19: Resized to 256px JPG](https://www.kaggle.com/xhlulu/siim-covid19-resized-to-256px-jpg) untuk citranya dan data [SIIM-COVID-19 Detection Training Labels](https://www.kaggle.com/ammarnassanalhajali/siimcovid19-detection-training-label) untuk label/anotasinya. 

### Kode
Pada kaggle, sebenarnya sudah ada banyak kode yang menggunakan dataset SIIM-FISABIO-RSNA COVID-19 karena memang itu adalah kompetisi berhadiah besar. Saya pun belajar banyak dengan melihat berbagai kode yang ada, terutama terkait konversi label agar sesuai format YOLO. Kode utama yang saya jadikan referensi adalah [COVID-19 Detection YOLOv5 3Classes](https://https://www.kaggle.com/ammarnassanalhajali/covid-19-detection-yolov5-3classes-training/notebook). Dari kode itu, saya menghilangkan beberapa hal yang tidak penting dan menambahkan hal baru, seperti penambahan untuk test data. Bahkan, ada juga kesalahan fatal pada kode aslinya, yaitu ketika membuat konversi label. 

### Model
Ada dua model yang digunakan, yaitu YOLOv4 dan YOLOv5. Untuk YOLOv5, saya menggunakan repo asli yang ada di Github, yaitu https://github.com/ultralytics/yolov5. Untuk YOLOv4, repo aslinya masih relatif sederhana dan tidak memiliki banyak fitur. Karenanya, saya menggunakan repo yang mirip dengan repo asli YOLOv5 dan dapat diimplementasikan langsung di PyTorch, yaitu https://github.com/WongKinYiu/PyTorch_YOLOv4/tree/u5. Keduanya cukup mirip dan format pelabelannya pun sama. Dengan begitu, harapannya keduanya bisa dibandingkan dengan lebih tepat. Namun, tidak bisa dipungkiri bahwa repo asli YOLOv5 jauh lebih advanced dari repo modifikasi YOLOv4. 

### Alur Pengujian
Pengujian diawali dengan pengolahan data, yaitu citra dan labelnya, agar bisa sesuai dengan format YOLO. Setelah itu, dijalankanlah training pada model. Ketika training, berbagai statistik akan tercatat secara otomatis. Setelah itu, terdapat evaluasi untuk melihat performa ketika training dan untuk menguji model menggunakan data test. Pada bagian akhir, terdapat pembandingan beberapa statistik dari beberapa pengujian yang telah dilakukan. 

### WandB
Untuk melihat hasil pengujian secara lebih lanjut, berikut link project dalam WandB:
https://wandb.ai/pandegaaz/siim-covid19-detect-1 (pengujian awal 1)
https://wandb.ai/pandegaaz/siim-covid19-detect-2 (pengujian awal 2)
https://wandb.ai/pandegaaz/siim-covid19-detect-3 (pengujian awal 3)
