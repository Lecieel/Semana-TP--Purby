# Semana-TP--Purby
Es algún tipo de robot o animatrónico que se parece a un furby pero con un mecanismo diferente y  forma de pingüino.

# ¿Qué se hizo?
Hicimos Purby, un proyecto inspirado en los Furbys, pero con nuestro propio diseño de pingüino. La idea fue hacer 
un juguete que pudiera detectar cuando alguien lo toca y reaccionar moviendo algunas partes y prendiendo luces.
# ¿Con qué propósito?
El propósito fue poner en práctica lo que aprendimos en la especialidad de programación y demostrar que podemos
crear algo desde cero usando programación y electrónica. También queríamos hacer un proyecto divertido.
# ¿Qué herramientas utilizamos?
Para hacer Purby utilizamos:
-Arduino UNO, que es el que controla todo.
-Un sensor PIR, para detectar movimiento.
-2 LEDs, para representar los ojos.
-3 servomotores, para mover los brazos y los parpados.
-Cables jumper, para conectar los componentes.
-El lenguaje de programación  C++, para programar el Arduino y decirle qué hacer.
-También usamos distintos materiales para armar el cuerpo y darle la forma de pingüino. (como la piel de un pingüino)

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
