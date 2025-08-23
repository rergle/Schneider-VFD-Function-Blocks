ATV Series VFDs with Allen-Bradley AOI Instructions

# ATV Series VFDs with Allen-Bradley AOI Instructions

  ATVxxx / EthernetIP — Control with status and fault handling
  This folder contains a function block library for controlling Schneider Electric ATV Series VFDs via EthernetIP.
  These blocks were designed for integration with Allen-Bradley PLCs and provide control, status, and
  fault handling for the ATVxxx Series drives.

## Folder Structure

- **ATVxxx-Allen-Bradley-AOIs*.*/**
  -`ATV6xx-EthernetIP-AOI`: Addon Instruction
- -`ATV9xx-EthernetIP-AOI`: Addon Instruction
- -`ATV320-EthernetIP-AOI`: Addon Instruction
- -`ATV340-EthernetIP-AOI`: Addon Instruction
- -`SoMove-Files-Allen-Bradley`: VFD setup files
- -`ATVxxx-Studio5000-Example`: Example PLC program

## Function Blocks Overview — *ATVxxx-EthernetIP***

<img width="422" height="253" alt="blockAB" src="https://github.com/user-attachments/assets/a71e4437-e0f6-4b0e-a228-71d08dae0a96" />

- ***Inputs:***
- `I_Run_Forward` : BOOL — Starts the drive forward - Maintained Input
- `I_Run_Reverse` : BOOL — Starts the drive reverse - Maintained Input
- `I_Fault_Reset` : BOOL — Reset drive faults - Momentary Input
- `I_Comm_Fault`   : BOOL — Comm interrupt Bit
- `I_Speed_Referance_Hz` : REAL — Setpoint for desired speed in Hz `00.0Hz to 60.0Hz`
- ***Input/Outputs:***
- `IQ_ATV_Process_Input_Data`   : INT[6] — VFD Input registers that are Read from the VFD, example.."ATV320:I"
- `IQ_ATV_Process_Output_Data` : INT[6]  — VFD Output registers that are Writen to the VFD, example.."ATV320:O"
- `IQ_Fault_Message` : STRING — Create a Local or Cotroller Tag to store the VFD Fault message
- `IQ_Drive_Status`   : STRING — Create a Local or Cotroller Tag to store the VFD Status message
- ***Outputs:***
- `Q_ACC_Speed_Hz`   : REAL — Output frequency of the VFD in Hertz
- `Q_Motor_Current` : REAL — Output Current of the VFD in Amps
- `Q_Fault_Code`      : INT — Last Fault that occured
- `Q_Motor_Torque`   : REAL — Motor Torque in %
- `Q_Motor_Voltage` : INT — The amount of Voltage the VFD is supplying the motor
- `Q_Drive_Ready`         : BOOL — True VFD is Running
- `Q_Drive_At_Speed`    : BOOL — True Motor is at speed setpoint.
- `Q_Drive_Faulted`      : BOOL — True if VFD is Faulted
- `Q_Drive_Over_Speed` : BOOL — True if VFD is in overspeed condition
- `Q_Comm_Fault `         : BOOL — True if Communication is interrupted
- **Features:**

## Fault and Status Handling

This function blocks maps drive status and fault codes to descriptive messages, making
diagnostics easier. Fault reset logic is included for automatic or manual recovery.

- Decodes status and fault codes to readable messages
- Handles drive enable/disable, run, stop, and fault reset logic

## SoMove File

The files in `SoMove-Files-Allen-Bradley/` are SoMove project files for configuring the ATVxxx
series drives for use with EthernetIP, using Static IP addressing.
Use the SoMove file to help configure your ATVxxx drive as needed.

- SoMove Download: [https://www.se.com/us/en/work/products/explore/somove/](https://www.se.com/us/en/work/products/explore/somove/)
- SoMove Cable for connecting with ATV Drives: [TCSMCNAM3M002P](https://www.se.com/us/en/product/TCSMCNAM3M002P/connection-cable-usb-to-rj45-tesys-t-for-connection-between-pc-and-drive/)
- EthernetIP communication module for ATV320 & ATV340 Drives: [VW3A3616](https://www.se.com/us/en/product/VW3A3616/communication-module-modbus-tcp-and-ethernet-ip-altivar-10-or-100mbps-2-x-rj45-connectors/)
- EthernetIP communication module for ATV630 Drives: [VW3A3720](https://www.se.com/us/en/product/VW3A3720/communication-module-ethernet-ip-modbus-tcp-10-or-100mbps-2-x-rj45-connectors/)

### ATV320 IO-Mode Setup with SoMove (Video)

[![Watch the video](https://img.youtube.com/vi/AHr30IkEi-s/0.jpg)](https://youtu.be/AHr30IkEi-s)

### ATV630 IO-Mode Setup with SoMove (Video)

[![Watch the video](https://img.youtube.com/vi/aUsC99xA9SU/0.jpg)](https://youtu.be/aUsC99xA9SU)

**Studio5000 Setup**

1. Right click on `Ethernet` in the Device Tree and click `New Module...`
2. Search for and select `Generic EtherNet Module`
3. In the `General` tab enter the following parameters:

- Name: "the name of your VFD"
- Comm Format: Data - INT

**ATV320 or ATV340**
`<img width="551" height="341" alt="ATV320" src="https://github.com/user-attachments/assets/b97b5226-227f-4f88-bf31-123d93791d27" />`

 **ATV6xx or ATV9xx**
`<img width="550" height="342" alt="ATV630" src="https://github.com/user-attachments/assets/ede6c55a-ecd4-4582-ad40-e95ed3c52d86" />`

- IP Adrress: `your VFD IP address`

4. Click OK and add the device
5. Right click on the Add-On Instructions folder in the device tree select `Import Add-On Instruction`
6. Select the `ATV***_v*.L5X` file and add to project.
7. Drag a new ATV_xxx AOI onto the ladder editor, tag the block, download, and go online.

### ATV320 IO-Mode Add-On Instruction Setup In Studio5000 (Video)

[![Watch the video](https://img.youtube.com/vi/CvI5QliW0fY/0.jpg)](https://youtu.be/CvI5QliW0fY)

### ATV630 IO-Mode Add-On Instruction Setup In Studio5000 (Video)

[![Watch the video](https://img.youtube.com/vi/NJGgFqq3x_s/0.jpg)](https://youtu.be/NJGgFqq3x_s)

**Author**

- [rergle@gmail.com](mailto:rergle@gmail.com)

**License**
This project is provided as‑is for engineering and educational use.

  © 2025 rergle
