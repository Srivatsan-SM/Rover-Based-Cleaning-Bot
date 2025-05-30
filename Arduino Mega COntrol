// Arduino Mega
#define L_MOTOR_1 2
#define L_MOTOR_2 3
#define R_MOTOR_1 4
#define R_MOTOR_2 5

#define GRABBER_SERVO_PIN 9
#define RAIN_SENSOR_PIN A0

int rainThreshold = 600;

void setup() {
  pinMode(L_MOTOR_1, OUTPUT);
  pinMode(L_MOTOR_2, OUTPUT);
  pinMode(R_MOTOR_1, OUTPUT);
  pinMode(R_MOTOR_2, OUTPUT);
  pinMode(RAIN_SENSOR_PIN, INPUT);

  Serial.begin(9600);  // To ESP32
}

void loop() {
  int rainValue = analogRead(RAIN_SENSOR_PIN);
  bool isWet = (rainValue < rainThreshold);

  // Send data to ESP32
  Serial.print("RAIN:");
  Serial.println(isWet ? "WET" : "DRY");

  // Add motor or servo control logic here based on trash detection
  delay(500);
}
