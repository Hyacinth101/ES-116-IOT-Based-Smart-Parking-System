## Working of the Smart Parking System 
The smart parking system operates using a combination of infrared (IR) sensors, an Arduino Uno microcontroller, an LCD display with I2C interface, and a servo motor. The system is designed to monitor the entry and exit of vehicles in real time, update slot availability dynamically, and control gate movement based on current occupancy.

At the core of the system are two IR sensors—one positioned at the entrance and one at the exit. When a vehicle approaches the entry point, the IR sensor detects a disruption in infrared reflection. This signal is passed to the Arduino, which checks the current availability of parking slots through an internally maintained counter.

If slots are available, the system triggers the servo motor to rotate and open the gate, allowing vehicle access. The slot count is then decremented, and the updated value is displayed on the LCD. In the case of a full lot, the gate remains closed and a "Parking Full" message is shown.

Similarly, when a vehicle exits, the second IR sensor detects the motion and prompts the Arduino to increment the slot count. The servo motor opens the gate temporarily to permit the exit, and the display is updated to reflect the new availability.

To ensure accuracy, the logic uses two flag variables (flag1 and flag2) to differentiate between active entry and exit processes, thus avoiding simultaneous sensor conflicts and double counts. Small time delays are introduced in the code to debounce the IR signals, preventing false triggers due to rapid environmental changes or partial obstructions.

Although the system uses polling (continuous checking) instead of hardware interrupts, the logic is structured to behave in an interrupt-responsive manner—ensuring near-instantaneous gate operation without system lag.

A Flow Chart for explanation: 
![image](https://github.com/user-attachments/assets/fdc61973-b4c7-40b8-9752-b51fc4b80bde)



