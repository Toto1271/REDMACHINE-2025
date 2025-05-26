# Documento de ingeniería / Red Machine 

Este repositorio contiene todos los materiales necesarios para crear a "pompo", el robot autonomo creado por el equipo "Red Machine", con el objetivo de participar en la categoría de Futuros Ingenieros en las diferentes etapas de la WRO Venezuela, en su edición 2025. 

![Luka`s front](https://github.com/user-attachments/assets/cb8bf7b5-eaee-497f-9a00-b02afdd8bf22)


# Contenido

 -  [Miembros del equipo Red Machine]
 -  [Introduction] 
 -  [Diseño mecánico]
 -  [Diseño del software]
 -  [Mechanical Index]
 -  [Historia y cronología]


# Miembros de Red Machine
-Samuel Jose Galban Franco

-Juan Diego Cano Barros

-Angel Saul Rodriguez Guerra

![red machine 2024](https://github.com/RoboticaLLR/redmachine2024/assets/146040533/d5bb5fc0-b1bd-47a8-9ac3-c190587ae5ae)

   
# Introducción
El equipo ha hecho su mayor esfuerzo para conseguir construir el mejor robot posible. Nuestra preparación para estas olimpiadas se ha basado en un largo aprendizaje en construcción, diseño y programación, y la experiencia de competencias anteriores ha sido fundamental. Largas horas de análisis y estudio de la pista ha llevado a la creación de una estrategia propia, basada en los componentes con los que el equipo deseó trabajar, y esperando conseguir la mejor participación posible en las diversas etapas de esta competencia. 


# Diseño mecánico
"Pompo" es un robot autónomo diseñado con piezas de lego, con la finalidad de conseguir la mayor presición y estabilidad posible durante las rondas de competencia. Dichas piezas fueron extraídas de un kit lego spike prime código 45678 y spike prime expansion set código 45681. 
El fundamento que llevó a utilizar piezas de lego para el cuerpo de pompo se basa en la conocida eficiencia de los robots construidos de dicha manera, tomando en cuenta los resultados positivos y la facilidad que permiten a la hora de la construcción. 
Además, se agrega un diseño 3D del diseño de Pompo, donde se pueden ver y analizar eficientemente todos los componentes, piezas y estructuras: 



## Componentes electrónicos 
A pesar de que la construcción del robot fue hecha con piezas de lego, para todo el apartado electrónico el equipo se decidió por utilizar piezas externas con las que ya se han familiarizado. Entre estas se encuentran los siguientes sensores y actuadores:


Arduino Mega 2560: Es una placa microcontroladora basada en el ATmega2560. Tiene 54 pines de entrada/salida digital y 16 entradas analógicas, un oscilador de cristal de 16 MHz, una conexión USB, una toma de alimentación, una cabecera ICSP y un botón reset. El arduino es la placa que contiene el código para el funcionamiento de pompo, encargándose de analizar toda la información obtenida por los sensores para así lograr cumplir con el reto. 

![mega 2560](https://github.com/user-attachments/assets/edc71e77-3581-48eb-af96-6dfae65660ac)


Puente-H: Es un tipo de controlador que permite cambiar la polaridad de un motor de corriente continua, hacia delante y hacia atrás, además de ser la fuente de energía de diversos sensores. El modelo de puente H utilizado es el L298N, que nos permite cambiar la velocidad de los motores en función de la tensión enviada por el Arduino.

![puente H pequeño](https://github.com/RoboticaLLR/RedMachine/assets/146040533/264757f2-118f-42c9-9dd8-2a3c91455834)

Sensor de ultrasonido: Es un sensor que utiliza sonidos ultrasónicos para detectar el tiempo de rebote del sonido de un lado a otro. Utilizando el Arduino Mega 2560 se determina la distancia en base al tiempo que tarda la onda en volver, teniendo así este sensor la función de determinar cuando hay una pared cerca para así realizar el giro correspondiente.
El modelo utilizado de este sensor es el HC-sr04.

![HC-sr04](https://github.com/user-attachments/assets/a59b0102-8994-4ac4-aa06-3d6553ae1a2d)

Giroscopio: Es un sensor que mide la orientación del robot en grados. Se utiliza para poder realizar giros precisos, principalmente con la función de los giros para cambio de sección (giros de 90°), y mantener el robot con un movimiento en línea recta. 
El modelo utilizado de este sensor es 

![BNO055](https://github.com/user-attachments/assets/02c487ce-d624-411f-9db3-a2a3ef82a514)

Pixy 2.1: Es una cámara que tiene guardados valores que corresponden a los colores rgb de las señales de tráfico. Para detectar, la cámara busca esos valores en los píxeles de la imagen y, cuando se detecta un número exacto de pixeles de alguno de los colores anexados, pixy envía los datos al arduino, el cual se encarga luego de realizar los movimientos precisos para evitar los semáforos. 

![pixy2 1 2](https://github.com/user-attachments/assets/6397d5c9-d6fe-4c80-a7b9-d097bee0ba3e)


Servo motor de Rev Robotics: Es un motor eléctrico con sensor de retroalimentación de posición integrado, que permite realizar movimientos angulares perfectos, utilizando una señal que va de 0V a 5V, donde cada valor que pueda tener el voltaje representa un ángulo exacto, cumpliendo con excelencia la función de realizar los giros.

![servo pequeño](https://github.com/RoboticaLLR/RedMachine/assets/146040533/57aaa91d-b5e5-4360-aef2-06025d15f8b0)

Electric motor: A device that converts electrical energy into mechanical movement, allowing in this case to move a gearbox and mobilize the wheels. The speed and torque it has are determined by the voltage sent through the H-bridge, being moderated by the Arduino.

![motor pequeño](https://github.com/RoboticaLLR/RedMachine/assets/146040533/a74aacac-0276-49b0-abc1-485906c2a775)


El Arduino está alimentado por tres baterías de 9v, y enciende mediante un interruptor. Se encarga de alimentar y dar las respectivas señales al servomotor, para que sea capaz de realizar los cruces de forma efectiva con facilidad t al giroscopio, además de dar y recibir señales del resto de sensores. 

Por último, el puente H está conectado y alimentado por tres baterías de 3,7v y se enciende con el mismo interruptor que enciende el Arduino.
El puente H recibe señales del Arduino que llevan a mover el motor en diferentes direcciones y velocidades. También se encarga de alimentar los sensores ultrasónicos.


# Diseño del software

1. Image analysis
    -  [Image Processing](https://github.com/RoboticaLLR/redmachine2024/blob/main/src/Code.md#Image-Processing)
    -  [Color detection](https://github.com/RoboticaLLR/redmachine2024/blob/main/src/Code.md##Color-detection)
    - [Programming](https://github.com/RoboticaLLR/redmachine2024/blob/main/src/Code.md##Programming)
2. [Robot movement]
    - [Servo Determination](https://github.com/RoboticaLLR/redmachine2024/blob/main/src/Code.md#Servo-Determination)
    - [Orientation](https://github.com/RoboticaLLR/redmachine2024/blob/main/src/Code.md/#Orientation)
    - [Gyroscope Sideturns](https://github.com/RoboticaLLR/redmachine2024/blob/main/src/Code.md/#Gyroscope-Sideturns)
    - [First Challenge](https://github.com/RoboticaLLR/redmachine2024/blob/main/src/Code.md/#First-Challenge)
    - [Correction](https://github.com/RoboticaLLR/redmachine2024/blob/main/src/Code.md/#Correction)
    - [First Challenge parking](https://github.com/RoboticaLLR/redmachine2024/blob/main/src/Code.md/#First-Challenge-parking)
    - [Obstacle Challenge](https://github.com/RoboticaLLR/redmachine2024/blob/main/src/Code.md/#Obstacle-Challenge)
    - [Detection of Pillars](https://github.com/RoboticaLLR/redmachine2024/blob/main/src/Code.md/#Detection-of-Pillars)
    - [Movement through Orientation](https://github.com/RoboticaLLR/redmachine2024/blob/main/src/Code.md/#Movement-through-Orientation)
    - [Pillar avoidment First Lap](https://github.com/RoboticaLLR/redmachine2024/blob/main/src/Code.md/#Pillar-avoidment-First-Lap)
    - [Post-first sideturn](https://github.com/RoboticaLLR/redmachine2024/blob/main/src/Code.md/#Post-first-sideturn)
    - [Pillar storage](https://github.com/RoboticaLLR/redmachine2024/blob/main/src/Code.md/#Pillar-storage)
    - [Second and Third Lap Strategy](https://github.com/RoboticaLLR/redmachine2024/blob/main/src/Code.md/#Second-and-Third-Lap-Strategy)
    - [Next Pillar](https://github.com/RoboticaLLR/redmachine2024/blob/main/src/Code.md/#Next-Pillar)
    - [Sideturns](https://github.com/RoboticaLLR/redmachine2024/blob/main/src/Code.md/#Sideturns)
    - [Parking Obstacle Challenge](https://github.com/RoboticaLLR/redmachine2024/blob/main/src/Code.md/#Parking-Obstacle-Challenge)





# Videos del funcionamiento de pompo
 - [Primer reto (TODAS LAS POSIBILIADES)](https://www.youtube.com/watch?v=auAgh7E2WA8)

[![image](https://github.com/user-attachments/assets/ed1c0d5b-dab7-4e8b-98aa-dfcefc9b1e91)](https://www.youtube.com/watch?v=auAgh7E2WA8)
 

 - [Second challenge practice](https://www.youtube.com/watch?v=cjjnRDXaDAU)

[![image](https://github.com/user-attachments/assets/b4dc474c-5cb7-4fe4-aece-13e8c19d635f)](https://www.youtube.com/watch?v=cjjnRDXaDAU)




# Índice mecánico
Para más información sobre la mecánica, se ha creado un documento en el que puedes consultar las especificaciones de las piezas y mecanismos del robot.

-  [Motors](https://github.com/RoboticaLLR/redmachine2024/blob/main/schemes/Mechanics.md#Analisis-del-funcionamiento-de-los-motores)
- [Sensors](https://github.com/RoboticaLLR/redmachine2024/blob/main/schemes/Mechanics.md#Sensors)
-  [Camera](https://github.com/RoboticaLLR/redmachine2024/blob/main/schemes/Mechanics.md#Camera)
- [Controller boards](https://github.com/RoboticaLLR/redmachine2024/blob/main/schemes/Mechanics.md#Controller-cards)
 - [Robot power](https://github.com/RoboticaLLR/redmachine2024/blob/main/schemes/Mechanics.md#Robot-power)
 - [Conexions diagram](https://github.com/RoboticaLLR/redmachine2024/blob/main/schemes/Mechanics.md#Conexions-diagram)

# Historia y cronología del equipo

1. 2023 Season
- [July 2023](https://github.com/RoboticaLLR/redmachine2024/blob/main/t-photos/History.md#July-2023)
- [August 2023](https://github.com/RoboticaLLR/redmachine2024/blob/main/t-photos/History.md#August-2023)
- [September 2023](https://github.com/RoboticaLLR/redmachine2024/blob/main/t-photos/History.md#September-2023)
- [October 2023](https://github.com/RoboticaLLR/redmachine2024/blob/main/t-photos/History.md#October-2023)
2. 2024 Season 
- [February 2024](https://github.com/RoboticaLLR/redmachine2024/blob/main/t-photos/History.md#February-2024)
- [March 2024](https://github.com/RoboticaLLR/redmachine2024/blob/main/t-photos/History.md#March-2024)
- [April 2024](https://github.com/RoboticaLLR/redmachine2024/blob/main/t-photos/History.md#April-2024)
- [May 2024](https://github.com/RoboticaLLR/redmachine2024/blob/main/t-photos/History.md#May-2024)
- [June 2024](https://github.com/RoboticaLLR/redmachine2024/blob/main/t-photos/History.md#June-2024)
- [October 2024](https://github.com/RoboticaLLR/redmachine2024/blob/main/t-photos/History.md#October-2024)
- [November 2024](https://github.com/RoboticaLLR/redmachine2024/blob/main/t-photos/History.md#November-2024)
3. Julian´s and Luka´s history 
- [JULIAN 1.0](https://github.com/RoboticaLLR/redmachine2024/blob/main/t-photos/History.md#JULIAN-1.0)
- [JULIAN 2.0](https://github.com/RoboticaLLR/redmachine2024/blob/main/t-photos/History.md#JULIAN-2.0)
- [JULIAN 3.0](https://github.com/RoboticaLLR/redmachine2024/blob/main/t-photos/History.md#JULIAN-3.0)
- [JULIAN 4.0](https://github.com/RoboticaLLR/redmachine2024/blob/main/t-photos/History.md#JULIAN-4.0)
- [JULIAN 5.0](https://github.com/RoboticaLLR/redmachine2024/blob/main/t-photos/History.md#JULIAN-5.0)
- [LUKA 1.0](https://github.com/RoboticaLLR/redmachine2024/blob/main/t-photos/History.md#LUKA-1.0)
- [LUKA 2.0](https://github.com/RoboticaLLR/redmachine2024/blob/main/t-photos/History.md#LUKA-2.0)
- [LUKA 3.0](https://github.com/RoboticaLLR/redmachine2024/blob/main/t-photos/History.md#LUKA-3.0)