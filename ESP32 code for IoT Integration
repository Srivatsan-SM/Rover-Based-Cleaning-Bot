#include <WiFi.h>
#include <HTTPClient.h>

const char* ssid = "Srivatsan";
const char* password = "232617112004";
const String serverURL = "Placeholder for now";

String trashType = "unknown";
String wetStatus = "unknown";

void setup() {
  Serial.begin(9600);  // Read from Arduino
  WiFi.begin(ssid, password);
  while (WiFi.status() != WL_CONNECTED) {
    delay(1000);
    Serial.println("Connecting to WiFi...");
  }
  Serial.println("Connected!");
}

void loop() {
  if (Serial.available()) {
    String data = Serial.readStringUntil('\n');

    if (data.startsWith("RAIN:")) {
      wetStatus = data.substring(5);
    } else if (data.startsWith("TRASH:")) {
      trashType = data.substring(6);
    }

    // Send to Web App
    HTTPClient http;
    http.begin(serverURL);
    http.addHeader("Content-Type", "application/json");

    String json = "{\"trashType\":\"" + trashType + "\",\"wet\":\"" + wetStatus + "\"}";
    int responseCode = http.POST(json);
    http.end();

    delay(1000); // Rate limit
  }
}
