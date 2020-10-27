# Export Simulink model

To export Simulink model and run it on edge device you have to follow these steps: 

1) Open your simulink project.

<img src="docs/graphics/Project.PNG" width="700"/>

2) Go to the "Apps" Section in the top menu and select "Simulink Coder". New tap opens. 


<img src="docs/graphics/point2.PNG" width="500"/>

3) Go to the "CODE" tab and in the "Generic C Code" section choose "Generic C++ code". 



<img src="docs/graphics/point02.PNG" width="400"/>

4) Go to "Settings", new window with configuration parameters opens. 

5) Click on "Code Generation" section and select the folowing options: 
  - Activate "Generate code only"
  - Activate "Package code and artifacts"
  - Optional: "Zip file name"
  - Select the "Toolchain"

<img src="docs/graphics/code_gen.PNG" width="600"/>
 
6) Go to the "Interface" option in the "Code Generation" section and select: 
  - Activate all checkboxes in the "Generate C API" option


<img src="docs/graphics/interface.PNG" width="600"/>

  - For Advanced parameters: 
    - Disable "MAT-file logging"


<img src="docs/graphics/interface_advanced.PNG" width="600"/>


7) Go to the "Hardware Implementation" and do the following: 
  - In the "Device vendor" option choose "Intel"
  - Activate "Support long long" checkbox
  - Activate "Test hardware in the same as production hardware"


<img src="docs/graphics/hardware.PNG" width="600"/>


8) Click "Ok" and then in the "Generate Code" drop down list select "Build"

![](docs/graphics/build.PNG)

9) The .zip file is created and prepared for import to LiveTwin 