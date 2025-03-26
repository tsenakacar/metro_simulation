# 🚇 Metro Ağı Simülasyonu

Bu proje, Python ile geliştirilmiş bir metro ağı simülasyonudur. Metro istasyonları ve hatları üzerinde yolculuk yapılmasını, iki istasyon arasındaki **en hızlı** veya **en az aktarmalı** rotaların bulunmasını sağlar.

---

## ⚙️ Kullanılan Teknolojiler ve Kütüphaneler

- **Python 3**: Temel programlama dili.
- **`collections`**
  - `deque`: Genişlik öncelikli arama (BFS) için çift uçlu kuyruk.
  - `defaultdict`: Hatlara ait istasyonları kolayca gruplamak için.
- **`heapq`**: A* algoritmasında öncelik kuyruğu (min-heap) oluşturmak için.
- **`typing`**: Tip belirleme için (`Dict`, `List`, `Optional`, vb.)

---

## 🧠 Algoritmaların Çalışma Mantığı

### 🔄 BFS (Breadth-First Search) – En Az Aktarmalı Rota
- Kuyruk tabanlı bir arama algoritmasıdır.
- Her istasyon ziyaret edildiğinde, bağlı olduğu komşular sıraya alınır.
- Aynı istasyona aynı hatta tekrar gidilmez.
- Aktarma, komşu istasyon farklı hatta ise sayılır.
- **Avantajı**: En kısa adım sayılı (bu durumda en az aktarma) yol bulunur.

### 🚀 A* (Dijkstra mantığında) – En Hızlı Rota
- `heapq` ile öncelik kuyruğu kullanılır.
- Her adımda en düşük toplam süreli istasyon işlenir.
- İstasyon daha kısa sürede ziyaret edildiyse tekrar işlenmez.
- Coğrafi tahmin (heuristic) olmadığından klasik Dijkstra gibi çalışır.
- **Avantajı**: Süre bazlı en verimli yolu bulur.

### Neden Bu Algoritmalar?
- BFS: Adım sayısı önemli olduğunda (örneğin az aktarma).
- A*: Gerçek süreler önemli olduğunda (örneğin yolculuk süresi kısa olsun istendiğinde).

---

## ▶️ Örnek Kullanım ve Test Sonuçları

Program çalıştırıldığında aşağıdaki senaryolar test edilir:

1. **AŞTİ → OSB**
2. **Batıkent → Keçiören**
3. **Keçiören → AŞTİ**

Her senaryo için:
- En az aktarma sayısı içeren rota
- Toplam süreye göre en hızlı rota yazdırılır

### Örnek Çıktı:

```text
1. AŞTİ'den OSB'ye:
En az aktarmalı rota: AŞTİ -> Kızılay -> Ulus -> Demetevler -> OSB
En hızlı rota (19 dakika): AŞTİ -> Kızılay -> Kızılay -> Ulus -> Demetevler -> OSB
```

---

## 🚀 Projeyi Geliştirme Fikirleri

- GUI (grafiksel arayüz) ile görselleştirme
- Kullanıcıdan canlı başlangıç ve hedef istasyonu alma
- Harita entegrasyonu (örneğin coğrafi koordinatlarla heuristic A* kullanımı)
