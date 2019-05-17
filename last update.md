int lmp=42; //left motorplus
int lmm=43; //left motorminus
int lmpwm=4;  //leftmotorpwm
int rmp=36; //rightmotorplus
int rmm=37; //rightmotorminus
int rmpwm=2;  //rightmotorpwm
int ledPin=13;
int state=0;
int flag=0;
int trigpinb=30;    //trigpinback
int echopinb=31;    //echopinback
int trigpinf=48;    //trigpinfront
int echopinf=49;    //echopinfront
int trigpinl=53;    //trigpinleft
int echopinl=52;    //echopinleft
long durationb;
int distanceb;
long durationf;
int distancef;
long durationl;
int distancel;
int backdistance() {     //back thing distance
  digitalWrite(trigpinb,LOW);
  delay(2);
  digitalWrite(trigpinb,HIGH);
  delay(10);
  digitalWrite(trigpinb,LOW);
  
  durationb=pulseIn(echopinb, HIGH);
  distanceb=durationb*0.034/2;
  Serial.print("Distance back:");
  Serial.println(distanceb);
  return distanceb;
}

int frontdistance() {     //front thing distance
  digitalWrite(trigpinf,LOW);
  delay(2);
  digitalWrite(trigpinf,HIGH);
  delay(10);
  digitalWrite(trigpinf,LOW);
  
  durationf=pulseIn(echopinf, HIGH);
  distancef=durationf*0.034/2;
  Serial.print("Distance front:");
  Serial.println(distancef);
  return distancef;
}

int leftdistance() {     //left thing distance
  digitalWrite(trigpinl,LOW);
  delay(2);
  digitalWrite(trigpinl,HIGH);
  delay(10);
  digitalWrite(trigpinl,LOW);
  
  durationl=pulseIn(echopinl, HIGH);
  distancel=durationl*0.034/2;
  Serial.print("Distance left:");
  Serial.println(distancel);
  return distancel;
}


void lmfor() {      //leftmotorforward
  digitalWrite(lmp,HIGH);
  digitalWrite(lmm, LOW);
  analogWrite(lmpwm,255);
}

void lmrev() {      //leftmotorreverse
  digitalWrite(lmm,HIGH);
  digitalWrite(lmp, LOW);
  analogWrite(lmpwm,255);
}

void rmfor() {    //rightmotorforward
  digitalWrite(rmp,HIGH);
  digitalWrite(rmm, LOW);
  analogWrite(rmpwm,255);
}

void rmrev() {    //rightmotorreverse
  digitalWrite(rmm,HIGH);
  digitalWrite(rmp, LOW);
  analogWrite(rmpwm,255);
}

void rmstop() {    //rightmotorstop
  digitalWrite(rmp,LOW);
  digitalWrite(rmm, LOW);
  analogWrite(rmpwm,0);
}

void lmstop() {      //leftmotorstop
  digitalWrite(lmm,LOW);
  digitalWrite(lmp, LOW);
  analogWrite(lmpwm,0);
}

void forward() {      //car forward
  rmfor();
  lmfor();
}

void reverse() {      //car reverse
  rmrev();
  lmrev();
}

void left() {       //car left
  rmfor();
  lmrev();
}

void right() {      //car right
  lmfor();
  rmrev();
}

void vehstop() {      //vehicle stop
  rmstop();
  lmstop();
}
void setup() {
  pinMode(ledPin, OUTPUT);
  digitalWrite(ledPin, LOW);
  pinMode(lmp,OUTPUT);
  pinMode(lmm, OUTPUT);
  pinMode(lmpwm,OUTPUT);
  pinMode(rmp,OUTPUT);
  pinMode(rmm, OUTPUT);
  pinMode(rmpwm,OUTPUT);
  pinMode(trigpinb,OUTPUT);
  pinMode(echopinb, INPUT);
  pinMode(trigpinf,OUTPUT);
  pinMode(echopinf, INPUT);
  pinMode(trigpinl,OUTPUT);
  pinMode(echopinl, INPUT);
  Serial.begin(9600);
  // put your setup code here, to run once:

}

void loop() {
  vehstop();
  
  /*if(Serial.available()>0) {
    state=Serial.read();
    flag=0;
  }
  int x=frontdistance();
  if (state == '0') {
    if(x<=20) {
    vehstop();
    Serial.println("stop");
    } else if(x>20) {
      forward();
      Serial.println("forward");
    }
  }
   else if (state == '1') {
    reverse();
    Serial.println("rev");
  }
   else if (state== '2') {
    left();
    Serial.println("left");
  }
   else if (state== '3') {
    right();
    Serial.println("right");
  }
  else if (state== '4') {
    vehstop();
    Serial.println("right");
  }
 
  //Serial.println("done!!");
  // put your main code here, to run repeatedly:
*/
}
