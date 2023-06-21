#include <Servo.h>



//Threshold for servo motor control with muscle sensor. 
//You can set a threshold according to the maximum and minimum values of the muscle sensor.
#define THRESHOLD 600

//Pin number where the sensor is connected. (Analog 0)
#define EMG_PIN 0

//Pin number where the servo motor is connected. (Digital PWM 3)
#define SERVO_PIN 3

//Define Servo motor
Servo SERVO_1;


//Boolean to stop the motor
bool stop_bool_right = false;
bool stop_bool_left = false;
bool setval = true;

/*-------------------------------- void setup ------------------------------------------------*/

void setup(){
  
  //BAUDRATE set to 115200, remember it to set monitor serial properly. 
  //Used this Baud Rate and "NL&CR" option to visualize the values correctly.
  Serial.begin(115200);
  
  //Set servo motor to digital pin 3
//  SERVO_1.attach(SERVO_PIN);
}

/*--------------------------------  void loop  ------------------------------------------------*/

void loop(){

  //The "Value" variable reads the value from the analog pin to which the sensor is connected.
  int value = analogRead(EMG_PIN);
  delay(200);

  if(setval){
    SERVO_1.write(180);
    delay(100);
    setval = false;
  }


  //If the sensor value is GREATER than the THRESHOLD, the servo motor will turn to 170 degrees.
  if(value > THRESHOLD && !stop_bool_right){
    SERVO_1.attach(SERVO_PIN);
    SERVO_1.write(0);
    delay(35);
 
    stop_bool_right = true;
    stop_bool_left = false;
    SERVO_1.detach();
  }

  //If the sensor is LESS than the THRESHOLD, the servo motor will turn to 10 degrees.
  if(value < THRESHOLD*0.25 && !stop_bool_left){
    SERVO_1.attach(SERVO_PIN);
    SERVO_1.write(180);
    delay(35);
    stop_bool_right = false;
    stop_bool_left = true;
    SERVO_1.detach();
    
  }

//    Serial.println("right:" + String(stop_bool_right));
//    Serial.println("left:" + String(stop_bool_left));
    

    SERVO_1.write(90);
  //You can use serial monitor to set THRESHOLD properly, comparing the values shown when you open and close your hand.
  Serial.println(value);
}

