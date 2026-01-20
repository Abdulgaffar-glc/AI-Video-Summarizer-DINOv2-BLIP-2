🎞️ AI Video Summarizer (DINOv2 + BLIP-2)

Bu proje, uzun videoları otomatik olarak analiz eden ve içeriği özetleyen gelişmiş bir yapay zeka aracıdır. Videodaki en önemli sahneleri (Keyframes) belirler ve her sahne için üretken yapay zeka kullanarak açıklamalar yazar.

Sistem, bulanık görüntüleri filtreler, sahneleri görsel benzerliklerine göre gruplar ve içeriği metne döker.
🌟 Özellikler

    Akıllı Kare Seçimi: Laplacian Variance yöntemiyle bulanık kareleri tespit eder ve işlemden çıkarır.

    Görsel Embedding (DINOv2): Meta AI'ın DINOv2 (ViT-L/14) modelini kullanarak karelerin yüksek çözünürlüklü vektör temsillerini çıkarır.

    Dinamik Özetleme: Videonun süresine göre çıkarılacak özet sayısını (Cluster sayısı) otomatik hesaplar (örn. uzun videolarda daha fazla özet).

    Sahne Açıklama (Captioning): Salesforce'un BLIP-2 (OPT-2.7b) modelini kullanarak seçilen sahneler için detaylı İngilizce açıklamalar üretir.

🛠️ Mimari Akış

    Örnekleme: Video taranır ve belirli aralıklarla kareler alınır.

    Kalite Kontrolü: Bulanık veya düşük kaliteli kareler elenir.

    Vektörleştirme: Geçerli kareler DINOv2 ile sayısal vektörlere dönüştürülür.

    Kümeleme (Clustering): K-Means algoritması ile benzer sahneler gruplanır ve her grubun "merkez" karesi seçilir.

    Captioning: Seçilen merkez kareler BLIP-2'ye gönderilir ve sahne açıklaması üretilir.

⚙️ Kurulum

Gerekli kütüphaneleri yüklemek için:
Bash

pip install torch torchvision opencv-python numpy scikit-learn transformers pillow accelerate

Not: Büyük modeller (DINOv2 Large ve BLIP-2) kullanıldığı için GPU (CUDA) kullanımı şiddetle tavsiye edilir.
🚀 Kullanım

    Videoyu Hazırlayın: Videonuzu proje klasörüne yükleyin (Kod içinde varsayılan: /content/video.mp4).

    Kodu Çalıştırın:

Python

python summarizer.py

    Çıktı: Konsolda, videonun önemli anlarının zaman damgası ve açıklaması görüntülenecektir.
