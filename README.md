yerel-secim-sonuclari/
│
├── index.html
├── style.css
└── script.js
<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>2028 Yerel Seçim Sonuçları</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <header>
        <h1>2028 Yerel Seçim Sonuçları</h1>
    </header>

    <main>
        <div id="map-container">
            <img src="MapChart_Map.png" alt="2028 Türkiye Yerel Seçim Haritası" id="election-map">
            <div id="info-box">
                <!-- Şehir bilgileri burada gösterilecek -->
            </div>
        </div>
    </main>

    <footer>
        <p>&copy; 2024 - Kurgusal Seçim Sonuçları. Tüm Hakları Saklıdır.</p>
    </footer>

    <script src="script.js"></script>
</body>
</html>
body {
    font-family: Arial, sans-serif;
    background-color: #f4f4f4;
    margin: 0;
    padding: 0;
    text-align: center;
}

header {
    background-color: #4CAF50;
    color: white;
    padding: 10px 0;
}

main {
    padding: 20px;
}

#map-container {
    position: relative;
    display: inline-block;
}

#election-map {
    width: 100%;
    max-width: 800px;
    height: auto;
}

#info-box {
    position: absolute;
    background-color: rgba(255, 255, 255, 0.9);
    border: 1px solid #ccc;
    padding: 10px;
    display: none;
    max-width: 200px;
    z-index: 10;
    border-radius: 5px;
}

footer {
    background-color: #333;
    color: white;
    padding: 10px 0;
    position: fixed;
    bottom: 0;
    width: 100%;
}
document.addEventListener('DOMContentLoaded', function() {
    const map = document.getElementById('election-map');
    const infoBox = document.getElementById('info-box');

    const electionResults = {
        "Istanbul": {
            "winner": "Türkiye Partisi",
            "percentage": "55%",
            "logo": "url-to-turkiye-partisi-logo.png"
        },
        "Ankara": {
            "winner": "IŞIK Partisi",
            "percentage": "60%",
            "logo": "url-to-isik-partisi-logo.png"
        },
        // Diğer illeri ve sonuçlarını ekle
    };

    map.addEventListener('mousemove', function(event) {
        const x = event.clientX;
        const y = event.clientY;

        const city = getCityFromCoordinates(x, y);
        if (city && electionResults[city]) {
            const result = electionResults[city];
            infoBox.style.display = 'block';
            infoBox.style.left = x + 'px';
            infoBox.style.top = y + 'px';
            infoBox.innerHTML = `
                <strong>${city}</strong><br>
                Kazanan: ${result.winner}<br>
                Oy Oranı: ${result.percentage}<br>
                <img src="${result.logo}" alt="${result.winner} logosu" width="50">
            `;
        } else {
            infoBox.style.display = 'none';
        }
    });

    function getCityFromCoordinates(x, y) {
        // Haritadaki koordinatlara göre şehir belirleme
        // Burada bir şehir tespit fonksiyonu yazılmalı (örneğin, x ve y koordinatlarına göre şehir ismi döndürür)
        // Basit bir harita sisteminde her şehre sabit bir alan atayabilirsin
        // Örnek: if(x > A && x < B && y > C && y < D) return "Istanbul";
        return null;
    }
});
