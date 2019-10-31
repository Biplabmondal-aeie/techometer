#include<LiquidCrystal.h>
LiquidCrystal lcd(12,11,10,9,8,7);
float value=0;
float rev=0;
int rpm;
int oldtime=0;
int time;

void isr() 
rev++;
}

void setup()
{
lcd.begin(16,2); 
attachInterrupt(0,isr,RISING); 

void loop()
{
delay(1000);
detachInterrupt(0);  
time=millis()-oldtime;  
rpm=(rev/time)*60000*3;  
oldtime=millis();  
rev=0;
lcd.clear();
lcd.setCursor(3,0);
lcd.print("TACHOMETER");
lcd.setCursor(4,1);
lcd.print( rpm);
lcd.print(" RPM");
lcd.print(" ");
attachInterrupt(0,isr,RISING);
}
