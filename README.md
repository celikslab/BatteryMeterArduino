# BatteryMeterArduinoProject
## Arduino-Android Tabanlı Pil Kapasite Ölçer 
<p align="center">
  <img width="576" height="324" src="https://github.com/celikslab/BatteryMeterArduino/blob/main/images/ana.png">
</p>

## Kullanılan Malzemeler

<li>Arduino Nano</li>
<li>BreadBoard</li>
<li>Hc05 Bluetooth Modül</li>
<li>Dişi Header</li>
<li>Jumper Kablo</li>
<li>AA Pil Yatağı</li>
<li>10K direnç</li>
<li>Android Telefon</li>

## Devre Şeması

<p align="center">
  <img width="500" height="350" src="https://github.com/celikslab/BatteryMeterArduino/blob/main/images/schematic.png">
</p>

## Prototip

<p align="center">
  <img width="500" height="350" src="https://github.com/celikslab/BatteryMeterArduino/blob/main/images/prototip.jpg">
</p>

## Yazılım

### Arduino Kodları

```c++
#define pil A0
// 338 max - 1.65 V
// 246 min - 1.2 V
int min_deger = 246;
float yuzde = 0;
int deger = 0; 
float volt=0;
int gerilim = 0;
void setup() {
  
  Serial.begin(9600);
}
void loop() {
gerilim = analogRead(pil);
   volt = 1024 / 5; //1 volta karşılık gelen deger
   volt = gerilim / volt; 
  if(gerilim >= 338){
    gerilim = 338; 
  }
  if(gerilim <= 246){
    gerilim = 246; 
  }
   yuzde = gerilim - min_deger;
   deger = (100.00/92.00) * yuzde;  //max-mindeger =92dir.
   Serial.print(volt);
   Serial.print("V");
   Serial.print("|");
   Serial.print(deger);
   Serial.print( "%" ) ;
   Serial.print("|");
   delay(400);
  }

```

### Appİnventor Kodları 

<p align="center">
  <img width="500" height="350" src="https://github.com/celikslab/BatteryMeterArduino/blob/main/images/blocks.png">
</p>

