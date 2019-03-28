# Motion-based-message-conveyor
This project uses RF transmission technique to transmit specific messages assigned to a particular range on angles. It uses two arduino unos , RF transmitter , RF receiver , accelerometer and LCD Display
# TRANSMITTER END 
const int xpin = A0;                  
const int ypin = A1;        


#include <RH_ASK.h>
#include <SPI.h> // Not actually used but needed to compile

RH_ASK Radio(2000,"",2);

void setup() {
Serial.begin(9600);
pinMode(13,OUTPUT);
Serial.begin(9600);    // Debugging only
if (!Radio.init())
Serial.println("init failed");

}

void loop() 
{
int xval=analogRead(xpin);
int yval=analogRead(ypin);
if ((xval>=340 && xval<=350) && (yval>=279 && yval<=300)) 
{
send1();
}
if ((xval>=350 && xval<=360) && (yval>=400 && yval<=450))
{
send2();  
}
if ((xval>=260 && xval<=270) && (yval>=330 && yval<=340)) 
{
send3();  
}
if ((xval>=400 && xval<=410) && (yval>=350 && yval<=360))
{
send4();
}
}

void send1()
{
const char *msg  = "I need water";
Radio.send((uint8_t *)msg, strlen(msg));
    Radio.waitPacketSent();
    digitalWrite(13,HIGH);
    delay(1000);
    digitalWrite(13,LOW);
}
void send2()
 {
  const char *msg  = "I need food";


    Radio.send((uint8_t *)msg, strlen(msg));
    Radio.waitPacketSent();
    digitalWrite(13,HIGH);
    delay(1000);
    digitalWrite(13,LOW);
}

void send3()
 {
  const char *msg  = "Bathroom";
   
    Radio.send((uint8_t *)msg, strlen(msg));
    Radio.waitPacketSent();
    digitalWrite(13,HIGH);
    delay(1000);
    digitalWrite(13,LOW);
}
void send4()

 {
  const char *msg  = "help";
    Radio.send((uint8_t *)msg, strlen(msg));
    Radio.waitPacketSent();
    digitalWrite(13,HIGH);
    delay(1000);
    digitalWrite(13,LOW);
 }
  
