# Temperature-measuring-using-Arduino
https://www.tinkercad.com/things/cUgLWvBDdKi-brave-bruticus-rottis/editel
 Link to the Environment where it was developed

#define sensorPin  A0
#define greenLED 2
#define yellowLED 3
#define redLED 4

void setup()
{
  pinMode(greenLED, OUTPUT);
  pinMode(yellowLED, OUTPUT);
  pinMode(redLED, OUTPUT);
  Serial.begin(9600);
}
Code : 
void loop()
{
  int reading = analogRead(sensorPin);
  float voltage = reading * 5.0;
  voltage /= 1024.0;
  float temperatureC = (voltage - 0.5) * 100 ;
  float temperatureF = (temperatureC * 9.0 / 5.0) + 32.0;

  Serial.print(voltage); Serial.print(" volts  -  ");
  Serial.print(temperatureC); Serial.print(" degrees C  -  ");
  Serial.print(temperatureF); Serial.println(" degrees F");

  if (temperatureF >= 102.5) {
    digitalWrite(greenLED, LOW);
    digitalWrite(yellowLED, LOW);
    digitalWrite(redLED, HIGH);
  }
  else if (temperatureF >= 98 && temperatureF < 102.5) {
    digitalWrite(greenLED, LOW);
    digitalWrite(yellowLED, HIGH);
    digitalWrite(redLED, LOW);
  }
  else {
    digitalWrite(greenLED, HIGH);
    digitalWrite(yellowLED, LOW);
    digitalWrite(redLED, LOW);
  }

  delay(2000);
}
