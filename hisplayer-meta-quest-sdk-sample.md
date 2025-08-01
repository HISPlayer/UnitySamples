# HISPlayer Meta Quest SDK Sample
The sample is intended for playing advance video playback with Widevine L1 DRM protected content. 8K video resoultion is supported. This sample only works with Meta Quest devices.

## Requirements

#### Meta XR All-in-One version
- Minimum Meta XR All-in-One version: 60.0

#### Unity version
- Minimum Unity version: 2021.3.26f1

#### Supported HISPlayer SDK versions
- All HISPlayer SDK version for Meta Quest

#### Supported Android Version
- Minor version - Android 10.0 ‘Quince Tart’
- Minimum SDK: 29

#### Supported Unity Color Space
- Linear

#### Target Architecture
- IL2CPP - ARM64

## Integrate Meta XR All-in-One SDK

Integrate HISPlayer SDK with the **[Meta XR All-in-One SDK](https://developer.oculus.com/downloads/package/meta-xr-sdk-all-in-one-upm/)**.

First, please configure the Unity project for Oculus by following this [Tutorial](https://developer.oculus.com/documentation/unity/unity-tutorial-hello-vr/) and open **Window > Package Manager > Packages: In Project** to check Meta XR All-in-One SDK is installed properly.

<p align="center">
<img width="605" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/b4e362ba-f3d1-4d07-a46b-7a76e73d30fb">
</p>

#### Oculus platform

Open **Edit > Player Settings > MetaXR**, select the Android platform and clik "**Select All**" and "**Apply All**" in order to set up all the Oculus settings. 

<p align="center">
<img width="90%" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/691d9de5-3874-4b6a-bb1e-3b2981020590">
</p>

In XR Plug-in Management, please make sure that you have the **Oculus** option checked. Otherwise, when you run the application, it will show a 2D window without XR environment.
  
  - **Edit > Project Settings > XR Plug-in Management**

<img width="1040" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/beb2689c-d884-495c-9fa4-07b70014dfed">

## Import HISPlayer SDK
If you have not imported HISPlayer SDK yet, please follow the [Quickstart Guide](https://hisplayer.github.io/UnityAndroid-SDK/#/./setup-guide?id=quickstart-guide) or follow steps below.

**Assets > Import Package > Custom Package > HISPlayerSDK unity package**

Select the package of _HISPlayer SDK_ and import it.

<p align="center">
<img width=90% src="https://github.com/user-attachments/assets/c6c6d488-2b2c-4b79-b775-dd9dffc14471">
</p>

Open the window **Tools > HISPlayer** located in the upper side of the screen > Click on Player Settings Configuration > Select **Build Target to Android** > Set all the required settings.

<p align="center">
<img width="550" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/b3203548-b0c3-46c9-ae74-dded00c5915a">
</p>

<p align="center">
      <img width="50%" alt="image" src="https://github.com/user-attachments/assets/31964b54-f40b-4590-a081-e45dd865f73a">
</p>

By selecting Android target 33, Unity is going to ask you to update (in the case you don't have the SDK 33 installed). Please, press "Update Android SDK" button.

<p align="center">
<img width="292" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/d4cfb0b6-5d5f-4233-bd42-b454ae64925e">
</p>

Setting **"Plugins folder"** will create **mainTemplate.gradle** and **gradleTemplate.properties** in your ProjectRoot\Assets\Plugins\Android. Please make sure you use the correct **mainTemplate.gradle** that is generated from our SDK. If you need to modify it, please make sure the dependencies and configurations from HISPlayer SDK's mainTemplate.gradle exist in your modified gradle file.

## Import HISPlayer Meta Quest SDK Sample
Please, download the sample here: [**HISPlayer Meta Quest SDK Sample**](https://downloads.hisplayer.com/Unity/Quest/HISPlayer_MetaQuestSDK_Sample.unitypackage) (no need to download it if you have received it in the email). 

Before using the sample, please make sure you have followed the above requirements to set-up your Unity project for Oculus and HISPlayer SDK. To use the sample, please follow these steps :
  - Set up the Meta XR All-in-One environment
  - Import HISPlayer SDK
  - Import HISPlayer Meta Quest SDK Sample
  - Open Assets/HISPlayerMetaQuestSample/Scenes/HISPlayerMetaQuestSDKSample.unity
  - Import TextMeshPro
  - If you received a license key from HISPlayer, input the license key through the Inspector Unity window: **StreamController GameObject > HISPlayerSample component > License Key**
  - Open File > Build Settings > Add Open Scenes
  - Build and Run

To check how to set up the SDK and API usage, please refer to Assets/HISPlayerMetaQuestSDKSample/Scripts/Sample/HISPlayerSample.cs and StreamController GameObject in the Editor.

## HISPlayer Oculus Controllers
<p align="center">
  <img width="100%" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/d820d25f-a38b-4fa6-8bcc-8b7a8824125f">
</p>

## Sample Explanation

### Editor

Attach OVROverlay script to **RenderScreen** Quad GameObject. The video will be rendered on the Quad GameObject.

<p align="center">
  <img width="70%" alt="image" src="https://github.com/user-attachments/assets/54f131a8-1331-49ed-bf17-df40311e2526">
</p>

Set the following OVROverlay properties:
- **Overlay Shape**: Quad or Equirect (for 360 degree video)
- **Is External Surface**: True
- **External Surface Width**: Input the desired width size. You may input the same value as the highest resolution (width) of your stream.
- **External Surface Height**: Input the desired height size. You may input the same value as the highest resolution (height) of your stream.
- **Is Protected Content**: True.  

In the HISPlayer multistream properties, set the **RenderMode** as **External Surface**. Please go to **StreamController** GameObject > **HISPlayerSample** script > **MultiStreamProperties** > **RenderMode** > **External Surface**.

<p align="center">
  <img width="90%" alt="image" src="https://github.com/user-attachments/assets/3aff176b-16e5-46b0-b42a-0ace964c1dcc">
</p>

### Script

Please check Assets/HISPlayerMetaQuestSDKSample/Scripts/Sample/**HISPlayerSample.cs** script and refer to the **SetUpMetaQuest()** function:
- Find OVROverlay component from the GameObject (**RenderScreen**) that we have created.
- When the external surface object has been created:
  - Set the external surface to HISPlayer multistream properties's **externalSurface** object.
  - Call SetUpPlayer() to initialize the player and load the stream. 

### Non-DRM Video Playback
If you are not playing a DRM protected content, please modify the **MultiStreamProperties** by unchecking the **Enable DRM** checkbox to disable DRM and remove all element from **Key Server URI** list.

<p align="center">
  <img width="50%" alt="image" src="https://github.com/user-attachments/assets/5da42bb6-30bc-47c1-b4ee-70b81775286e">
</p>

### 360 Degree Video Playback
To render 360 degree video, you can set the OVROverlay property **Overlay Shape** to **Equirect**.

<p align="center">
  <img width="80%" alt="image" src="https://github.com/user-attachments/assets/cefa37ec-0cd1-457b-b283-5d7e7e27a697">
</p>


### Stereoscopic Video Playback
To render stereoscopic Left/Right or Top/Bottom video, you can set the OVROverlay property **Use Default Rects** to false and set the **Source Rects** and **Destination Rects**.

## More Information, Features and APIs
For more information about the supported features and APIs, please refer to the following [**HISPlayer Android Documentation**](https://hisplayer.github.io/UnityAndroid-SDK/#/).
