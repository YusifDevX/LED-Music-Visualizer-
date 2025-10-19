#include <Adafruit_NeoPixel.h>
#define PIN 6
#define NUM_LEDS 30
#define mic A0

Adafruit_NeoPixel strip(NUM_LEDS, PIN, NEO_GRB + NEO_KHZ800);

void setup() {
  strip.begin();
  strip.show();
}

void loop() {
  int sound = analogRead(mic);
  int brightness = map(sound, 0, 1023, 0, 255);

  for(int i=0; i<NUM_LEDS; i++){
    strip.setPixelColor(i, strip.Color(brightness, 0, 255-brightness));
  }
  strip.show();
}
