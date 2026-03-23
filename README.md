# AVI Player dla JC8048W550C (800x480, ESP32-S3)

Na podstawie projektu thelastoutpostworkshop/JC4827W543_avi_player.

## Wymagania

### Biblioteki (Library Manager w Arduino IDE):
- **GFX Library for Arduino** v1.5.6
- **TAMC_GT911** v1.0.2

### Biblioteki ZIP (Sketch → Include Library → Add .ZIP Library):
- **avilib**: zawarta w projekcie (avilib-master.zip)
- **arduino-libhelix**: zawarta w projekcie (arduino-libhelix-main.zip)

### Ustawienia płytki Arduino IDE:
- Board: **ESP32S3 Dev Module**
- USB CDC On Boot: "Enabled"
- Flash Mode: "QIO 80MHz"
- Flash Size: **16MB (128)**
- Partition Scheme: **16M Flash (3MB APP/9.9MB FATFS)**
- PSRAM: **OPI PSRAM**
- CPU Frequency: **240MHz(WiFi)**
- Core version: **3.2.0 lub nowszy**

## Piny JC8048W550C

| Funkcja | Pin |
|---------|-----|
| Backlight | GPIO 2 |
| Touch SDA | GPIO 19 |
| Touch SCL | GPIO 20 |
| SD CS | GPIO 10 |
| SD MISO | GPIO 11 |
| SD SCK | GPIO 12 |
| SD MOSI | GPIO 13 |
| I2S BCLK | GPIO 0 |
| I2S LRCK | GPIO 18 |
| I2S DOUT | GPIO 17 |

## Karta SD

Utwórz folder `/avi` na karcie SD i wgraj pliki AVI: przyklady zawarte w projekcie
```
/avi/
  film1.avi
  film2.avi
```

## Konwersja filmów (FFmpeg)

```bash
ffmpeg -i input.mp4 -c:v cinepak -q:v 10 -vf "fps=24,scale=800:480" -c:a mp3 -ac 1 -ar 22050 output.avi
```

**Uwaga:** Szerokość i wysokość muszą być wielokrotnością 4.

## Obsługa

- **Lewa strzałka** - poprzedni plik
- **Prawa strzałka** - następny plik  
- **Przycisk PLAY** - odtwórz zaznaczony plik
