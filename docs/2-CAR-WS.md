# CAR-WS

CAR-WS, which are built upon the foundation of the Vaa3D system, while incorporating a cloud server and enabling collaborative capabilities. And it also take several features from [Vaa3D](http://www.vaa3d.org/), refers the [User Manual](https://github.com/Vaa3D/Vaa3D_Wiki/wiki/UserManual.wiki) for details.

## Installation

The workstation client and the VR client share the same software. For Windows system user, please download and unzip the releases and click on `vaa3d_CAR.exe` to run the software. For others system user, please build CAR-VR-WS from scratch.

<details>
<summary>Build CAR-WS-VR from scratch</summary>

CAR-WS and CAR-VR clients share the same codebase based on Qt 4.7.3. You can refer to the following tutorials to compile.

- [On Linux](https://github.com/Vaa3D/Vaa3D_Wiki/wiki/Build-Vaa3D-on-Linux): Build CAR-VR-WS with MSVC and QMake.
- [On Windows](https://github.com/Vaa3D/Vaa3D_Wiki/wiki/Build-Vaa3D-on-Windows-(QMake)): Build CAR-VR-WS with LLVM and QMake.
- [On Mac](https://github.com/Vaa3D/Vaa3D_Wiki/wiki/Build-Vaa3D-on-Mac-OS): Build CAR-VR-WS with GCC and 
</details>

## Step-by-Step Guide

1. Enter the CAR collaborate mode, `Advanced` - `Big-Image-Data` - `CAR-WS`

    <details>
    <summary>Screenshots</summary>

    ![Entering](../assets/ws_entering.png)
    </details>

2. Configuration CAR

    1. Click `Collaborate` - `Config`;

    2. Enter the server configuration;

    3. Login to CAR by enter the username and password.

       We have provided two available test users. The usernames and passwords are as follows:

       1. Username: testuser Password: 123456
       2. Username: testuser02 Password: 123456
    <details>
    <summary>Screenshots</summary>

    ![Configuration](../assets/ws_config.png)

    ![Authorization](../assets/ws_auth.png)
    </details>

3. Open image and load annotation

    1. Click `File` - `Open TeraFly Image(3-5D)` and choose an image;
    2. Users can collaborate in one room each other by download the same ano file.
    <details>
    <summary>Screenshots</summary>

    ![Load Ano 1](../assets/ws_load_ano_1.png)

    ![Load Ano 2](../assets/ws_load_ano_2.png)
    </details>

    3. Choose any collaboration room (00029_P001_T01-S001_MFG_R0460_WY-20220415_GYC_03  (human brain neuron) or 18454-00019 (mouse brain neuron)) to enter the collaboration room.

4. Manually annotation in CAR

    Collaborators can annotate by using short cuts

    - **Alt-B**: invoke the curve drawing function using serial BBoxes;
    - **Alt-C**: invoke the multiple neuron-segments Connection function;
    - **Alt-D**: invoke the multiple neuron-segments Deleting function;
    - **Alt-S**: invoke the multiple neuron-segments Splitting/breaking function.

5. Auto reconstruction in CAR
   
   We use the neurons from the mouse brain as an example:
   
   1. In Step 3, click on "18454-00019" to enter the "18454-00019" collaboration room.

   2. Switch image resolution: You can double-click with the mouse to toggle between different image resolutions or right-click on a marker and select "Zoom-in to this selected marker location" to enter the highest resolution image. The mouse scroll wheel can also be used to zoom in or out to different image resolutions.

   3. Right-click on an image block (ensure there is a marker in the image block before using the automatic tracking algorithm), and the following menu options will appear:

      ![auto01](../assets/auto01.png)

   4. Click the "app2Convenient" button to initiate tracking, and the following results will appear.

      ![auto02](../assets/auto02.png)

#### How to use Data management system in CAR?

1. Click `Collaborate` - `Data Management Client` and invoke the data management system;

   <details>
   <summary>Screenshots</summary>

   ![ws_dbms_01](../assets/ws_dbms_01.png)
   </details>

2. Log into the data management system;

   <details>
   <summary>Screenshots</summary>

   ![ws_dbms_login](../assets/ws_dbms_login.png)
   </details>

3. Click on the "Import Swc File" button. In the pop-up window, select your morphology file and click "Import."

   <details>
   <summary>Screenshots</summary>

   ![ws_dbms_import_swc_01](../assets/ws_dbms_import_swc_01.png)

   ![ws_dbms_import_swc_02](../assets/ws_dbms_import_swc_02.png)
   </details>

4. Export data

   Select the file, right-click, and choose "Export Swc File" from the context menu. After a new window pops up, select the destination path to save the file, then click 'Export' to export the file to the specified directory.
   
   <details>
   <summary>Screenshots</summary>
   
   ![ws_dbms_export_swc_01](../assets/ws_dbms_export_swc_01.png)

   ![ws_dbms_export_swc_02](../assets/ws_dbms_export_swc_02.png)
   </details>

7. Version Control 

   1. Select the file, right-click, and choose "Version Control" from the context menu.
   
      <details>
      <summary>Screenshots</summary>

      ![version_control_00](../assets/version_control_00.png)
      </details>

   2. A new window will appear, allowing the user to specify any timestamp for exporting or reverting to  

      the reconstructed morphology using the 'Export' and 'Revert' buttons. This feature enables tracing back to historical reconstruction data at any desired moment.

      <details>
      <summary>Screenshots</summary>

      ![version_control_01](../assets/version_control_01.png)
      </details>

   3. Select "Export," and a new window will appear. In this window, users can view specific features of the exported morphology, including Swc Node Number, and choose the save path for the exported file.

      <details>
      <summary>Screenshots</summary>
      ![version_control_02](../assets/version_control_02.png)
      </details>

4. Select "Revert," and a new window will appear. In this window, users can revert the morphology in the desired timestamp.

   <details>
   <summary>Screenshots</summary>

​	![revert](../assets/revert.png)

​	</details>
