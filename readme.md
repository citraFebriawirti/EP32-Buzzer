### BUZZER 
Buzzer pin gio13 +  gnd

### Push Button
pin gio12 +  gnd

```
#define BUTTON_PIN 12
#define BUZZER_PIN 13

bool isBuzzing = false;

void setup() {
  Serial.begin(9600);
  pinMode(BUTTON_PIN, INPUT_PULLUP);
  pinMode(BUZZER_PIN, OUTPUT);
  digitalWrite(BUZZER_PIN, LOW);
}

void loop() {
  int buttonState = digitalRead(BUTTON_PIN);

  if (buttonState == LOW) {  // Button is pressed (active LOW)
    if (!isBuzzing) {
      isBuzzing = true;
      digitalWrite(BUZZER_PIN, HIGH);
      Serial.println("ALERT:ON");
    }
  } else {  // Button is released
    if (isBuzzing) {
      isBuzzing = false;
      digitalWrite(BUZZER_PIN, LOW);
      Serial.println("ALERT:OFF");
    }
  }
}
```
