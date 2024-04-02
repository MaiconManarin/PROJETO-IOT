# PROJETO-IOT
https://wokwi.com/projects/394077075536789505

#include <ESP32Servo.h>

Servo meuservo;

void setup() {
pinMode(18,OUTPUT);
pinMode(19,OUTPUT);
pinMode(21,OUTPUT);
pinMode(26,INPUT);
pinMode(32,INPUT);
Serial.begin(115200);
meuservo.attach(4);
}

void loop();
 
 botao();




void led(){
digitalWrite(18,HIGH);
digitalWrite(19,HIGH);
digitalWrite(21,LOW);
delay(1000);
digitalWrite(18,LOW);
digitalWrite(19,LOW);
digitalWrite(21,HIGH);
delay(1000);

}

void botao(){
  int valor = digitalRead(32);
  Serial.println(valor);


}
void servop(){
  
}

void testaDistancia(){
  digitalWrite(PIN_TRIG, HIGH);
  delayMicroseconds(10);
  digitalWrite(PIN_TRIG, LOW);

  // Leia o resultado:
  int duration = pulseIn(PIN_ECHO, HIGH);
  Serial.print("Distância em CM: ");
  int dist = duration / 58;
  Serial.println(dist);

  StaticJsonDocument<300> dadoDistancia;

  dadoDistancia["variable"] = "sensor_distancia";
  dadoDistancia["value"] = dist;

  serializeJson(dadoDistancia, distancia);

  client.publish("mini-projeto/distancia", distancia);
}






