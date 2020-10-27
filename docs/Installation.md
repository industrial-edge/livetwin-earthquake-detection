# LiveTwin application example 


- [LiveTwin application example](#livetwin-application-example)
  - [Configure PLC project](#configure-plc-project)
  - [Export Simulink model](#export-simulink-model)
  - [Import the model to LiveTwin](#import-the-model-to-livetwin)
    - [Create template](#create-template)
    - [Create LiveTwin project](#create-livetwin-project)


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

