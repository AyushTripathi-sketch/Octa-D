
#include <Servo.h> 
#include <NewPing.h>
String voice;
#define left_motor_A 6
#define left_motor_B 5
#define right_motor_A 10
#define right_motor_B 9
#define led_1 13
#define led_2 12
#define TRIGGER_PIN A1
#define ECHO_PIN A0
#define MAX_DISTANCE 200
NewPing DistanceSensor(TRIGGER_PIN,ECHO_PIN,MAX_DISTANCE);
int cm,distance;
int pos=0;
int servoPin=7;
// Create a servo object 
Servo Servo2; 
void setup()
{
  Servo2.attach(servoPin);
  Serial.begin(9600);
  pinMode(left_motor_A,OUTPUT);
  pinMode(left_motor_B,OUTPUT);
  pinMode(right_motor_A,OUTPUT);
  pinMode(right_motor_B,OUTPUT);
  pinMode(led_1,OUTPUT);
  pinMode(led_2,OUTPUT);
  Servo2.write(90);
  delay(100);
  distance=readPing();
  delay(100);
  distance=readPing();
  delay(100);
  distance=readPing();
  delay(100);
  distance=readPing();
  delay(100); 
}
void loop()
{
  int distanceRight=0;
  int distanceLeft=0;
  delay(50);
  distance=readPing();
  Serial.print("Distance:  ");
  Serial.print(distance);
  Serial.println("cm");
  delay(100);
 
 while(Serial.available());
{
  voice=Serial.readString();
    Serial.println(voice);
   if(distance<=25)
   {digitalWrite(led_1,HIGH);
    Stop();
    delay(100);
    backward();
    delay(100);
    Stop();
    digitalWrite(led_1,LOW);
    delay(100);
    distanceRight=lookRight();
    delay(200);
    distanceLeft=lookLeft();
    delay(200);

    if(distance>=distanceLeft)
    {
      right();
      Stop();
    }
    else
    {
      left();
      Stop();
    }
   }
    else
    {
       if(voice=="#")
      forward();
      else if(voice=="forward"){
      forward(); Serial.println("forw");}
      else if(voice=="backward")
      backward();
      else if(voice=="left")
      left();
      else if(voice=="right")
      right();
      else if (voice=="stop")
      Stop();
      else if(voice=="on")
      {
      digitalWrite(led_1,HIGH);
      digitalWrite(led_2,HIGH);}
      else if(voice=="off")
     {digitalWrite(led_1,LOW);
     digitalWrite(led_2,LOW); }
    }
    distance=readPing();
}
}
  void forward()               
{
  digitalWrite(left_motor_B, LOW);
  digitalWrite(left_motor_A, HIGH);
  digitalWrite(right_motor_B, LOW);
  digitalWrite(right_motor_A, HIGH);
    
}
void backward()                           
{
  digitalWrite(left_motor_A, LOW);
  digitalWrite(left_motor_B, HIGH);
  digitalWrite(right_motor_A, LOW);
  digitalWrite(right_motor_B, HIGH);
  delay(300);
  Stop();
  }
  void right()                                
{
  digitalWrite(left_motor_A, HIGH);
  digitalWrite(left_motor_B, LOW);
  digitalWrite(right_motor_B, HIGH);
  digitalWrite(right_motor_A, LOW);
  delay(300);
  Stop();
  }

void left()                               
{
  digitalWrite(left_motor_B, HIGH);
  digitalWrite(left_motor_A, LOW);
  digitalWrite(right_motor_A, HIGH);
  digitalWrite(right_motor_B, LOW);
  delay(300);
  Stop();
}

void Stop()                              
{
  digitalWrite(left_motor_B, LOW);
  digitalWrite(left_motor_A, LOW);
  digitalWrite(right_motor_A, LOW);
  digitalWrite(right_motor_B, LOW);
}
int lookRight()
{
  Servo2.write(20);
  delay(200);
  int distance=readPing();
  delay(200);
  Servo2.write(90);
  return distance;
}
int lookLeft()
{
  Servo2.write(175);
  delay(200);
  int distance=readPing();
  delay(200);
  Servo2.write(90);
  return distance;
  delay(100);
}
int readPing()
{
  int cm=DistanceSensor.ping_cm();
  if(cm==0)
  cm=250;
  return cm;
}
