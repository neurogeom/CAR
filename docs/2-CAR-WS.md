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
    > <details>
    > <summary>Screenshots</summary>
    >
    > ![Entering](../assets/ws_entering.png)
    > </details>
2. Configuration CAR
    1. Click `Collaborate` - `Config`;
    2. Enter the server configuration;
    3. Login to CAR by enter the username and password.
    > <details>
    > <summary>Screenshots</summary>
    >
    > ![Configuration](../assets/ws_config.png)
    >
    > ![Authorization](../assets/ws_auth.png)
    > </details>
3. Open image and load annotation
    1. Click `File` - `Open TeraFly Image(3-5D)` and choose an image;
    2. Users can collaborate in one room each other by download the same ano file.
    > <details>
    > <summary>Screenshots</summary>
    >
    > ![Load Ano 1](../assets/ws_load_ano_1.png)
    >
    > ![Load Ano 2](../assets/ws_load_ano_2.png)
    > </details>
4. Collaborators can annotate by using short cuts
    - **Alt-B**: invoke the curve drawing function using serial BBoxes;
    - **Alt-C**: invoke the multiple neuron-segments Connection function;
    - **Alt-D**: invoke the multiple neuron-segments Deleting function;
    - **Alt-S**: invoke the multiple neuron-segments Splitting/breaking function.
