#define CW_FAST 1				//時計回り　　速い
#define CCW_FAST 2				//反時計回り　速い
#define CW_SLOW 3				//時計回り　　遅い
#define CCW_SLOW 4				//反時計回り　遅い
#define BRAKE 5					//ブレーキ

#define ON true					//LED で使用
#define OFF false				//上と同じ

int r_high = 11;
int r_low = 5;
int l_high = 10;
int l_low = 3;
int led = 2;					//LED使わない場合はコメントアウト

int slow_speed = 100;

void setup() {					//ピン指定
  pinMode(r_high, OUTPUT);
  pinMode(r_low, OUTPUT);
  pinMode(l_high, OUTPUT);
  pinMode(l_low, OUTPUT);
  pinMode(led, OUTPUT);			//LED使わない場合はコメントアウト
}

void signal_high(int mode){		//トランジスタの上2つの設定 l:左, r:右
  if(mode == CW_FAST){
    digitalWrite(l_high, LOW);
    digitalWrite(r_high, HIGH);
  }
  if(mode == CCW_FAST){
    digitalWrite(l_high, HIGH);
    digitalWrite(r_high, LOW);
  }
  if(mode == CW_SLOW){
    analogWrite(l_high, slow_speed);
    digitalWrite(r_high, HIGH);
  }
  if(mode == CCW_SLOW){
    digitalWrite(l_high, HIGH);
    analogWrite(r_high, slow_speed);
  }
  if(mode == BRAKE){
	digitalWrite(l_high, LOW);
    digitalWrite(r_high, LOW);
  }
}

void signal_low(int mode){		//トランジスタ下2つの設定 上と同じ
  if(mode == CW_FAST){
    digitalWrite(l_low, HIGH);
    digitalWrite(r_low, LOW);
  }
  if(mode == CCW_FAST){
    digitalWrite(l_low, LOW);
    digitalWrite(r_low, HIGH);
  }
  if(mode == CW_SLOW){
    digitalWrite(l_low, HIGH);
    analogWrite(r_low, slow_speed);
  }
  if(mode == CCW_SLOW){
    analogWrite(l_low, slow_speed);
    digitalWrite(r_low, HIGH);
  }
  if(mode == BRAKE){
    digitalWrite(l_low, HIGH);
    digitalWrite(r_low, HIGH);
  }
}

void rotation_mode(int mode){	//回転のモードを決める 1~5行目で定義してある
  signal_high(mode);
  signal_low(mode);
  delay(1000);
}

void light(bool mode){			//動作確認用のLED ONで光る, OFFで消える
  								//LED使わない場合はコメントアウト(loop内の二つも)
  if(mode) digitalWrite(led, HIGH);
  else digitalWrite(led, LOW);
  delay(2000);
}

void loop() {
  light(ON);
  rotation_mode(CW_FAST);
  rotation_mode(BRAKE);
  rotation_mode(CCW_FAST);
  rotation_mode(BRAKE);
  rotation_mode(CW_SLOW);
  rotation_mode(BRAKE);
  rotation_mode(CCW_SLOW);
  rotation_mode(BRAKE);
  light(OFF);
}
