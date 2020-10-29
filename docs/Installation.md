# LiveTwin application example 


- [LiveTwin application example](#livetwin-application-example)
  - [Configure PLC project](#configure-plc-project)
  - [Export Simulink model](#export-simulink-model)
  - [Import the model to LiveTwin](#import-the-model-to-livetwin)
    - [Create template](#create-template)
    - [Create LiveTwin project](#create-livetwin-project)
  - [Simulation configuration](#simulation-configuration)
    - [Databus configuration](#databus-configuration)
    - [S7 Connector configuration](#s7-connector-configuration)


## Configure PLC project
1) Open TIA portal and open the project: [TIA project](../src/Shock_detection1500.zip). 

2) Download the PLC program to PLC (It is also possible to use PLCSIM advance).

3) Feel free to simulate and configure provided HMI (*HMI_TP700/Screens/Applications/51_LiveTwin*) to control the PLC program. 
  


## Export Simulink model 

*Note: Matlab 2019b is used in this example*

Documentation for exporting your own Simulink model can be found here: [documentation](export_simulink_model.md)

The Simulink model for this use case is already in this repository: [Shock-sensor-model](../src/shock_sensor.zip)

## Import the model to LiveTwin 

*Prerequisities:*
 - *LiveTwin and Flow Creator applications are running on edge device*



### Create template
1) Open LiveTwin UI and go to the "LiveTwin studio" section located in the left main menu.

2) Go to the Libraries are and click on the "plus" button to add a template. New tab pop up in the working area. 

<img src="docs/graphics/plus_button.PNG" width="300"/>

3) Navigate to the "New Template" area and fill the form: 
  - Choose a "Name" for your template
  - Select the "Model Type" (in this case Simulink)
  - Browse in the"Model File" for the exported .zip file of the Simuling project. You can find it here: [livetwin template](src/shock_sensor.zip)

<img src="docs/graphics/new_template.PNG" width="600"/>

4) Click "Save". The new template is generated. 

### Create LiveTwin project 

1) Go to the "Projects" section in the "LiveTwin studio" menu and click on the "plus" button to add project. 
   
<img src="docs/graphics/add_project.PNG" width="300"/>

2) Navigate to the "Projects" area and fill the following information: 
  - Select your "Template"
  - Select "LiveTwin" as a "Project Type"
  - Give the project a name 
  - Choose "Simulation Step" and "Project Cyclic Time" based on your reguirements

<img src="docs/graphics/new_project.PNG" width="700"/>

3) Click "Save&Close". The new LiveTwin project is created. 

## Simulation configuration

In order to finish this automation task, we need to read/write data from/to PLC. In this use case, we will use S7 Connector system application to establish connection with PLC using S7 and OPC comunnication protocols. S7 connector is also connected to Databus and LiveTwin can then access the data from Databus via MQTT protocol. In order to establish this infrastructure, follow these instructions: 


### Databus configuration
1) Go to the "My Installed Apps" section of the Industrial Edge Management System. 
2) Click on the "IE Databus" application icon. 
3) Click on the "Update Configuration" button, new configuration file appears. 
4) Select you edge device and click on "Launch Configurator", Databus Configuration window appears. 


5) Configure the following information: 
 ```txt
   User name: edge 
   Password: edge 
   Topic: ie/# 
   Permission: Publish and Subscribe

   ```
<img src="docs/graphics/databus.gif" width="1000"/>

### S7 Connector configuration
For pefrormance purposes, we will use S7 communication protocol for high frequency data simulating vibrations and OPC UA protocol for low frequency data. In order to establish connection with PLC, follow these instructions: 

1) Go to the "My Installed Apps" section of the Industrial Edge Management System. 
2) Click on the "SIMATIC S7 Connector" application icon. 
3) Click on the "Update Configuration" button, new configuration file appears.
4) Click on "Add Data Source" button and select "Simatic S7 protocol". 
5) Click the "plus" button on the rifht side of the data source to add a tag and input: 
  ```txt
    Name : accy 
    Adress: %DB3.DBD2
    Data Type: Real
    Acquisition Cycle: 100 ms
    Acquisition Mode: CyclicOnChange
    Access Mode: Read
  ```