Yes, you can use Windows Terminal to connect to a switch via a COM port to USB converter, but it requires some setup. Here's how you can do it:

1. **Using PowerShell**:
   - Open Windows Terminal and select PowerShell.
   - Use the following commands to interact with the COM port:

     ```powershell
     $port = new-Object System.IO.Ports.SerialPort COMX,9600,None,8,one
     $port.Open()
     $port.WriteLine("Your Command Here")
     $port.Close()
     ```

     Replace `COMX` with your actual COM port (e.g., `COM3`) and adjust the baud rate and other parameters as needed.

2. **Using SimplySerial**:
   - Install a tool like [SimplySerial](https://mikecoats.com/serial-windows-terminal/) that integrates with Windows Terminal.
   - Configure it to connect to your COM port by adding a profile in Windows Terminal for SimplySerial.

3. **Using WSL (Windows Subsystem for Linux)**:
   - If you have WSL1 installed, you can use Linux tools like `screen` to connect to the COM port. For example:

     ```bash
     screen /dev/ttyS4 9600
     ```

     Replace `/dev/ttyS4` with the corresponding COM port.

These methods allow you to bypass PuTTY and use Windows Terminal for serial communication. Let me know if you'd like more detailed instructions for any of these options!Yes, you can use Windows Terminal to connect to a switch via a COM port to USB converter, but it requires some setup. Here's how you can do it:

1. **Using PowerShell**:
   - Open Windows Terminal and select PowerShell.
   - Use the following commands to interact with the COM port:

     ```powershell
     $port = new-Object System.IO.Ports.SerialPort COMX,9600,None,8,one
     $port.Open()
     $port.WriteLine("Your Command Here")
     $port.Close()
     ```

     Replace `COMX` with your actual COM port (e.g., `COM3`) and adjust the baud rate and other parameters as needed.

2. **Using SimplySerial**:
   - Install a tool like [SimplySerial](https://mikecoats.com/serial-windows-terminal/) that integrates with Windows Terminal.
   - Configure it to connect to your COM port by adding a profile in Windows Terminal for SimplySerial.

3. **Using WSL (Windows Subsystem for Linux)**:
   - If you have WSL1 installed, you can use Linux tools like `screen` to connect to the COM port. For example:

     ```bash
     screen /dev/ttyS4 9600
     ```

     Replace `/dev/ttyS4` with the corresponding COM port.

In WSL2, COM ports from Windows are typically mapped to `/dev/ttyS<N>` in Linux, where `<N>` corresponds to the COM port number minus 1. For example, if your USB-to-COM converter is using `COM10` in Windows, it would usually translate to `/dev/ttyS9` in WSL2.

However, WSL2 doesn't natively support direct access to serial ports. To enable this, you can use a workaround by sharing the USB device with WSL2 using the `usbipd` tool. Here's how you can do it:

1. **Install USBIPD-WIN**:
   - Open PowerShell as an administrator.
   - Install the tool by following the instructions [here](https://askubuntu.com/questions/1461302/i-need-help-connecting-serial-ports-to-ubuntu-in-wsl).

2. **Bind the USB Device**:
   - Use `usbipd list` to find the USB device associated with your COM port.
   - Bind the device using `usbipd bind --busid <bus-id>`.

3. **Attach the Device in WSL2**:
   - In WSL2, attach the USB device using `usbipd attach --wsl --busid <bus-id>`.

4. **Access the Serial Port**:
   - Once attached, the device should appear as `/dev/ttyUSB0` or similar in WSL2.

Let me know if you'd like more detailed guidance on any of these steps!
