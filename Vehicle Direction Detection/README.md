# Vehicle Direction Determination

## Aim ##
To create a Simulink model of Vehicle Direction Detection as per the Requirement data.

## General Overview ##
Identifying the direction of the vehicle is one of the important & diverse features in Autonomous driving & Advanced Driver Assistance Features. This particular sub-feature of identifying the direction of vehicle is basically identifying the direction the vehicle is taking based on the camera input.
Camera reads the road signs & stores into its memory with unique values for left turn, right turn & straight drive. Depending on the direction it is taking, final indication is given to the driver – as an indication if he is driving in the recommended direction or not.
Vehicle Direction Determination can also be coupled along - side features like GPS systems to identify whether the vehicle is reaching its destination in an optimized manner. This sub feature can also be used along with Lane Detection, Highway Warning, Ramp Entry / Exit in Wrong Way Detection etc.

## Requirement - 1 ##
* Steering wheel input as yaw rate (Signal name: SteeringWheel_YawDegreeInput) is the input for this system.
* This is compared against 3 angular values, one each for left turn, right turn & straight drive (Calibration Values: Right_Turn_AngularLimit, Left_Turn_AngularLimit, Straight_Drive_Steering_Angle) to say which specific direction the steering wheel is turning towards.
* Use switch blocks to compare & develop this requirement. Keep this requirement in a subsystem & output of this requirement is a local signal (Signal Name: Vehicle_Turn_Status).

## Requirement – 2 ##
* Keep this requirement as a separate subsystem. Inputs to this requirement are local signal from requirement 1 (Signal Name: Vehicle_Turn_Status) & an input signal from camera (Signal Name: CameraInput_RoadSign), which confirms the occurrence of a road sign.
* Signal Vehicle_Turn_Status is compared against calibration values (Calibration Values: RightTurn_RoadSign, LeftTurn_RoadSign, Straight_RoadSign), if each of them is found equal, then each of the three corresponding output is compared against the camera input signal,
* Using a logical operator block, only one among them is finally given as output signal (Signal Name: Vehicle_Direction_Indicator).
 
This repository includes the following files for the project 'Vehicle Direction Determination'.
* .slx 	- Simulink model
* .sldd - Simulink Data Dictionary
* .docx - Project report