# Hassas Volatilite - TradingView İndikatörü

## Açıklama
Bu TradingView indikatörü, fiyatın, hareketli ortalamanın (MA) ve ATR'nin kareleri arasındaki oranı hesaplar. Bu oran, piyasanın volatilitesi ve fiyat hareketliliği hakkında bilgi sağlar.

## Özellikler
- **Matematiksel Formül:** (Fiyat^2 - MA^2) / ATR^2
- Kullanıcılar, ATR ve MA periyotlarını özelleştirebilir.
- Piyasadaki volatiliteyi anlamak için gelişmiş bir analiz aracı.

## Nasıl Kullanılır?
1. TradingView'de indikatörü ekleyin.
2. ATR ve MA periyotlarını girin.
3. Piyasadaki volatilite ve fiyat hareketliliğini analiz edin.

## Teknolojiler
- **Pine Script v6**
- **TradingView Platformu**

## Kod
```pine
<//@version=6
indicator("Fiyat^2 - MA^2 / ATR^2", overlay=false)

// Kullanıcıdan giriş değerleri
ma_length = input.int(14, title="MA Uzunluğu")
atr_length = input.int(14, title="ATR Uzunluğu")

// Hesaplamalar
price = close
ma = ta.sma(price, ma_length)
atr = ta.atr(atr_length)

// İlk formül: (fiyat^2 - MA^2) / ATR^2
indicator_value = (math.pow(price, 2) - math.pow(ma, 2)) / math.pow(atr, 2)

// Çizim
plot(indicator_value, color=color.blue, linewidth=2, title="Fiyat^2 - MA^2 / ATR^2")

// Sıfır çizgisi
hline(0, "0 Seviyesi", color=color.gray, linestyle=hline.style_dotted)
