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

void setup() {
  Serial.begin(9600);
  pinMode(trigpinb,OUTPUT);
  pinMode(echopinb, INPUT);
  pinMode(trigpinf,OUTPUT);
  pinMode(echopinf, INPUT);
  pinMode(trigpinl,OUTPUT);
  pinMode(echopinl, INPUT);
}

void loop() {
  int lcd=leftdistance();
  int bcd=backdistance();
  int fcd=frontdistance();
  delay(1000);
}
