int lmp=42; //left motorplus
int lmm=43; //left motorminus
int lmpwm=3;  //leftmotorpwm

int rmp=36; //rightmotorplus
int rmm=37; //rightmotorminus
int rmpwm=2;  //rightmotorpwm
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
  forward();
  delay(1000);
  reverse();
  delay(1000);
  left();
  delay(1000);
  right();
  delay(1000);
  vehstop();
  delay(1000);
  Serial.println("done!!");
  // put your main code here, to run repeatedly:

}
