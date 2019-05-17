int lmp=42; //left motorplus
int lmm=43; //left motorminus
int lmpwm=3;  //leftmotorpwm
int rmp=36; //rightmotorplus
int rmm=37; //rightmotorminus
int rmpwm=2;  //rightmotorpwm
int ledPin=13;
int state=0;
int flag=0;

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
  Serial.begin(9600);
  // put your setup code here, to run once:

}

void loop() {
  if(Serial.available()>0) {
    state=Serial.read();
    flag=0;
  }
  if (state == '0') {
    forward();
    Serial.println("forward");
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
    vehstopj();
    Serial.println("right");
  }
  //Serial.println("done!!");
  // put your main code here, to run repeatedly:

}
