# HISPlayer visionOS 180 Video VR Sample

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
If you have not imported HISPlayer SDK yet, please follow the [Quickstart Guide](https://hisplayer.github.io/UnityVisionOS-SDK/#/setup-guide).

## HISPlayer Sample configuration

- Complete the configuration for visionOS ->  [**Configure Unity for visionOS**](https://hisplayer.github.io/UnityVisionOS-SDK/#/setup-guide?id=_12-configure-unity-for-visionos)
  - To deploy for VisionPro device, please refer to the following configuration : [**Deploy for VisionPro Device**](https://hisplayer.github.io/UnityVisionOS-SDK/#/setup-guide?id=deploy-for-apple-vision-pro-device)
  - To deploy for VisionPro simulator, please refer to the following configuration : [**Deploy for VisionPro Simulator**](https://hisplayer.github.io/UnityVisionOS-SDK/#/setup-guide?id=deploy-for-apple-vision-pro-simulator)

- Open the scene **Assets/HISPlayerSample/Scenes/HISPlayer180VRSample.unity**

<p align="center">
  <img width=60% src="https://github.com/HISPlayer/UnitySamples/assets/47497948/296ba96c-2ac0-478e-9eb3-912fa01f0564">
</p>

- Import TextMesh Pro Essential

- Input the license key through the Inspector.
  - **HISPlayerController** GameObject -> **HISPlayer180VRController** component -> **License Key**

<p align="center">
  <img width=80% alt="image" src="https://github.com/HISPlayer/UnitySamples/assets/47497948/5c8f6888-55fb-4e25-9c84-6bd72290939e">
</p>

- Open **File** > **Build Settings** > **Add Open Scenes**. 

<p align="center">
  <img width=70% src="https://github.com/HISPlayer/UnitySamples/assets/47497948/1fa50bd4-48b0-4f16-80d5-8bbc08028f8d">
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

## Add/Remove Streams and URLs
In order to add/remove streams and URLs, please refer to the component **HISPlayer180VRController** attached to the **HISPlayerController GameObject** in the **Inspector** within the **HISPlayer180VRSample.unity** scene. 

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
Unity provides ways to configure how you will display your video content on the 180/360 environment. Please, refer to the following
Unity documentation to check what kind of settings you will need: [Unity Video Panoramic Tutorial](https://docs.unity3d.com/Manual/VideoPanoramic.html).

We provide the render texture, the material and the shader to configure the options of your video so please, refer to:
  
* **Packages/HISPlayer SDK/HISPlayer/Scripts/Shaders/HISPlayer360Shader.shader**
* 180 resources
  * **Packages/HISPlayer SDK/HISPlayer/Resources/Materials/HISPlayer180Material.mat** to check the 180 settings.
  * **Packages/HISPlayer SDK/HISPlayer/Resources/RenderTextures/HISPlayer180RenderTexture.rendertexture**.
  * **Packages/HISPlayer SDK/HISPlayer/Resources/Materials/HISPlayer180Material.mat**.

* 360 resources
  * **Packages/HISPlayer SDK/HISPlayer/Resources/Materials/HISPlayer360Material.material** to check the 180 settings.
  * **Packages/HISPlayer SDK/HISPlayer/Resources/RenderTextures/HISPlayer360RenderTexture.rendertexture**.
  * **Packages/HISPlayer SDK/HISPlayer/Resources/Materials/HISPlayer360Material.mat**.

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

### How to use 360 videos
In the case you want to use to 360 videos, please refer to the 360 resources listed above. 

* On the upper side of the Unity screen, open **Window > Rendering Lighting**, select the **Environment** option and replace the current attached material of the **Skybox Material** by the **HISPlayer360Material.mat**. 

<p align="center">
<img width=70% alt="image" src="https://github.com/HISPlayer/UnitySamples/assets/47497948/773885eb-3fb0-4450-8121-c8ef74b4eb3e">
</p>

*  Select the **HISPlayerController** GameObject, go to the **Inspector** and replace the current attached RenderTexture on the **HISPlayer 180 VR Controller > Multi Stream Properties** by the **HISPlayer360RenderTexture.rendertexture**.
* Replace the default URL by the 360 video you want to display

<p align="center">
<img width=70% alt="image" src="https://github.com/HISPlayer/UnitySamples/assets/47497948/2e82b66f-ca0c-4a8b-a004-dd2bd1260b04">
</p>

* **HISPlayer360Material default settings**:
  * **Rotation**: 90 
  * **Flip Vertically**: True
  * **Mapping**: Latitude Longitude Layout
  * **Image Type**: 360 Degrees
  * **3D Layout**: Over Under
    * Refer to [Unity Video Panoramic Tutorial](https://docs.unity3d.com/Manual/VideoPanoramic.html)

<p align="center">
  <img width=70% alt="image" src="https://github.com/HISPlayer/UnitySamples/assets/47497948/992ae994-1212-4084-8c06-727d8b9f829e">
</p>

    
