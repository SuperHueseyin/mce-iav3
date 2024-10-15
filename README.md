# mcr-iav3

``` 

#define LED 13
#define BTN 10

#define BTN_PRESSED true /* USER BUTTON was pressed */

bool btn_state = !BTN_PRESSED;
bool led_state = LOW;
int count = 0;

void count_up()
{
  count++;
  Serial.println(count);
}

void setup() {
  // put your setup code here, to run once:
  pinMode(LED, OUTPUT);
  pinMode(BTN, INPUT);
  Serial.begin(115200);
}

void loop() {
  // put your main code here, to run repeatedly:

  if (!(digitalRead(BTN)))  // LOW 
  {
      btn_state = BTN_PRESSED;
      delay(50); // debounce button
  }
  else  // BTN -> HIGH 
  {
      if (BTN_PRESSED == btn_state)
      {
        led_state = !led_state;
        digitalWrite(LED, led_state);
        count_up();
      }
      btn_state = !BTN_PRESSED;
      delay(50); // debounce button
  }
}

```
