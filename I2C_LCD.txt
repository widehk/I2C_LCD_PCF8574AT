/* Demonstration sketch for PCF8574T I2C LCD Backpack 
Uses library from https://bitbucket.org/fmalpartida/new-liquidcrystal/downloads GNU General Public License, version 3 (GPL-3.0) */
#include <Wire.h>
#include <LCD.h>
#include <LiquidCrystal_I2C.h>
// lcd_Addr, EN, RW, RS, D4, D5, D6, D7 
LiquidCrystal_I2C  lcd(0x38,2,1,0,4,5,6,7); // 0x27 is the I2C bus address for an unmodified backpack

void setup()
{
  // activate LCD module
  lcd.begin (16,2); // for 16 x 2 LCD module
  lcd.setBacklightPin(3,POSITIVE);
  lcd.setBacklight(HIGH);
}

void loop()
{
  lcd.home (); // set cursor to 0,0
  lcd.print("WIDE.HK-PCF8574A"); 
  lcd.setCursor (0,1);        // go to start of 2nd line
   lcd.print("I2C:0x38 (0x27!)"); 
  //lcd.print(millis());
  delay(1000);
  lcd.setBacklight(LOW);      // Backlight off
  delay(250);
  lcd.setBacklight(HIGH);     // Backlight on
  delay(1000);
}