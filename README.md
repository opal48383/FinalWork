# Arduino  
### 學習Arduino的過程
--- 
### LED.Flashing
將LED閃爍，亮燈100ms，協滅100ms
```c++
void  setup (){
   pinMode(2,OUTPUT);
}

void  loop (){
 digitalWrite (2,HIGH);
 delay (100);
 digitalWrite (2,LOW);
 delay(100);
}
```
#### 功能如下:
![gif](https://github.com/opal48383/FinalWork/raw/master/20201222_115827_1[1].gif)
--- 
### LED.LtoR
將LED由左至右逐一亮滅
```c++
int LED = 5;  
void  setup (){  
  for ( int i = 2 ; i < 6 ; i ++)  
  pinMode(i,OUTPUT);  
}  
  
void  loop (){  
  for ( int i = 5 ; i > 1 ; i--)  
    digitalWrite (i , HIGH);  
  if (LED >= 2)  
    digitalWrite (LED , LOW);  
  else  
    LED = 6;  
    LED --;  
  delay(500);
```
#### 功能如下:
--- 
### BreathingLight
將LED的亮度由255降至0，再由0升至255  
做出一個呼吸燈
```c++
int value=255;  
int x=-15;  
  
void setup() {  
pinMode(3,OUTPUT);  
}  
  
void loop() {  
if (value<=0 || value>=255) x=-x;  
analogWrite(3,value);  
delay(10);  
value=value-x;  
}  
```
#### 功能如下: 
--- 
### 12.01.1341-ButtonLED
將LED變成能用手動開關
```c++
void setup() {
pinMode(2,OUTPUT);
pinMode(3,INPUT);
}

void loop() {
    while(digitalRead(3) == LOW)
    {
      while (digitalRead(3) == LOW)
      {}digitalWrite( 2 , !digitalRead(2));
    }
    delay(200);
}
```
#### 功能如下: 
--- 
### 12.01.1444-RCspeed
使用Button來切換RC Servo的速度
```c++
#include <Servo.h>
Servo RC;
int a = 0;
void setup() {
  RC.attach(9);
  pinMode(4,INPUT);
}

void loop() {
  if (digitalRead(4) == 0)
  { while(digitalRead(4) == 0);
    a = (a+1)%7;
    delay(250);
  }
  switch(a){
    case 0:
      RC.write(0);
    break;
    case 1:
      RC.write(30);
    break;
    case 2:
      RC.write(60);
    break;
    case 3:
      RC.write(90);
    break;
    case 4:
      RC.write(120);
    break;
    case 5:
      RC.write(150);
    break;
    case 6:
      RC.write(180);
    break;
  }
}
```
#### 功能如下: 
--- 
### 12.08.0945-HT6751B
讓風扇自動切換正逆轉
```c++
void setup() {
pinMode(2,OUTPUT);//IN3
pinMode(5,OUTPUT);//IN1
pinMode(6,OUTPUT);//IN2
}

void loop() {
    fowr(200);
    delay(1000);
    brake();
    delay(2000);
    rev(200);
    delay(1000);
}
void fowr(int f) {
    analogWrite (5,f);
    analogWrite (6,0);
  }
void rev(int r) {
    analogWrite (5,0);
    analogWrite (6,r);
}
void brake() {
    analogWrite (5,255);
    analogWrite (6,255);
}
```
#### 功能如下: 
--- 
# 12.08.1100-HT6751B.Speed
使用一顆按鈕控制風扇的開關  
再使用另一顆按鈕控制風扇轉速  
```c++
int a = -1;  
boolean SW = true;  
void setup() {  
Serial.begin(9600);  
pinMode(2,OUTPUT);//IN3  
pinMode(5,OUTPUT);//IN1  
pinMode(6,OUTPUT);//IN2  
pinMode(4,INPUT);//button  
pinMode(8,OUTPUT);//6  
pinMode(9,OUTPUT);//5  
pinMode(10,OUTPUT);//4  
pinMode(11,OUTPUT);//3  
pinMode(12,OUTPUT);//2  
pinMode(13,OUTPUT);//1  
pinMode(3,INPUT);//SW  
}  
  
void loop() {  
  if (digitalRead(3) == 0)  
  {  
  Serial.print("Button: ");  
  Serial.println(digitalRead(3));  
   while(digitalRead(3) == 0);  
    if (SW == true)  
    {  
      SW = false;  
      a=-1;  
      digitalWrite(13,HIGH);  
      digitalWrite(12,HIGH);  
      digitalWrite(11,HIGH);  
      digitalWrite(10,HIGH);  
      digitalWrite(9,HIGH);  
      digitalWrite(8,HIGH);  
    }  
    else  
    {  
     SW = true ;   
     a = 0;   
    }  
    Serial.print("SW: ");  
    Serial.println(SW);  
    delay(250);  
  }  
   if (digitalRead(4) == 0)  
  { while(digitalRead(4) == 0);   
  if( SW == true ){ a = (a+1)%6;   
    delay(250);  
    Serial.print("Speed: ");  
    Serial.println(a);}   
  }  
  switch(a){  
    case 0:  
      Speed(110);  
      digitalWrite(13,LOW);  
      digitalWrite(12,HIGH);  
      digitalWrite(11,HIGH);  
      digitalWrite(10,HIGH);  
      digitalWrite(9,HIGH);  
      digitalWrite(8,HIGH);  
    break;  
    case 1:  
      Speed(139);  
      digitalWrite(13,LOW);  
      digitalWrite(12,LOW);  
      digitalWrite(11,HIGH);  
      digitalWrite(10,HIGH);  
      digitalWrite(9,HIGH);  
      digitalWrite(8,HIGH);  
    break;  
    case 2:  
      Speed(168);  
      digitalWrite(13,LOW);  
      digitalWrite(12,LOW);  
      digitalWrite(11,LOW);  
      digitalWrite(10,HIGH);  
      digitalWrite(9,HIGH);  
      digitalWrite(8,HIGH);  
    break;  
    case 3:  
      Speed(197);  
      digitalWrite(13,LOW);  
      digitalWrite(12,LOW);  
      digitalWrite(11,LOW);  
      digitalWrite(10,LOW);  
      digitalWrite(9,HIGH);  
      digitalWrite(8,HIGH);  
    break;  
    case 4:  
      Speed(226);  
      digitalWrite(13,LOW);  
      digitalWrite(12,LOW);  
      digitalWrite(11,LOW);  
      digitalWrite(10,LOW);  
      digitalWrite(9,LOW);  
      digitalWrite(8,HIGH);  
    break;  
    case 5:  
      Speed(255);  
      digitalWrite(13,LOW);  
      digitalWrite(12,LOW);  
      digitalWrite(11,LOW);  
      digitalWrite(10,LOW);  
      digitalWrite(9,LOW);  
      digitalWrite(8,LOW);  
    break;  
        case -1:  
      Speed(0);  
      digitalWrite(13,HIGH);  
      digitalWrite(12,HIGH);  
      digitalWrite(11,HIGH);  
      digitalWrite(10,HIGH);  
      digitalWrite(9,HIGH);  
      digitalWrite(8,HIGH);  
    break;  
  }  
}  
  
void Speed(int S) {  
    analogWrite (5,S);  
    analogWrite (6,0);  
  }  
  ```
#### 功能如下: 
--- 
# 12.15.1334-LCDupdown
一開始先用LCD顯示"Welcome!"
再變成上下可拉動的選單
```c++
/*
  The circuit:
 * LCD RS pin to digital pin 12
 * LCD Enable pin to digital pin 11
 * LCD D4 pin to digital pin 5
 * LCD D5 pin to digital pin 4
 * LCD D6 pin to digital pin 3
 * LCD D7 pin to digital pin 2
 * LCD R/W pin to ground
 * LCD VSS pin to ground
 * LCD VCC pin to 5V
 * 10K resistor:
 * ends to +5V and ground
*/
#include <LiquidCrystal.h>
const int rs = 12, en = 11, d4 = 5, d5 = 4, d6 = 3, d7 = 2;
LiquidCrystal lcd(rs, en, d4, d5, d6, d7);
String LCD[]{"A","B","C","D"};

int a=0,b=0;
bool SW=false;

void setup() {
  pinMode(7,INPUT);
  pinMode(6,INPUT);
  lcd.begin(16, 2);
  lcd.clear();
  lcd.print("Welcome!");
}

void loop() {
    if(SW == false){
    if (digitalRead(7) == 0 || digitalRead(6) == 0) {
    while (digitalRead(7) == 0 || digitalRead(6) == 0){}
    SW = true;
    lcd.clear();
    delay(200);
   }
    }
   else{
     if (digitalRead(7) == 0) {
        while (digitalRead(7) == 0){}
         a++;
         delay(200);
         lcd.clear();
      }
      if (digitalRead(6) == 0) {
        while (digitalRead(6) == 0){}
        a--;
        delay(200);
        lcd.clear();
      }
      b = a + 1;
     if (a>=4){a=0;}
     if (b>=4){b=0;}
     if (a<=-1){a=3;}
     if (b<=-1){b=3;}
     lcd.setCursor(0, 0);
     lcd.print(LCD[a]);
     lcd.setCursor(0, 1);
     lcd.print(LCD[b]);
   }
}
```
#### 功能如下: 
--- 
# 12.29.1331-DHT  
讀取溫度及濕度  
溫度在大於26°C 小於28°C 時亮燈
```c++
#include <Adafruit_Sensor.h>
#include <DHT.h>
#include <DHT_U.h>
#define DHTPIN 2
#define DHTTYPE    DHT22
DHT_Unified dht(DHTPIN, DHTTYPE);
uint32_t delayMS;

void setup() {
  Serial.begin(9600);
  dht.begin();
  Serial.println(F("DHTxx Unified Sensor Example"));
  sensor_t sensor;
  delayMS = sensor.min_delay / 1000;
  pinMode(3,OUTPUT);
}

void loop() {
  delay(delayMS);
  sensors_event_t event;
  dht.temperature().getEvent(&event);
  if (isnan(event.temperature)) {
    Serial.println(F("Error reading temperature!"));
  }
  else {
    Serial.print(F("Temperature: "));
    Serial.print(event.temperature);
    Serial.println(F("°C"));
  }
  if (event.temperature >= 26.0 && event.temperature <= 28.0){
    digitalWrite(3,LOW);
  }
  else{digitalWrite(3,HIGH);}
  
  dht.humidity().getEvent(&event);
  if (isnan(event.relative_humidity)) {
    Serial.println(F("Error reading humidity!"));
  }
  else {
    Serial.print(F("Humidity: "));
    Serial.print(event.relative_humidity);
    Serial.println(F("%"));
  }
}
```
#### 功能如下:
