#include <IRremote.h>
int RECV_PIN = 10;
float armazenavalor;
int pwmPin = 6;
int ledVerde = 3;
int ledVermelho = 11;

IRrecv irrecv(RECV_PIN);
decode_results results;

void setup() {
  pinMode(pwmPin, OUTPUT);
  pinMode(ledVerde, OUTPUT);
  pinMode(ledVermelho, OUTPUT);
  Serial.begin(9600);
  irrecv.enableIRIn(); //Inicializa o receptor IR
}

void loop() {
  if (irrecv.decode(&results)) {
    Serial.print("Valor lido: ");
    Serial.println(results.value, HEX);
    armazenavalor = (results.value);
  }
  if(results.value == 0xAF548B7 || results.value == 0xFF6897){ //Botao +Volume ou 1
    analogWrite(pwmPin, 255);
    digitalWrite(ledVerde, HIGH);
    digitalWrite(ledVermelho, LOW);
  }
  if(results.value == 0xAF5A857 || results.value == 0xFF9867){ //Botao -Volume ou 2
    analogWrite(pwmPin, 0);
    digitalWrite(ledVerde, LOW);
    digitalWrite(ledVermelho, HIGH);
  }
  irrecv.resume(); //Le o próximo valor
}
