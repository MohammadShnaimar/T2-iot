# T2-iot

![Copy of Serial Communication between two Arduino](https://github.com/MohammadShnaimar/T2-iot/assets/139280577/4ca7045e-3d2c-40b0-8ede-a2686fbbd598)

شرح مبسط للبروجكت: في حال تم الضعط على الزر في الاردوينو رقم واحد سوف يشتغل الليد اللذي في الاردوينو الثاني

هاذه الاكواد لكل اردوينو

اردوينو المرسل

void setup() {
  // Start serial connection
  Serial.begin(9600);
  // Configure pin 2 as an input and enable the internal pull-up resistor
  pinMode(2, INPUT_PULLUP);
}

void loop() {
  // Read the pushbutton value into a variable
  int sensorVal = digitalRead(2);
  // Send the pushbutton value to Arduino2 via Serial communication
  Serial.println(sensorVal);
  delay(100); // A small delay to avoid flooding the Serial communication
}









اردوينو المستقبل

int ledPin = 13; // LED connected to pin 13

void setup() {
  // Start serial connection
  Serial.begin(9600);
  // Configure pin 13 as an output
  pinMode(ledPin, OUTPUT);
}

void loop() {
    int sensorVal = Serial.parseInt();

    // Keep in mind the pull-up means the pushbutton's logic is inverted.
    // It goes HIGH when it's open, and LOW when it's pressed.
    // Turn on the LED when the button's pressed, and off when it's not:
    if (sensorVal == HIGH) {
      digitalWrite(ledPin, LOW);
    } else {
      digitalWrite(ledPin, HIGH);
    }
  }

