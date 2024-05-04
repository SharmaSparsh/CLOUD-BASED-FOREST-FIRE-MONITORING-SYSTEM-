# CLOUD-BASED-FOREST-FIRE-MONITORING-SYSTEM-
Developed a cloud-based system for real-time monitoring of forest fires using IoT sensors and cloud computing. 
#include<LiquidCrystal.h>
#include <SoftwareSerial.h>
const byte rxPin=6;
const byte txPin=7;
SoftwareSerial mySerial(rxPin,txPin);
const int rs=13,en=12,d4=11,d5=10,d6=9,d7=8;
LiquidCrystal lcd(rs,en,d4,d5,d6,d7);
int buzzer=7;
int flame=2;
int smoke=A0;
float temp=A1;
void setup() {
  // put your setup code here, to run once:
  Serial.begin(9600);
  mySerial.begin(9600);
  lcd.begin(20,4);
pinMode(buzzer,OUTPUT);
pinMode(flame,INPUT);
pinMode(smoke,INPUT);
Serial.println("Setup Confirm");
}

void loop() {
  // put your main code here, to run repeatedly:
int temperature=analogRead(temp);
temperature = temperature/2;
int aag=digitalRead(flame);
int smok=analogRead(smoke);

if(aag==HIGH && smok==HIGH && temperature>60){
    mySerial.print('\r');
    mySerial.print(aag);
    mySerial.print('|');
    mySerial.print(smok);
    mySerial.print('|');
    mySerial.print(temperature);
    mySerial.print('\n');
    
    
    Serial.print('\r');
    Serial.print(aag);    
    Serial.print('|');
    Serial.print(smok);
    Serial.print('|');
    Serial.print(temperature);
    Serial.print('\n');
digitalWrite(buzzer,HIGH);
digitalWrite(buzzer,LOW);
delay(100);
digitalWrite(buzzer,HIGH);
digitalWrite(buzzer,LOW);
lcd.setCursor(0,0);
lcd.print("FIRE ALERT");
lcd.setCursor(0,1);
lcd.print("TEMP:");
lcd.setCursor(6,1);
lcd.print(temperature);
lcd.setCursor(0,2);
lcd.print("FIRE ALERT");
lcd.setCursor(0,3);
lcd.print("TEMP:");
lcd.setCursor(6,4);
lcd.print(temperature);
delay(250);
lcd.clear();
}
else if(aag==HIGH && smok==LOW && temperature>60){
    mySerial.print('\r');
    mySerial.print(aag);
    mySerial.print('|');
    mySerial.print(smok);
    mySerial.print('|');
    mySerial.print(temperature);
    mySerial.print('\n');
    
    
    Serial.print('\r');
    Serial.print(aag);    
    Serial.print('|');
    Serial.print(smok);
    Serial.print('|');
    Serial.print(temperature);
    Serial.print('\n');
digitalWrite(buzzer,HIGH);
digitalWrite(buzzer,LOW);
delay(100);
digitalWrite(buzzer,HIGH);
digitalWrite(buzzer,LOW);
lcd.setCursor(0,0);
lcd.print("HIGHLY FLAME DETECT");
lcd.setCursor(0,1);
lcd.print("TEMP:");
lcd.setCursor(6,1);
lcd.print(temperature);
lcd.setCursor(0,2);
lcd.print("HIGHLY FLAME DETECT");
lcd.setCursor(0,3);
lcd.print("TEMP:");
lcd.setCursor(6,4);
lcd.print(temperature);
delay(250);
lcd.clear();
}
else if(aag==LOW && smok==HIGH && temperature>60){
    mySerial.print('\r');
    mySerial.print(aag);
    mySerial.print('|');
    mySerial.print(smok);
    mySerial.print('|');
    mySerial.print(temperature);
    mySerial.print('\n');
    
    
    Serial.print('\r');
    Serial.print(aag);    
    Serial.print('|');
    Serial.print(smok);
    Serial.print('|');
    Serial.print(temperature);
    Serial.print('\n');
digitalWrite(buzzer,HIGH);
digitalWrite(buzzer,LOW);
delay(100);
digitalWrite(buzzer,HIGH);
digitalWrite(buzzer,LOW);
lcd.setCursor(0,0);
lcd.print("HIGHLY SMOKE DETECT");
lcd.setCursor(0,1);
lcd.print("TEMP:");
lcd.setCursor(6,1);
lcd.print(temperature);
lcd.setCursor(0,2);
lcd.print("HIGHLY SMOKE DETECT");
lcd.setCursor(0,3);
lcd.print("TEMP:");
lcd.setCursor(6,4);
lcd.print(temperature);
delay(250);
lcd.clear();
}
else if(aag==LOW && smok==LOW && temperature>90){
    mySerial.print('\r');
    mySerial.print(aag);
    mySerial.print('|');
    mySerial.print(smok);
    mySerial.print('|');
    mySerial.print(temperature);
    mySerial.print('\n');
    
    
    Serial.print('\r');
    Serial.print(aag);    
    Serial.print('|');
    Serial.print(smok);
    Serial.print('|');
    Serial.print(temperature);
    Serial.print('\n');
digitalWrite(buzzer,LOW);
lcd.setCursor(0,0);
lcd.print("TEMP IS HIGH");
lcd.setCursor(0,1);
lcd.print("TEMP:");
lcd.setCursor(6,1);
lcd.print(temperature);
lcd.setCursor(0,2);
lcd.print("TEMP IS HIGH");
lcd.setCursor(0,3);
lcd.print("TEMP:");
lcd.setCursor(6,4);
lcd.print(temperature);
delay(250);
lcd.clear();
}
else{
    mySerial.print('\r');
    mySerial.print(aag);
    mySerial.print('|');
    mySerial.print(smok);
    mySerial.print('|');
    mySerial.print(temperature);
    mySerial.print('\n');
    
    
    Serial.print('\r');
    Serial.print(aag);    
    Serial.print('|');
    Serial.print(smok);
    Serial.print('|');
    Serial.print(temperature);
    Serial.print('\n');
digitalWrite(buzzer,LOW);
lcd.setCursor(0,0);
lcd.print("NO FIRE ALERT");
lcd.setCursor(0,1);
lcd.print("TEMP:");
lcd.setCursor(6,1);
lcd.print(temperature);
lcd.setCursor(0,2);
lcd.print("NO FIRE ALERT");
lcd.setCursor(0,3);
lcd.print("TEMP:");
lcd.setCursor(6,4);
lcd.print(temperature);
delay(250);
lcd.clear();
}
}


