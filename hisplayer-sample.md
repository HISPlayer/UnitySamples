# HISPlayer Sample

## Import sample package

### HISPlayer SDK versions 3.4.0 and above

The _HISPlayer Sample_ is included in the _HISPlayer SDK Unity Package_.

Importing the package is the same as importing other normal packages in Unity. 
Select the package of _HISPlayer SDK_ and import it.

**Assets > Import Package > Custom Package > HISPlayerSDK unity package**

<p align="center">
<img width=80% src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/c8ff9e55-524e-48f1-a323-95b00aa5c6c7">
</p>

In the case you just need to include the _HISPlayer Sample_, please disable **com.unity.hisplayersdk** from the _Import Unity Package_ window.

<p align="center">
  <img width=60% src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/51acd7c5-6515-42aa-a6a7-e0480f7b3691">
</p>

### HISPlayer SDK versions 3.3.0 and below

Please, download the sample here -> [**HISPlayer Sample**](https://downloads.hisplayer.com/Unity/AllPlatforms/HISPlayer_Sample.unitypackage) 
(no need to download it if you have received it in the email).

Importing the package is the same as importing other normal packages in Unity. Select the downloaded package and import it.

- **Assets > Import Package > Custom Package > HISPlayer_Sample.unitypackage**

<p align="center">
<img width=70% src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/64449b3e-6397-4b65-ba21-c9635cb83a81">
</p>

## HISPlayer Sample configuration

- Select the target platform and complete the HISPlayer configuration
  - Android ->  [**Configure Unity for Android**](https://hisplayer.github.io/UnityAndroid-SDK/#/./setup-guide?id=_12-configure-unity-for-android)
  - iOS ->  [**Configure Unity for iOS**](https://hisplayer.github.io/UnityiOS-SDK/#/./setup-guide?id=_12-configure-unity-for-ios)
  - WebGL ->  [**Configure Unity for WebGL**](https://hisplayer.github.io/UnityWebGL-SDK/#/./setup-guide?id=_12-configure-unity-for-webgl)
  - Windows ->  [**Configure Unity for Windows**](https://hisplayer.github.io/UnityWindows-SDK/#/./setup-guide?id=_12-configure-unity-for-windows)
  - UWP ->  [**Configure Unity for UWP**](https://hisplayer.github.io/UnityWindows-SDK/#/./setup-guide?id=universal-windows-platform-uwp-settings)
  - macOS ->  [**Configure Unity for macOS**](https://hisplayer.github.io/UnityMacOS-SDK/#/./setup-guide?id=_12-configure-unity-for-macos)

- Open the scene **Assets/HISPlayerSample/Scenes/HISPlayerSample.unity**

<p align="center">
  <img width=60% alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/0c4b5314-d835-4e56-879c-6d48c16312b2">
</p>

- Import TextMesh Pro Essential

- If you received a license key from HISPlayer, input the license key through the Inspector. **HISPlayerController** GameObject -> **HISPlayerController** component -> **License Key**

<p align="center">
  <img width=80% alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/f99d01df-847e-4289-9a33-364ce9210e53">
</p>

- Open **File** > **Build Settings** > **Add Open Scenes**

<p align="center">
  <img width=70% alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/6c774c5f-2b81-4cd3-8588-b26f8ee92784">
</p>

- Build and Run

To check how to set up the SDK and API usage, please refer to **Assets/HISPlayerSample/Scripts/HISPlayerController.cs** and **HISPlayerController GameObject** in the Editor.

## MultiStream UI Demo
The UI components in the sample scene are fully modifiable and each stream has its own UI. The sample is intended to show a comprehensive scene using the HISPlayer SDK to help demonstrate features such as play, pause, seek, etc using the multi stream feature. 

<p align="center">
  <img width=55% alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/312e37e7-aff3-4537-8dc3-d5843b86441c">
</p>

<p align="center">
  <img width=90% alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/640453d1-8a58-45cf-9260-c659cb308655">
</p>

## Add/Remove Streams and URLs
In order to add/remove streams and URLs, please refer to the component **HISPlayerMultiStreamController** attached to the **HISPlayerMultiStreamController GameObject** in the **Inspector**. 

### Add/Remove Streams

You can add/remove streams by pressing the buttons **+/-** in the **Multi Stream Properties list**. Once a new stream is added, please, select the render mode and the surface where you want to display your videos (Material, Raw Image or RenderTexture). 

<p align="center">
  <img width=70% alt="streams" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/f0a1521d-807a-48f5-893e-58135516b37e">
</p>

<p align="center">
  <img width=70% alt="render-mode" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/e65f23af-cf95-4858-b654-d0199feecd71">
</p>

### Change Default URL
To change the default video URL using your own URL, please replace the element value with your own URL in the **URL list** of the stream you want to modify.

<p align="center">
  <img width=60% alt="replace-url" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/5b876db4-f3c9-4c98-84df-f23737070f50">
</p>

### Add/Remove URLs

You can add/remove URLs by selecting one element from the **Multi Stream Properties list** and then pressing the buttons **+/-** in the **Url list**. 

<p align="center">
  <img width=70% alt="add-url" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/b65bf99f-202b-436e-a9c3-f1a6b9b97eaa">
</p>

### Change video content at runtime
For changing the content of the videos at runtime, please refer to the **ChangeVideoContent** API: 

- **[Android ChangeVideoContent API](https://hisplayer.github.io/UnityAndroid-SDK/#/hisplayer-api?id=protected-void-changevideocontentint-playerindex-int-urlindex)**.
- **[iOS ChangeVideoContent API](https://hisplayer.github.io/UnityiOS-SDK/#/hisplayer-api?id=protected-void-changevideocontentint-playerindex-int-urlindex)**.
- **[WebGL ChangeVideoContent API](https://hisplayer.github.io/UnityWebGL-SDK/#/hisplayer-api?id=protected-void-changevideocontentint-playerindex-int-urlindex-int-resumeposition-0-adsproperties-ads-null)**.
- **[Windows/UWP ChangeVideoContent API](https://hisplayer.github.io/UnityWindows-SDK/#/hisplayer-api?id=protected-void-changevideocontentint-playerindex-int-urlindex)**.
- **[macOS ChangeVideoContent API](https://hisplayer.github.io/UnityMacOS-SDK/#/hisplayer-api?id=protected-void-changevideocontentint-playerindex-int-urlindex)**.

