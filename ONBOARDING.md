# 🚀 CircuitSolver: Geliştirici Başlangıç Kılavuzu (Onboarding Guide)
**Hazırlayan:** Onur (Future Self için Notlar)
**Tarih:** 31.01.2026

Bu belge, projeye aylar sonra geri döndüğünde "Ben burada ne yapıyordum?", "Conda neydi?", "Bunu nasıl çalıştıracağım?" sorularını cevaplamak için hazırlanmıştır.

---

## 🧠 Kavramlar Sözlüğü (Nedir Bunlar?)

### 1. VS Code Yeterli mi?
**EVET.** Başka hiçbir devasa programa (CLion, PyCharm vs.) ihtiyacın yok. VS Code hem Python'u hem C'yi yöneten ana kumanda merkezimizdir.

### 2. Conda / Miniconda Nedir? (Python İçin)
Python projeleri birbirini bozmayı sever. Biri NumPy 1.0 ister, diğeri 2.0 ister.
* **Conda:** Bu projeyi "karantinaya alan" bir koruma kalkanıdır.
* **Environment (Ortam):** Projeye özel sanal bir odadır. Bu projede kurduğun kütüphaneler (NumPy vb.) sadece bu odayı etkiler, bilgisayarının geri kalanına bulaşmaz.

### 3. GCC ve Make (C İçin)
* **GCC:** Yazdığın C kodunu M1 işlemcinin anlayacağı dile çeviren çevirmen (Compiler).
* **Make:** İleride proje büyüdüğünde "tek tuşla derlemek" için kullanacağımız otomasyon aracı.

---

## 🛠️ Kurulum Adımları (Sırasıyla Yap)

### Adım 1: Python Ortamını Kur (Sadece Bir Kere)
Bu projede matris işlemleri için `numpy` kütüphanesi lazım. Bunu bilgisayarın ana Python'una kurma!

1.  Terminali aç (Mac veya VS Code Terminal).
2.  Eğer yüklü değilse **Miniconda** yükle (İnternetten indir).
3.  Şu komutla bu projeye özel bir oda (environment) oluştur:
    ```bash
    conda create --name circuitsolver python=3.10
    ```
4.  Odaya giriş yap:
    ```bash
    conda activate circuitsolver
    ```
    *(Terminalin başında `(circuitsolver)` yazdığını görmelisin).*
5.  Gerekli kütüphaneyi kur:
    ```bash
    conda install numpy
    ```

### Adım 2: VS Code Ayarı
VS Code'a "Ben bu projede az önce kurduğum Conda ortamını kullanmak istiyorum" demelisin.
1.  Herhangi bir `.py` dosyasını aç.
2.  Sağ alttaki Python sürümüne tıkla (veya `Cmd + Shift + P` -> `Python: Select Interpreter`).
3.  Listeden **`circuitsolver (conda)`** olanı seç.

### Adım 3: C Ortamı (Mac için Hazır mı?)
MacBook'ta genelde hazırdır ama kontrol et. Terminale şunu yaz:
```bash
gcc --version
```
Eğer hata verirse veya "yüklü değil" derse:
```bash
    xcode-select --install
```
yaz ve açılan pencerede "Yükle" de.

## 🏃‍♂️ Projeyi Çalıştırma (Workflow)

### Senaryo A: Python Prototipi Üzerinde Çalışıyorsun
Amacın mantığı kurmak ve hızlı deneme yapmak.
1.  VS Code'u aç.
2.  `python-prototype/` klasörüne git.
3.  Terminalde `conda activate circuitsolver` komutunun aktif olduğundan emin ol.
4.  Kodu çalıştır:
```bash
python main.py
```

### Senaryo B: C Motoru (Engine) Üzerinde Çalışıyorsun
Amacın yüksek performans ve manuel bellek yönetimidir (Manual Memory Management).

1.  `c-engine/` klasörüne git.
2.  **Kompilierung** (Derleme) işlemi için:
```bash
gcc main.c -o devre_cozucu
```
3.  **Ausführung** (Çalıştırma) işlemi için:
```bash
./devre_cozucu
```

---

## ✅ Geri Dönüş Checklist'i (Aylar Sonra Buradasın)

Projeyi açtığında sırasıyla şunları kontrol et:

- [ ] **Git Pull:** `git pull` yaparak GitHub'daki en son yedeği çektin mi?
- [ ] **Conda Aktif mi?:** Terminalde `(circuitsolver)` ibaresini görüyor musun?
- [ ] **Interpreter Seçili mi?:** VS Code sağ altta doğru Python ortamını (Conda) görüyor mu?
- [ ] **Temizlik:** Önceki derlemelerden kalan `.o` veya `a.out` dosyalarını sildin mi?
- [ ] **Hedef:** Bugün **Logik** (Python) tarafında mı yoksa **Performance** (C) tarafında mı ter dökeceksin?

---
*Unutma: Çalışmayan bir kod, sadece diskte yer kaplayan bir gürültüdür.*