Physical-Computing
==================
/*
Project Title: "'Night! Brite"
Marishka Zachariah
DIGF 2B03 Physical Computing
OCAD University
Created on Feb 1, 2014

Based on:
Fade: http://arduino.cc/en/Tutorial/Fade

*/

int photocellPin = 0;// Photocell connected to analog pin 0
int photocellVal = 0; // define photocell variable
int ledPin = 9;// LED connected to digital pin 9
int ledState = 0;//state of the led 
int fadeDown = 30;//delay per fade
int fadeUp = 20;//delay per fade
int minLight = 100;//min light threshold
int maxLight = 100;//max light threshold


void setup() {
 //Serial.begin(9600);
  pinMode(photocellPin, INPUT);
  pinMode(ledPin, OUTPUT);
}
void loop() {
  photocellVal = analogRead(photocellPin);

  if (photocellVal < minLight and ledState == 0){
    fadeLed(1);
    //Serial.println("fade up");
  }                      
    else if (photocellVal > maxLight and ledState == 1){
    fadeLed(0);
   // Serial.println("fade down");
  } 
    

  
}

void fadeLed(int num){
  if (num == 1){
     for(int fadeValue = 0 ; fadeValue <= 255; fadeValue +=5) { 
     analogWrite(ledPin, fadeValue);             
     delay(fadeUp);                            
    } 
     ledState = 1;
   
 } 
  else{  
     for(int fadeValue = 255 ; fadeValue >= 0; fadeValue -=5) { 
     analogWrite(ledPin, fadeValue);             
     delay(fadeDown);                            
  } 
   ledState = 0;
 } 

  
}

