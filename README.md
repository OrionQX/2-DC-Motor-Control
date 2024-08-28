const int motor1Pin1 = 9;
const int motor1Pin2 = 7;
const int motor2Pin1 = 8;
const int motor2Pin2 = 10;

const int enA = 11;
const int enB = 6;

int hiz = 155;

void setup() {

  analogWrite(enA, hiz);
  analogWrite(enB, hiz);

  pinMode(motor1Pin1, OUTPUT);
  pinMode(motor1Pin2, OUTPUT);
  pinMode(motor2Pin1, OUTPUT);
  pinMode(motor2Pin2, OUTPUT);

  Serial.begin(9600);
}

void loop() {

  if (Serial.available() > 0) {

    char command = Serial.read();

    if (command == '1') {

      hiz = 255;
      analogWrite(enA, hiz);
      analogWrite(enB, hiz);
    } else if (command == '2') {

      hiz = 155;
      analogWrite(enA, hiz);
      analogWrite(enB, hiz);
    } else if (command == 'S') {

      digitalWrite(motor1Pin1, HIGH);
      digitalWrite(motor1Pin2, LOW);
      digitalWrite(motor2Pin1, HIGH);
      digitalWrite(motor2Pin2, LOW);
    } else if (command == 'W') {

      digitalWrite(motor1Pin1, LOW);
      digitalWrite(motor1Pin2, HIGH);
      digitalWrite(motor2Pin1, LOW);
      digitalWrite(motor2Pin2, HIGH);
    } else if (command == 'A') {

      digitalWrite(motor1Pin1, LOW);
      digitalWrite(motor1Pin2, HIGH);
      digitalWrite(motor2Pin1, LOW);
      digitalWrite(motor2Pin2, LOW);
    } else if (command == 'D') {

      digitalWrite(motor1Pin1, LOW);
      digitalWrite(motor1Pin2, LOW);
      digitalWrite(motor2Pin1, LOW);
      digitalWrite(motor2Pin2, HIGH);
    } else if (command == '-') {

      digitalWrite(motor1Pin1, LOW);
      digitalWrite(motor1Pin2, LOW);
      digitalWrite(motor2Pin1, LOW);
      digitalWrite(motor2Pin2, LOW);
    }
  }
}

