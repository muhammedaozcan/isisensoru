#include <SoftwareSerial.h>
#include <LiquidCrystal.h>
String agadi = "SUPERONLINE_WiFi_6CA4";
String agpass = "KJH39LVFR4PC";
String TS_IP="184.106.153.149";
const int lm35 = A0;
float voltaj_deger = 0;
float sicaklik = 0;
int gelen_veri = 0;
LiquidCrystal lcd(13, 12, 5, 4, 3, 2);
SoftwareSerial esp(10,11);
void setup() {
lcd.begin(16, 2);
Serial.begin(9600);
pinMode(lm35, INPUT); 
esp.begin(115200);
esp.println("AT");
if (esp.find("OK")) { 
    esp.println("AT+CWMODE=1"); //client - station(give) - access point(take)
    delay(2000);
    esp.println(("AT+CWJAP=\"")+agadi+"\",\""+agpass + "\""); 
    Serial.println("Baglanti Basarili");
    delay(2000);}

else  {Serial.println("ESP8266 aygiti bulunamiyor");}
}

void loop() {
gelen_veri = analogRead(lm35);
voltaj_deger = (gelen_veri / 1023.0) * 5000;
sicaklik = voltaj_deger / 10.0;
esp.println("AT+CIPSTART=\"TCP\",\""+TS_IP+"\",80");
delay(1000);
if (esp.find("Error")) { 
   esp.println("AT+CIPSTART Error");
   return;
  }
String sicaklikkomutu = "GET /update?key=TMSBWRTZG53G9G9D&field1=";
  sicaklikkomutu += String(sicaklik); 
  sicaklikkomutu += "\r\n\r\n"; 
  esp.print("AT+CIPSEND="); 
  esp.println(sicaklikkomutu.length() + 2); 
  delay(2000);
  if (esp.find(">")) { 
    esp.print(sicaklikkomutu);
    esp.print("\r\n\r\n");
    Serial.print("Sıcaklık Değeri= ");
    Serial.println(sicaklik);
    lcd.clear();
    lcd.home();
    lcd.print("sicaklik = ");
    lcd.setCursor(0, 1);
    lcd.print(sicaklik);
    lcd.print(" derece");
    Serial.println("Veri gönderildi");
    delay(6000);
  } else {
    esp.println("AT+CIPCLOSE");
  }}
