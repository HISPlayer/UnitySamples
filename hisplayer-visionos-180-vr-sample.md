# HISPlayer visionOS 180 VR Sample

## Verify the visionOS Unity package

Please, verify you have installed the **com.unity.xr.visionos** package. Open the window **Window > Package Manager** located in the upper side of the screen and look for the package. In the case you haven't installed it yet, please, refer to [Install the visionOS Unity package](https://hisplayer.github.io/UnityVisionOS-SDK/#/setup-guide?id=install-the-visionos-unity-package)

<p align="center">
<img width=70% alt="image" src="https://github.com/HISPlayer/UnityVisionOS-SDK/assets/47497948/01bc480f-186f-47f4-a550-259ee825f94c">
</p>

## Import sample package

Please, download the sample here -> [**HISPlayer visionOS 180 VR Sample**](https://downloads.hisplayer.com/Unity/visionOS/HISPlayer_visionOS_180_VR_Sample.unitypackage) 
(no need to download it if you have received it in the email).

Importing the package is the same as importing other normal packages in Unity. Select the downloaded package and import it.

- **Assets > Import Package > Custom Package > HISPlayer_visionOS_180_VR_Sample.unitypackage**

<p align="center">
  <img width=50% src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/9cddf00f-9abc-4075-9bc2-ba278b92a7f9">
</p>

## Import HISPlayer SDK
If you have not imported HISPlayer SDK yet, please follow the [Quickstart Guide](./setup-guide.md).

## HISPlayer Sample configuration

- Complete the configuration for visionOS ->  [**Configure Unity for visionOS**](https://hisplayer.github.io/UnityVisionOS-SDK/#/setup-guide?id=_12-configure-unity-for-visionos)
  - To deploy for VisionPro device, please refer to the following configuration : [**Deploy for VisionPro Device**](https://hisplayer.github.io/UnityVisionOS-SDK/#/setup-guide?id=deploy-for-apple-vision-pro-device)
  - To deploy for VisionPro simulator, please refer to the following configuration : [**Deploy for VisionPro Simulator**](https://hisplayer.github.io/UnityVisionOS-SDK/#/setup-guide?id=deploy-for-apple-vision-pro-simulator)

- Open the scene **Assets/HISPlayerSample/Scenes/HISPlayer180VRSample.unity**

<p align="center">
  <img width=60% alt="image" src="https://github.com/HISPlayer/UnitySamples/assets/47497948/d8b3dba6-0c51-44cf-9394-fd7ae2977bc1">
</p>

- Import TextMesh Pro Essential

- Input the license key through the Inspector.
  - **HISPlayerController** GameObject -> **HISPlayer180VRController** component -> **License Key**

<p align="center">
  <img width=80% alt="image" src="https://github.com/HISPlayer/UnitySamples/assets/47497948/5c8f6888-55fb-4e25-9c84-6bd72290939e">
</p>

- Open **File** > **Build Settings** > **Add Open Scenes**. 
<p align="center">
  <img width=70% alt="macos" src="https://github.com/HISPlayer/UnitySamples/assets/47497948/b4e903c2-2862-4730-a31b-785dd2ce44c1">
</p>

- Review that the scene is correctly configured. Please, open **Player Settings > XR Plug-in Management > Apple visionOS > App Mode** and select:
   - **Virtual Reality - Fully Immersive Space** for **HISPlayerSampleVR.unity**

- Build and Run

To check how to set up the SDK and API usage, please refer to:
  
  - **Assets/HISPlayerSample/Scripts/HISPlayer180VRController.cs** and **HISPlayerController GameObject** in the Editor.

## UI Demo
The UI components in the HISPlayer180VRSample.unity are fully modifiable. The sample is intended to show a comprehensive scene 
using the HISPlayer SDK to help demonstrate features such as play, pause, seek, etc. 

<p align="center">
  <img width=55% alt="image" src="https://github.com/HISPlayer/UnitySamples/assets/47497948/6eab9306-4b6b-4991-a3eb-eb73619e0d28">
</p>

<p align="center">
  <img width=90% alt="image" src="https://github.com/HISPlayer/UnitySamples/assets/47497948/9de1004b-81cd-4e78-b491-11038d976728">
</p>

## HISPlayer 180/360 Resources
Unity provides ways to configure how you will display your video content on the 180/360 environment. Please, refer to the following
Unity documentation to check what kind of settings you will need: [Unity Video Panoramic Tutorial](https://docs.unity3d.com/Manual/VideoPanoramic.html).

We provide the render texture, the material and the shader to configure the options of your video so please, refer to:
  
* **Packages/HISPlayer SDK/HISPlayer/Scripts/Shaders/HISPlayer360Shader.shader**
* 180 resources
  * **Packages/HISPlayer SDK/HISPlayer/Resources/Materials/HISPlayer180Material.mat** to check the 180 settings.
  * **Packages/HISPlayer SDK/HISPlayer/Resources/RenderTextures/HISPlayer180RenderTexture.rendertexture**.
* 360 resources
  * **Packages/HISPlayer SDK/HISPlayer/Resources/Materials/HISPlayer180Material.material** to check the 180 settings.
  * **Packages/HISPlayer SDK/HISPlayer/Resources/RenderTextures/HISPlayer180RenderTexture.rendertexture**.

In the case you want to use to 360 videos, please refer to the 360 resources listed above. 
In our sample we're using the following options for 180 videos: 

* **HISPlayer180Material.mat**
  * **Flip Vertically**: True
  * **Mapping**: Latitude Longitude Layout
  * **Image Type**: 180 Degrees
    * **Mirror on Back**: False
  * **3D Layout**: None

<p align="center">
<img width=70% alt="image" src="https://github.com/HISPlayer/UnitySamples/assets/47497948/ea2aefc6-cdf5-440b-ac1f-24d206456b89">
</p>

