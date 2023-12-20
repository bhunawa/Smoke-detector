
int ledPin1 = 2; // The first LED is connected to digital pin 2
int ledPin2 = 3; // The second LED is connected to digital pin 3
int buzzerPin = 4; // The buzzer is connected to digital pin 4
int sensorPin = A0; // The MQ2 sensor is connected to analog pin A0
int delayTime = 1000; // The initial delay time is set to 1000 milliseconds
int buzzerFrequency = 1000; // The initial frequency of the buzzer is set to 1000 Hz

void setup() {
  pinMode(ledPin1, OUTPUT); // Set the first LED pin as output
  pinMode(ledPin2, OUTPUT); // Set the second LED pin as output
  pinMode(buzzerPin, OUTPUT); // Set the buzzer pin as output
  pinMode(sensorPin, INPUT); // Set the MQ2 sensor pin as input
}

void loop() {
  int sensorValue = analogRead(sensorPin); // Read the sensor value
  if (sensorValue > 500) { // If the sensor value is above the threshold
    digitalWrite(ledPin1, HIGH); // Turn on the first LED
    tone(buzzerPin, buzzerFrequency); // Turn on the buzzer with the current frequency
    delay(delayTime); // Wait for delayTime milliseconds
    digitalWrite(ledPin1, LOW); // Turn off the first LED
    noTone(buzzerPin); // Turn off the buzzer

  digitalWrite(ledPin2, HIGH); // Turn on the second LED
  tone(buzzerPin, buzzerFrequency); // Turn on the buzzer with the current frequency
  delay(delayTime); // Wait for delayTime milliseconds
  digitalWrite(ledPin2, LOW); // Turn off the second LED
  noTone(buzzerPin); // Turn off the buzzer

  delayTime = delayTime + 100; // Increase the delay time by 100 milliseconds
  buzzerFrequency = buzzerFrequency + 50; // Increase the frequency of the buzzer by 50 Hz
  if (delayTime > 1000) { // If the delay time is more than 1000 milliseconds
  delayTime = 100; // Reset the delay time to 100 milliseconds
  buzzerFrequency = 1000; // Reset the frequency of the buzzer to 1000 Hz
    }
  } else { // If the sensor value is below the threshold
    digitalWrite(ledPin1, LOW); // Turn off the first LED
    digitalWrite(ledPin2, LOW); // Turn off the second LED
    noTone(buzzerPin); // Turn off the buzzer
  }
}
