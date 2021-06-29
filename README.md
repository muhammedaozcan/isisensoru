# isisensoru
Sıcaklık sensöründen alınan verinin cloud üzerinden okunması


Projede kullanılan componentler;

1-Sıcaklık sensörü olarak LM35 (analog ısı ölçüm).
2-Breadboard, jumper, lcd gibi devre elemanları.
3.ESP8266 Wifi Serial Transceiver Modül
4. Arduino UNO
5. Windows işletim sistemli bilgisyar, Android Mobil telefon

Proje özeti:

Projede LM35 üzerinden okunan sıcaklık verisi board üstünde bulunan LCD üzerinden 6saniyede 1 olmak üzere görüntülenmektedir. Aynı sıcaklık verisi Thingsspeak.com bulutuna
bu veriyi sürekli güncellemektedir. Mobil uygulama olan "ThingsView Free" üzerinden de bu veri canlı olarak takip edilebilmktedir.
