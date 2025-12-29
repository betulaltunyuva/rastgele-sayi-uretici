# Collatz Tabanlı Rastgele Sayı Üretimi

Bu çalışma, **Bilgi Sistemleri Güvenliği** dersi kapsamında,
**Collatz Varsayımı (3n + 1 problemi)** temel alınarak geliştirilmiş
basit bir **sözde rastgele sayı üretici** örneğini içermektedir.

Oluşturulan sistem deterministik yapıdadır.  
Yani aynı başlangıç değeri (**seed**) ile her çalıştırmada aynı çıktı dizisi elde edilir.
Bu nedenle gerçek kriptografik sistemler için uygun değildir ve
**yalnızca akademik / eğitsel amaçlıdır**.

---

## Matematiksel Arka Plan (Collatz Yaklaşımı)

Collatz Varsayımı’na göre herhangi bir pozitif tam sayı için aşağıdaki kurallar uygulanır:

- Sayı **çift** ise → `n = n / 2`
- Sayı **tek** ise → `n = 3n + 1`

Bu işlemler tekrarlandığında, sayıların sonunda **1** değerine ulaştığı gözlemlenir.

Örnek bir dizi (n = 7):

7 → 22 → 11 → 34 → 17 → 52 → 26 → 13 → 40 → 20 → 10 → 5 → 16 → 8 → 4 → 2 → 1

Bu dizinin düzensiz davranışı, rastgelelik benzeri bir yapı üretmek için kullanılmıştır.

---

## Kullanılan Yöntemin Açıklaması

Projede, kullanıcıdan alınan başlangıç değeri (seed) üzerinden Collatz adımları
ardışık olarak uygulanır.

Her adımda elde edilen sayı:
- `mod` işlemi ile belirli bir aralığa indirgenir
- Böylece sözde rastgele bir sayı üretilmiş olur

Bu işlem istenilen miktarda tekrar edilerek bir çıktı dizisi elde edilir.

---

## Algoritmanın Görsel Akışı

Algoritmanın çalışma mantığı aşağıdaki akış diyagramı ile gösterilmiştir:

![Akış Diyagramı](akis_diyagrami.png)

---

## Algoritmanın Sözde Kodu

Aşağıda, kullanılan yöntemin sadeleştirilmiş sözde kodu verilmiştir:

ALGORITHM Collatz_Based_PRNG

INPUT:
    seed  → başlangıç değeri (seed > 1)
    N     → üretilecek sayı miktarı
    mod   → çıktı sınırlandırma değeri

PROCESS:
    x ← seed

    FOR i ← 1 TO N DO
        IF x MOD 2 = 0 THEN
            x ← x / 2
        ELSE
            x ← 3 * x + 1
        END IF

        rastgele_sayi ← x MOD mod
        rastgele_sayi değerini listeye ekle
    END FOR

OUTPUT:
    sözde rastgele sayı dizisi

END

---

## Yöntemin Sınırlamaları

Bu çalışmada geliştirilen yöntem deterministik bir yapıdadır.
Aynı seed değeri kullanıldığında her çalıştırmada aynı çıktı üretilir.

Bu nedenle:
- Gerçek kriptografik güvenlik sağlamaz
- Sadece akademik ve kavramsal amaçlarla kullanılması uygundur

Amaç, Collatz dizisinin düzensiz yapısının
rastgelelik benzeri davranış üretmedeki potansiyelini göstermektir.

---

## Çalışmanın Amacı

Bu çalışmanın amacı,
Collatz Varsayımı’nın düzensiz sayı davranışını kullanarak
basit bir sözde rastgele sayı üretim mekanizmasının
nasıl tasarlanabileceğini göstermektir.

---

## NOT:
Bu çalışmada sunulan yöntem, matematiksel bir problem olan Collatz Varsayımı’nın
düzensiz ve öngörülemez davranışından faydalanılarak tasarlanmış
basit bir sözde rastgele sayı üretim yaklaşımıdır.

Elde edilen çıktılar istatistiksel olarak rastgelelik hissi verse de,
algoritma deterministik yapıdadır ve başlangıç değeri bilindiğinde
üretilen diziler tamamen tekrar edilebilir.

Bu nedenle geliştirilen yöntem;
- Kriptografik standartlarla karşılaştırılabilir değildir,
- Gerçek güvenlik uygulamaları için önerilmez,
- Eğitim, analiz ve algoritma tasarımı bakış açısıyla ele alınmalıdır.

Çalışmanın temel katkısı, matematiksel dizilerin
rastgelelik benzeri davranışlarının
bilgi güvenliği bağlamında nasıl yorumlanabileceğini göstermektir.


