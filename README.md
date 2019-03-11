/*
    This sketch trys to Connect to the best AP based on a given list
    1. ssid - WiFi name
    It automatically connects the nodemcu with another WiFi if one of the WiFi signal is not in the range 
    */

#include <ESP8266WiFi.h>
#include <ESP8266WiFiMulti.h>

ESP8266WiFiMulti wifiMulti;

void setup() {
  Serial.begin(115200);
  delay(10);

  WiFi.mode(WIFI_STA);
  wifiMulti.addAP("ssid_from_AP_1", "your_password_for_AP_1");  //enter your ssid1 and password
  wifiMulti.addAP("ssid_from_AP_2", "your_password_for_AP_2"); // enter your ssid2 and password
 
}

void loop() {
  if (wifiMulti.run() != WL_CONNECTED) {
    Serial.println("WiFi not connected!");
    delay(1000);
  }
   if (wifiMulti.run() == WL_CONNECTED) {
    Serial.println("");
    Serial.println("WiFi connected");
    Serial.println(WiFi.SSID());  // It prints the name of your ssid which is connected to esp8266 board
    Serial.println("IP address: ");
    Serial.println(WiFi.localIP());
    delay(1000);
   }
}
