# Adaptive Cruise Control

## Aim ##
To create a Simulink model of Adaptive Cruise Control as per the Requirement data.

## General Overview ##
Adaptive Cruise Control Feature for passenger cars allows the host vehicle to adapt to the speed in line with the flow of traffic. Driving in heavy traffic or keeping a safe distance to the preceding vehicle calls for a high level of concentration. The Adaptive Cruise Control feature can reduce the stress on the driver by automatically controlling the vehicle speed & maintaining a predefined minimum distance to the preceding vehicle. As a consequence, the driver enjoys more comfort & can concentrate on the road little better.
A radar sensor is usually at the core of the Adaptive Cruise Control. Installed at the front of the vehicle, the system permanently monitors the road ahead. As long as the road ahead is clear, cruise control feature maintains the speed set by the driver. If the system spots a slower vehicle within its detection range, it gently reduces speed by releasing the accelerator or actively engaging the brake control system. If the vehicle ahead speeds up or changes lanes, the cruise control automatically accelerates to the driver’s desired speed.
Standard Adaptive Cruise Control can be activated from speeds of around 30 km/h (20 mph) upwards and supports the driver, primarily on cross-country journeys or on freeways. The cruise control stop & go variant is also active at speeds below 30 km/h (20 mph). It can maintain the set distance to the preceding vehicle even at very low speeds and can decelerate to a complete standstill. When the vehicle remains stopped longer, the driver needs only to reactivate the system, for example by briefly stepping on the gas pedal to return to cruise control mode. In this way, cruise control stop & go supports the driver even in heavy traffic and traffic jams.
Since Adaptive Cruise Control is a comfort and convenience system, brake interventions and vehicle acceleration only take place within defined limits. Even with Adaptive Cruise Control switched on, it remains the driver’s responsibility to monitor the speed and distance from the vehicle in front.

## Objective ##
* Developing Adaptive Cruise Control feature as per the Requirement Document using MATLAB Simulink.
* Follow all the MBD related processes: Requirement Tagging & Traceability, SLDD creation, Configuration Parameter changes, Model Advisor check & Code Generation.
* In Configuration Parameters: enable “Support Floating Numbers” under Code Generation settings.
* Use Embedded Coder to generate the code.
* If choosing code generation, Storage class for Input signals: ImportedExtern; Storage class for Output signal: Export to File; Storage class for local signals: localizable; Storage class for calibration signals: Const.
* Choose sample time for all signals as 0.01s

## Requirement 1– Lead Vehicle ##
* Lead Vehicle is a vehicle which is driving in the road ahead of our drive vehicle. Two input signals (Signal Name: CameraInput_LeadVehicle & RadarInput_LeadVehicle).
* Ideally sensor fusion techniques will be deployed to process & analyze data from camera & radar. For complexity reasons, let’s not adapt to any such algorithms.
* We can simply add both the radar & camera inputs & the corresponding output is read as Speed profile output (Signal Name: LeadVehicle_Speed).
* Speed data of the lead vehicle is critical in implementing the Adaptive Cruise Control algorithm.

## Requirement 2 – Drive Vehicle ##
* Drive Vehicle is the vehicle driven by the user & this is the vehicle which has ACC algorithm in it.
* Like the Lead Vehicle, Drive Vehicle algorithm also has 2 input signals (Signal Name: CameraInput_DriveVehicle, RadarInput_DriveVehicle) & one signal coming as an Input to this subsystem (Signal Name: Acceleration_Mode) – three inputs into this requirement in total.
* Like the above requirement, sensor fusion techniques will also be deployed here, for complexity reasons we are ignoring them.
* Two output signals come from this subsystem (Signal Name: DriveVehicle_Speed & LeadVehicle_Detected).
* Signal DriveVehicle_Speed is summation of three input signals mentioned above & LeadVehicle_Detected is renamed from Input Signal RadarInput_DriveVehicle by mere use of Signal Conversion block.

## Requirement 3 – Adaptive Cruise Control Algorithm ##
* Adaptive Cruise Control feature has 3 major modes of operation: OFF Mode, STANDBY Mode & ON Mode. This particular requirement has to be implemented as state machine logic in Simulink.
* The input signals to this state machine system are (Signal Name: Time_Gap, Set_Speed, Set_Gap, CruiseSwitch, SetSwitch).
* Also, the output signals (Signal Name: DriveVehicle_Speed & LeadVehicle_Detected) from requirement-2 is fed back as an input signal into this state machine block.
* Additionally, output signal (Signal Name: LeadVehicle_Speed) from requirement-1 is given as an input signal to this state machine block as well.
* Output from this subsystem is a signal (Signal Name: Acceleration_Mode) which governs the vehicular speed of the drive vehicle which automatically adjusts its speed & velocity to match the lead vehicle.

#### Note: Additional sub requirements for requirement - 3 are mentioned in detail in the project portfolio as well as the project report. #### 

### Repo Files ###
This repository includes the following files for the project 'Vehicle Direction Determination'.
* .slx 	- Simulink model
* .sldd - Simulink Data Dictionary
* .docx - Project report

### Project Portfolio ###
Project Portfolio for Vehicle Direction Determination: 






