# HISPlayer visionOS 180 Video MR Sample

## Verify the visionOS Unity package

Please, verify you have installed the **com.unity.xr.visionos** package. Open the window **Window > Package Manager** located in the upper side of the screen and look for the package. In the case you haven't installed it yet, please, refer to [Install the visionOS Unity package](https://hisplayer.github.io/UnityVisionOS-SDK/#/setup-guide?id=install-the-visionos-unity-package)

<p align="center">
<img width=70% alt="image" src="https://github.com/HISPlayer/UnityVisionOS-SDK/assets/47497948/01bc480f-186f-47f4-a550-259ee825f94c">
</p>

## Import sample package

Please, download the sample here -> [**HISPlayer visionOS 180 MR Sample**](https://downloads.hisplayer.com/Unity/visionOS/HISPlayer_visionOS_180_MR_Sample.unitypackage) 
(no need to download it if you have received it in the email).

Importing the package is the same as importing other normal packages in Unity. Select the downloaded package and import it.

- **Assets > Import Package > Custom Package > HISPlayer_visionOS_180_MR_Sample.unitypackage**

<p align="center">
  <img width=50% src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/9cddf00f-9abc-4075-9bc2-ba278b92a7f9">
</p>

## Import HISPlayer SDK
If you have not imported HISPlayer SDK yet, please follow the [Quickstart Guide](https://hisplayer.github.io/UnityVisionOS-SDK/#/setup-guide).

## HISPlayer Sample configuration

- Complete the configuration for visionOS ->  [**Configure Unity for visionOS**](https://hisplayer.github.io/UnityVisionOS-SDK/#/setup-guide?id=_12-configure-unity-for-visionos)
  - To deploy for VisionPro device, please refer to the following configuration : [**Deploy for VisionPro Device**](https://hisplayer.github.io/UnityVisionOS-SDK/#/setup-guide?id=deploy-for-apple-vision-pro-device)
  - To deploy for VisionPro simulator, please refer to the following configuration : [**Deploy for VisionPro Simulator**](https://hisplayer.github.io/UnityVisionOS-SDK/#/setup-guide?id=deploy-for-apple-vision-pro-simulator)

- Open the scene **Assets/HISPlayerSample/Scenes/HISPlayer180MRSample.unity**

<p align="center">
  <img width=60% src="https://github.com/HISPlayer/UnitySamples/assets/47497948/5fecde52-3f95-4e1d-b048-f10af9be474a">
</p>

- Import TextMesh Pro Essential

- If you received a license key from HISPlayer, input the license key through the Inspector.
  - **HISPlayerController** GameObject -> **HISPlayer180MRController** component -> **License Key**

<p align="center">
  <img width=80% alt="image" src="https://github.com/HISPlayer/UnitySamples/assets/47497948/e2904071-ef2c-41ba-be67-267392a0f8af">
</p>

- Open **File** > **Build Settings** > **Add Open Scenes**. 

<p align="center">
  <img width=70% src="https://github.com/HISPlayer/UnitySamples/assets/47497948/e1a03f51-7dc8-4fad-9b26-c7051ecfe845">
</p>

- Review that the scene is correctly configured. Please, open **Player Settings > XR Plug-in Management > Apple visionOS > App Mode** and select:
   - **Mixed Reality - Volume or Immersive Space** to enable Mixed Reality mode.

- Build and Run

To check how to set up the SDK and API usage, please refer to:
  
  - **Assets/HISPlayerSample/Scripts/HISPlayer180MRController.cs** and **HISPlayerController GameObject** in the Editor.

## Add/Remove Streams and URLs
In order to add/remove streams and URLs, please refer to the component **HISPlayer180MRController** attached to the **HISPlayerController GameObject** in the **Inspector** within the **HISPlayer180MRSample.unity** scene. 

### Add/Remove Streams

You can add/remove streams by pressing the buttons **+/-** in the **Multi Stream Properties list**. Once a new stream is added, please, select the **RenderTexture mode** and the **RenderTexture surface** where you want to display your videos. 

<p align="center">
  <img width=70% alt="streams" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/f0a1521d-807a-48f5-893e-58135516b37e">
</p>

<p align="center">
  <img width=70% alt="render-mode" src="https://github.com/HISPlayer/UnitySamples/assets/47497948/4dd7a4e6-5c46-4b09-9f1e-a76848299657">
</p>

### Change Default URL
To change the default video URL using your own URL, please replace the element value with your own URL in the **URL list** of the stream you want to modify.

<p align="center">
  <img width=60% alt="replace-url" src="https://github.com/HISPlayer/UnitySamples/assets/47497948/230d4396-77ca-44e0-ae0f-7edfe6996b2e">
</p>

### Add/Remove URLs

You can add/remove URLs by selecting one element from the **Multi Stream Properties list** and then pressing the buttons **+/-** in the **Url list**. 

<p align="center">
  <img width=70% alt="add-url" src="https://github.com/HISPlayer/UnitySamples/assets/47497948/fa99bc29-0cc2-40c0-b47d-0f520d5b9603">
</p>

### Change video content at runtime

For changing the content of the videos, please refer to **[ChangeVideoContent](https://hisplayer.github.io/UnityVisionOS-SDK/#/hisplayer-api?id=protected-void-changevideocontentint-playerindex-int-urlindex)** API.

## HISPlayer 180/360 Resources
Using the MR mode, the Panoramic shaders like or the Skybox effects are not supported. 
In the sample we provide the Blender model, the material, the render texture and the shader graph
to render the 180 video on a semisphere. 
In the case you want to use 360 videos, please consider making an entire sphere with Blender. 

Please refer to:
  
* **Assets/HISPlayer/Resources/visionOS-MR/180MRVideoSurface.blend**
  * In the case you want to check or modify this file, you will need to download [Blender](https://www.blender.org/).
* **Assets/HISPlayer/Resources/visionOS-MR/HISPlayerVisionOSMRMaterial.mat**
* **Assets/HISPlayer/Resources/visionOS-MR/HISPlayerVisionOSMRRenderTexture.rendertexture**
* **Assets/HISPlayer/Resources/visionOS-MR/HISPlayerVisionOSMRShader.shadergraph**
