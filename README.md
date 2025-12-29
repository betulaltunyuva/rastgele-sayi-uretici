# Rastgele Sayı Üreteci (Collatz Tabanlı)

Bu proje, **Collatz dizisi (Collatz teoremi)** kullanılarak geliştirilmiş
basit bir **sözde rastgele sayı üreteci (PRNG)** örneğidir.

Üreteç deterministiktir; yani aynı başlangıç değeri (**seed**) kullanıldığında
aynı çıktı dizisi elde edilir.  
Bu nedenle **kriptografik amaçlar için uygun değildir** ve yalnızca
eğitim / analiz amacıyla hazırlanmıştır.

---

## Kullanılan Yöntem – Collatz Dizisi

Collatz dizisi aşağıdaki kurala göre çalışır:

- Eğer sayı **çift** ise → `n = n / 2`
- Eğer sayı **tek** ise → `n = 3n + 1`

Bu projede:
- Collatz işlemleri tekrar edilerek sayı üretilir
- Her adımda elde edilen değer, `mod` işlemi ile
  belirli bir aralıkta sözde rastgele sayıya dönüştürülür

---

## Sözde Kod (Pseudocode)

**Girdi:**
- `seed` → başlangıç değeri  
- `N` → üretilecek sayı adedi  
- `mod` → sayıların üretileceği aralık  

**Çıktı:**
- `0` ile `mod - 1` arasında sözde rastgele sayılar

```text
Başla
x ← seed

i = 1’den N’e kadar tekrarla:
    Eğer x çift ise:
        x ← x / 2
    Değilse:
        x ← 3*x + 1

    rastgele_sayi ← x mod mod
    rastgele_sayi ekrana yazdır

Bitir

## AKIŞ ŞEMASI

BAŞLA
  |
Seed, N, mod al
  |
x = seed
  |
i = 1
  |
i ≤ N ?
 ├─ Hayır → BİTİR
 └─ Evet
        |
      x çift mi?
       ├─ Evet → x = x / 2
       └─ Hayır → x = 3x + 1
              |
        r = x mod mod
              |
          r yazdır
              |
          i = i + 1
              |
        geri → i ≤ N ?


```bash
python collatz_rng2.py
