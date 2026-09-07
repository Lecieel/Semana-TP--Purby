# Semana-TP--Purby
Es algún tipo de robot o animatronico que se parece a un furby pero con un mecanismo diferente y  forma de pinguino.


#include <Servo.h>

Servo ojos;     // Servo de los ojos
Servo brazor;   // Servo del brazo derecho
Servo brazol;   // Servo del brazo izquierdo

int SensorPIR = 2;
int LED = 13;

void setup() {

  // Servos
  ojos.attach(9);
  brazor.attach(6);
  brazol.attach(4);

  // PIR y LED
  pinMode(SensorPIR, INPUT);
  pinMode(LED, OUTPUT);

  Serial.begin(9600);
}

void loop() {

  // Leer sensor PIR
  int valor = digitalRead(SensorPIR);

  Serial.println(valor);

  // Si detecta movimiento
  if (valor == HIGH) {

    // abrir ojos
    ojos.write(5);
    digitalWrite(LED, HIGH);
    delay(2000);

    // Mover brazos
    brazor.write(50);
    brazol.write(130);
    delay(200);

    //CERRAR OJOS
    ojos.write(20);
    digitalWrite(LED,LOW);
    delay(1000);

    // abrir ojos
    ojos.write(5);
    digitalWrite(LED, HIGH);
    delay(2000);

    brazor.write(90);
    brazol.write(90);
    delay(1000);

    brazor.write(50);
    brazol.write(130);
    delay(100);

    //CERRAR OJOS
    ojos.write(20);
    digitalWrite(LED,LOW);
    delay(1000);

  } else {

    // Apagar LED
    digitalWrite(LED, LOW);

    // cerrar ojos
    ojos.write(20);
    brazor.write(90);
    brazol.write(90);
  }

  delay(100);
}
