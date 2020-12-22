# Arduino  
### 學習Arduino的過程
--- 
#### LED.LtoR
LED由左至右逐一亮滅
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
#### 12.01.0942-BreathingLight
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
