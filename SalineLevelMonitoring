#include "HX711.h"

float v;
HX711 loadcell;

uint8_t dataPin = 6;
uint8_t clockPin = 7;


void setup()
{
  Serial.begin(115200);
  Serial.println(__FILE__);
  Serial.print("LIBRARY VERSION: ");
  Serial.println(HX711_LIB_VERSION);
  Serial.println();

  loadcell.begin(dataPin, clockPin);

  Serial.print("UNITS: ");
  Serial.println(loadcell.get_units(10));

  Serial.println("\nEmpty the scale, press a key to continue");
  while(!Serial.available());
  while(Serial.available()) Serial.read();

  loadcell.tare();
  Serial.print("UNITS: ");
  Serial.println(loadcell.get_units(10));


  Serial.println("\nPut 1000 gr in the scale, press a key to continue");
  while(!Serial.available());
  while(Serial.available()) Serial.read();

  loadcell.calibrate_scale(1000, 5);
  Serial.print("UNITS: ");
  Serial.println(loadcell.get_units(10));

  Serial.println("\nScale is calibrated, press a key to continue");
  while(!Serial.available());
  while(Serial.available()) Serial.read();

  pinMode(4, OUTPUT);
}


void loop()
{
  v = loadcell.get_units(5);
  Serial.print("UNITS: ");
  Serial.println(v);
  delay(250);

  if(v < 100){
    digitalWrite(4, HIGH);
    delay(50);
    digitalWrite(4, LOW);
    delay(50);
    digitalWrite(4, HIGH);
    delay(50);
    digitalWrite(4, HIGH);
    delay(50);
    digitalWrite(4, LOW);
    delay(50);
  }
  else{
    digitalWrite(4,LOW);
  }
}
