# Pairwise Exchange Method - Kullanma Kilavuzu (Turkce)

Bu uygulama, yerlesim tasariminda "Pairwise Exchange" (ikili yer degistirme)
yontemini gorsel ve adim adim gosteren bir Tkinter arayuzudur.

## 1) Baslatma
- Gereksinim: Python 3 (standart kutuphane yeterli).
- Calistirma: `python pairwise_exchange_gui.py`

## 2) Temel Kavramlar
- Amac: Departmanlarin yerlesimini (layout) degistirerek toplam maliyeti (Cost)
  dusurmek.
- Cost: Akis matrisi (Flow) ve mesafe matrisi (Distance) kullanilarak hesaplanir.
- Swap: Iki departmanin yer degistirmesi.
- DC: Swap sonrasi maliyet degisimi (negatifse iyilesme).

## 3) Arayuz Bolumleri
- Sol panel: Problem ayarlari, rastgele uretim, algoritma kontrolu, kayit/cikti.
- Sag panel:
  - Layout Visualization: Yerlesim ve anlik Cost gorulur.
  - Flow Matrix: Akis matrisi duzenleme.
  - Distance Matrix: Mesafe matrisi duzenleme.
  - Layout Editor: Departman -> konum esleme.
  - Swap Candidates & Explanation: Aday takaslar ve aciklamalar.

## 4) Problem Ayarlari (Problem bolumu)
- n (3..12): Departman sayisi.
- Rows / Cols: Yerlesim izgara satir/sutun sayisi.
- Metric: Manhattan veya Euclidean mesafe.
- Force symmetric flows: Flow matrisini simetrik yapar.
- Use custom distance matrix: Kendi mesafe matrisini kullanir.
- Force symmetric distances: Distance matrisini simetrik yapar.
- Max iterations: Run to End icin maksimum adim sayisi.

## 5) Rastgele Problem Uretimi (Random Generator)
- Min/Max flow: Akis deger araligi.
- Sparsity (0..1):
  - Deger arttikca daha fazla hucre 0 olur, matris daha seyrek hale gelir.
  - Deger azaldikca daha fazla hucre dolu olur.
- Seed (opt):
  - Ayni seed girilirse ayni akis matrisi ve baslangic layout'u uretilir.
  - Bos birakilirsa her calistirmada farkli rastgele sonuc uretilir.
- Generate Random Problem: Yeni rastgele problem olusturur (layout da karisir).

## 6) Matris Duzenleme
- Flow Matrix (editable):
  - Hucreleri duzenleyin, "Apply Flow Edits" ile uygula.
  - Simetri aciksa [i,j] degisimi [j,i]'e aynalanir.
- Distance Matrix (editable):
  - Hucreleri duzenleyin, "Apply Distance Edits" ile uygula.
  - Negatif deger kabul edilmez.
  - Simetri aciksa karsi hucreye aynalanir.

## 7) Layout Duzenleme
- Layout Editor: Her departmani bir konuma (P0, P1, ...) atayin.
- "Apply Layout Edits" ile uygula.
- Konumlar benzersiz olmali (ayni konum iki departmana verilemez).

## 8) Algoritma Kontrolleri
- Run to End: Iyilestirme kalmayana veya Max iterations'a kadar otomatik calistirir.
- Next Step: En iyi DC'ye sahip tek swap uygular.
- Previous Step: Son adimi geri alir.
- Reset to Initial: Tum adimlari geri alip baslangica doner.
- Show swaps: "All" seciliyse tum aday swap'lar listelenir.
- Top-K: "All" kapaliysa sadece en iyi K swap listelenir.

## 9) Swap Adaylari ve Dogrulama
- Sagdaki listede tum aday swap'lar ve DC degerleri gorunur.
- "Validate DC for current best": En iyi swap icin DC hesabini tam
  maliyetle karsilastirir.

## 10) Disa Aktarma (Logging / Export)
- Export CSV: Adim gecmisini CSV olarak kaydeder.
- Export TXT: Ozet rapor (baslangic/final layout, cost, adimlar).

## 11) Tipik Calisma Akisi
1) n ve izgara ayarlarini yapin.
2) Flow/Distance verisini girin veya random uretin.
3) Layout'u kontrol edin (gerekirse duzenleyin).
4) Next Step ile adim adim ilerleyin veya Run to End kullanin.
5) Sonuclari CSV/TXT olarak disa aktarin.
