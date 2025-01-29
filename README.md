<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ethereum Canlı Fiyat</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            padding: 20px;
        }
        h1 {
            color: #333;
        }
        #eth-price {
            font-size: 24px;
            font-weight: bold;
            color: #008000;
        }
    </style>
</head>
<body>
    <h1>Ethereum Fiyatı:</h1>
    <p id="eth-price">Yükleniyor...</p>

    <script>
        async function fetchEthPrice() {
            try {
                const response = await fetch('https://api.coingecko.com/api/v3/simple/price?ids=ethereum&vs_currencies=usd');
                const data = await response.json();
                document.getElementById('eth-price').textContent = data.ethereum.usd + " USD";
            } catch (error) {
                console.error("Fiyat alınamadı:", error);
                document.getElementById('eth-price').textContent = "Veri alınamadı!";
            }
        }

        // İlk yükleme
        fetchEthPrice();

        // Her 5 saniyede bir güncelle
        setInterval(fetchEthPrice, 5000);
    </script>
</body>
</html>

