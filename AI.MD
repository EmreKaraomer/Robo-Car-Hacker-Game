# Yapay Zeka (AI) Kullanım Günlüğü

Bu proje geliştirilirken, bazı temel mekaniklerin optimizasyonu ve algoritma mantıklarının kurulması aşamasında yapay zeka (Google Gemini) araçlarından mentorluk alınmıştır. Projenin tamamı yapay zekaya yazdırılmamış olup, aşağıda belirtilen promptlar ile sadece belirli fonksiyonların nasıl yazılabileceği hakkında fikir alışverişi yapılmıştır.

Aşağıda, oyunun temel modüllerinin geliştirilmesi sırasında yapay zeka ile yapılan konuşmaların bir özeti bulunmaktadır:

---

### Soru 1: Harita Dizisi (Array) Oluşturma

**Öğrenci (Prompt):**
> "Oyunuma harita oluşturabilir misin

**Yapay Zeka (Cevap):**
> "Tabii ki. Oyununuz için belirttiğiniz 30x20 boyutlarında, odaların etrafının duvarlarla (0) mühürlendiği ve girişlerinin sadece kilitli kapılar (7) ile sağlandığı harita matrisi aşağıdadır. Bu diziyi Canvas üzerinde çift `for` döngüsü ile `fillRect` kullanarak çizebilirsiniz:

```javascript
const KARE = 40; // 30x40 = 1200px genişlik, 20x40 = 800px yükseklik
const harita = [
    // ... (30x20 boyutlarındaki harita matrisi)
];

Soru 2: Basit Yapay Zeka Destekli Gardiyan Sistemi
Öğrenci (Prompt):

"Oyun için yapay zeka destekli bir gardiyan sistemi geliştirebilir miyiz? Belli bir grid aralığında rastgele devriye gezsinler. Eğer oyuncuya çok yaklaşırlarsa onu yakalasınlar."

Yapay Zeka (Cevap):

"Bunun için karmaşık bir A* pathfinding algoritması yazmak yerine, belirli bir X veya Y ekseninde maksimum ve minimum sınırları olan basit bir vektörel devriye mantığı kurabilirsiniz. Oyuncuyu yakalaması için de iki nokta arasındaki mesafeyi ölçen Pisagor teoremini (Math.hypot) kullanabiliriz.
// Devriye Mantığı
gardiyanlar.forEach(g => {
    if (g.eksen === 'x') {
        g.x += g.hiz * g.yon;
        if (g.x > g.max || g.x < g.min) g.yon *= -1; // Sınıra çarpınca geri dön
    }
    
    // Yakalanma Kontrolü (Mesafe 20 pikselin altına düşerse)
    let mesafe = Math.hypot((araba.x + 10) - (g.x + 10), (araba.y + 10) - (g.y + 10));
    if (mesafe < 20) {
        // Yakalanma fonksiyonlarını tetikle ve başa dön
    }
});

Soru 3: Müzik ve Ses Entegrasyonu (Web Audio API)
Öğrenci (Prompt):

"Oyun temasına uygun bir müzik ekleyebilir misin? Fakat ben MP3 bulmakla veya dosya indirmekle uğraşmayayım.

Size Cyberpunk ve gizlilik hissiyatı verecek, kalın bas notaları (sawtooth) içeren ve duvar arkasından geliyormuş gibi boğuk duyulmasını sağlayan bir filtre (lowpass) ile 'Sentetik Arka Plan Müziği' fonksiyonu hazırladım:

const AudioContext = window.AudioContext || window.webkitAudioContext;
const sesMotoru = new AudioContext();
let bgmDongu = null;
let bgmAdim = 0;
const bgmNotalar = [110.00, 110.00, 130.81, 110.00, 98.00, 98.00, 103.83, 110.00]; 

function arkaPlanMuzigiBaslat() {
    bgmDongu = setInterval(() => {
        // ... Oscillator, BiquadFilter ve Gain Node ayarları
        osc.start();
        osc.stop(sesMotoru.currentTime + 0.3);
        bgmAdim++;
    }, 400); 
}Soru 4: Ana Menü, Zorluk Seviyeleri ve Sekmeler

Öğrenci (Prompt):

"Oyunum için ana menü tasarlar mısın? Kurallar, zorluk seviyeleri ve tuş kontrolleri sekmeleri bulunsun. İçeriklerini oyuna uygun şekilde otomatik olarak doldurabilirsin."

Yapay Zeka (Cevap):

"Oyununuzun giriş ekranı için Canvas'ın üzerine binecek şık bir HTML/CSS overlay menüsü tasarlayabiliriz. Düğmelere basıldığında JavaScript ile bölümlerin display özelliklerini değiştirerek sekme mantığı kurdum.

Ayrıca 3 farklı zorluk seviyesi için (Kolay, Normal, Zor) gardiyanların devriye atacağı grid mesafelerini (min/max limitlerini), hareket hızlarını ve hata yapıldığında kesilecek ceza oranlarını değiştiren dinamik bir oyunuBaslat(zorluk) fonksiyonu ekledim.

Kurallar sekmesine kilit kırma, yemekhane araması, alarm sabotajı ve kazı hedeflerini; Tuş Kontrolleri sekmesine ise WASD, R, E ve Space tuşlarının görevlerini otomatik olarak ekledim."

Soru 5: Proje Belgelerinin (README) Hazırlanması
Öğrenci (Prompt):

"(Proje Dosyası Yüklendi) bu dosyadaki şartlara uygun bir README dosyası yazar mısın?"

Yapay Zeka (Cevap):

"Elbette. İstenilen puanlama kriterlerini (Canlı URL, Ekran görüntüleri, İlham alınan Itch.io oyununun referansı, tuş kontrolleri, asset bildirimleri ve grup üyeleri listesi) kapsayan profesyonel bir Markdown (README.md) şablonu hazırladım. Şablondaki köşeli parantezli yerleri kendi öğrenci numaralarınız ve linklerinizle doldurmanız yeterli olacaktır. Projenin tek bir HTML dosyasında çalışması ve dış kütüphane kullanılmaması gibi kurallara %100 uyulduğunu da belgede vurguladım."