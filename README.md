# Fashion-MNIST Üzerinde CNN ile Kıyafet Sınıflandırma

Fashion-MNIST veri seti üzerinde sıfırdan eğitilmiş bir CNN modeli ve bu modeli, kullanıcının yüklediği kıyafet fotoğraflarını sınıflandıran bir Gradio web uygulaması.

## Repodaki Dosyalar

| Dosya / Klasör | Açıklama |
|---|---|
| `Ödev_2_Model.ipynb` | Modelin eğitildiği ve test edildiği notebook. Eğitim/test sonuçları, grafikler ve metrikler bu notebook'un çıktılarında görüntülenebilir. |
| `Ödev_2_Gradio_Uygulamasi.ipynb` | Gradio uygulaması. Eğitilmiş modelin ağırlıkları notebook'un içine gömülüdür. |
| `pictures/` | Öğrenci tarafından telefonla çekilmiş 5 adet kıyafet fotoğrafı. |
| `pictures_results/` | Bu 5 fotoğrafın uygulamadaki tahmin sonuçlarının ekran görüntüleri. |

## Uygulamayı Çalıştırma

Uygulamayı çalıştırmak için **yalnızca** `Ödev_2_Gradio_Uygulamasi.ipynb` yeterlidir. Model ağırlıkları (`fashion_cnn_best.pth`) notebook'un içine base64 olarak gömülü olduğundan ayrıca bir model dosyası indirmeye gerek yoktur.

1. `Ödev_2_Gradio_Uygulamasi.ipynb` dosyasını Google Colab'da açın.
2. Hücreleri **yukarıdan aşağıya sırayla** çalıştırın.
   - "Gömülü Model Ağırlıkları" hücresi uzundur, içeriğine dokunmadan sadece çalıştırın. Çalıştırdıktan sonra başlığın yanındaki okla katlayabilirsiniz.
   - Bu hücre eksiksiz çalıştırılmazsa sonraki hücrede SHA-256 doğrulaması hata verir.
3. Son hücre bir Gradio linki üretir. Linke tıklayarak arayüzü açın, bir kıyafet fotoğrafı yükleyin ve tahmini görün.

**Notlar:**
- Üretilen link geçicidir (yaklaşık 1 hafta) ve yalnızca son hücre çalıştığı sürece aktiftir. Uygulamayı kapatmak için hücreyi durdurmanız yeterlidir.
- Arayüzdeki **Arka plan** seçeneği çoğu zaman "Otomatik" kalabilir. Önizlemede ("Modelin gördüğü görüntü") nesne koyu, zemin açık görünüyorsa elle **"Açık arka plan (ters çevir)"** seçeneğini kullanın.

Uygulama şu 10 sınıfı tanır: tişört, pantolon, kazak, elbise, mont, sandalet, gömlek, spor ayakkabı, çanta, bilekli bot.


## Eğitim Süresini İnceleme

- `Ödev_2_Model.ipynb` dosyasını açarak eğitim süresini inceleyebilirsiniz.


## Modeli Yeniden Eğitme (İsteğe Bağlı)

Uygulamayı çalıştırmak için gerekli değildir. Yeniden çalıştırmak isterseniz:

1. `Ödev_2_Model.ipynb` dosyasını Google Colab'da açın (GPU önerilir: *Çalışma zamanı > Çalışma zamanı türünü değiştir > GPU*).
2. Hücreleri sırayla çalıştırın. Fashion-MNIST veri seti otomatik olarak indirilir.
3. Notebook sonunda `fashion_cnn_best.pth` (en iyi model ağırlıkları) ve `results.json` (özet sonuçlar) dosyaları üretilir.

Not: Eğitim ve test sonuçlarını (loss/accuracy eğrileri, sınıf bazında metrikler, confusion matrix, tahmin süresi) çalıştırmadan da notebook'taki kayıtlı çıktılardan görebilirsiniz.

## Gereksinimler

Colab'da gerekli kütüphanelerin çoğu hazır gelir. Gradio notebook'unun ilk hücresi `gradio` kurulumunu kendisi yapar. Yerelde çalıştırmak isterseniz:

```bash
pip install torch gradio pillow numpy                # Gradio uygulaması
pip install torchvision scikit-learn matplotlib      # Model notebook'u için ek olarak
```

## Veri Seti

Fashion-MNIST (Zalando Research): https://github.com/zalandoresearch/fashion-mnist
