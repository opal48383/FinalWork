# Arduino  
### 學習Arduino的過程
--- 
### LED.Flashing
將LED閃爍，亮燈100ms，協滅100ms  
#### 功能如下:  
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
--- 
### LED.LtoR
將LED由左至右逐一亮滅  
#### 功能如下:  
🔴⚪⚪⚪  
⚪🔴⚪⚪  
⚪⚪🔴⚪  
⚪⚪⚪🔴  
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
--- 
### BreathingLight
將LED的亮度由255降至0，再由0升至255  
做出一個呼吸燈  
#### 功能如下:   
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
