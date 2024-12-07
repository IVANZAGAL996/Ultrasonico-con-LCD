# Ultrasonico-con-LCD

## INTRODUCCION

En esta practica haremos una combinacion de codigos para tranbajar con el sensor ultrasonico y poder visualizar la distancia en el display, ademas podremos observar nuestro nombre y el modulo qque estamos cursando.

Empezaremos realizando el siguiente codigo:

```
#include <LiquidCrystal_I2C.h>
#define I2C_ADDR    0x27
#define LCD_COLUMNS 20
#define LCD_LINES   4
LiquidCrystal_I2C lcd(I2C_ADDR, LCD_COLUMNS, LCD_LINES);
const int Trigger = 4;   //Pin digital 2 para el Trigger del sensor
const int Echo = 15;   //Pin digital 3 para el Echo del sensor

void setup() {
  Serial.begin(9600);//iniciailzamos la comunicación
  pinMode(Trigger, OUTPUT); //pin como salida
  pinMode(Echo, INPUT);  //pin como entrada
  digitalWrite(Trigger, LOW);//Inicializamos el pin con 0
   lcd.init();
  lcd.backlight();
}

void loop()
{

  long t; //timepo que demora en llegar el eco
  long d; //distancia en centimetros

  digitalWrite(Trigger, HIGH);
  delayMicroseconds(10);          //Enviamos un pulso de 10us
  digitalWrite(Trigger, LOW);
  
  t = pulseIn(Echo, HIGH); //obtenemos el ancho del pulso
  d = t/59;             //escalamos el tiempo a una distancia en cm
  
  lcd.clear();
 lcd.setCursor(2,0);
 lcd.print("DIPLOMADO V");
  lcd.setCursor(2,1);
  lcd.print("AUTOMATIZACION");
  delay(2000);

  lcd.clear();
 lcd.setCursor(2,0);
 lcd.print("IVAN ZAGAL");
  lcd.setCursor(2,1);
  lcd.print("ING MECANICA");
  delay(2000);

  Serial.print("Distancia: ");
  Serial.print(d);      //Enviamos serialmente el valor de la distancia
  Serial.print("cm");
  Serial.println();
  delay(1000);          //Hacemos una pausa de 100ms


  lcd.clear();
 lcd.setCursor(0,0);
 lcd.print("D=" + String (d)+ "cm");
  lcd.setCursor(0,0);
  delay(2000);
}
 ```
Cargaremos las siguientes librerias:

![](https://github.com/IVANZAGAL996/Ultrasonico-con-LCD/blob/main/librerias%203.PNG)

insertamos sensor y lcd:

![](https://github.com/IVANZAGAL996/Ultrasonico-con-LCD/blob/main/sensor%203.PNG)

![](https://github.com/IVANZAGAL996/Ultrasonico-con-LCD/blob/main/lcd3.PNG)

realizamos la siguiente conexión:

![](https://github.com/IVANZAGAL996/Ultrasonico-con-LCD/blob/main/conexion%203.PNG)

Cargamos programa e iniciamos simulacion y obtenemos los siguientes resultados:

![](https://github.com/IVANZAGAL996/Ultrasonico-con-LCD/blob/main/r11.PNG)

![](https://github.com/IVANZAGAL996/Ultrasonico-con-LCD/blob/main/r22.PNG)

![](https://github.com/IVANZAGAL996/Ultrasonico-con-LCD/blob/main/r33.PNG)

### creditos

Desarrollado por Edgar Ivan Prospero Zagal Ponce

[GitHub](https://github.com/IVANZAGAL996)





