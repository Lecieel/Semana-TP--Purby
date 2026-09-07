# ೃ࿔°❀⋆.ೃ࿔.*⋆.ೃ࿔.*:･･:*.ೃ࿔.⋆❀°ೃ
# Semana-TP--Purby ୨ৎ
Es algún tipo de robot o animatrónico que se parece a un furby pero con un mecanismo diferente y  forma de pingüino. 
# ────────────── ⋆⋅𖤓⋅⋆ ──────────────
# ¿Qué se hizo? ୨ৎ
Hicimos Purby, un proyecto inspirado en los Furbys, pero con nuestro propio diseño de pingüino. La idea fue hacer 
un juguete que pudiera detectar cuando alguien lo toca y reaccionar moviendo algunas partes y prendiendo luces.
# ¿Con qué propósito? ୨ৎ
El propósito fue poner en práctica lo que aprendimos en la especialidad de programación y demostrar que podemos
crear algo desde cero usando programación y electrónica. También queríamos hacer un proyecto divertido.
# ¿Qué herramientas utilizamos? ୨ৎ
Para hacer Purby utilizamos:
Para hacer a Purby utilizamos un Arduino UNO, que es el encargado de controlar todo, un sensor PIR para detectar
movimiento, 2 LEDs que representan sus ojos y 3 servomotores para mover los brazos y los párpados. También usamos 
cables jumper para conectar todos los componentes y programamos el Arduino utilizando el lenguaje C++, indicándole 
qué acciones realizar. Por último, usamos distintos materiales para armar su cuerpo y darle la forma y apariencia 
de un pingüino, como si tuviera su propia piel.

# ────────────── ⋆⋅𖤓⋅⋆ ──────────────
# Código ୨ৎ

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
