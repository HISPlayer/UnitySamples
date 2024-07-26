# HISPlayer Add Stream Sample

## Import sample package

Please, download the sample here -> [**HISPlayer Add Stream Sample**](https://downloads.hisplayer.com/Unity/AllPlatforms/HISPlayer_AddStream_Sample.unitypackage) 
(no need to download it if you have received it in the email).

Importing the package is the same as importing other normal packages in Unity. Select the downloaded package and import it.

- **Assets > Import Package > Custom Package > HISPlayer_Sample.unitypackage**

<p align="center">
<img width=70% src="https://github.com/user-attachments/assets/e2475b77-e192-4b86-9603-dcc9acbd400b">
</p>

## HISPlayer Sample configuration

- Select the target platform and complete the HISPlayer configuration
  - Android ->  [**Configure Unity for Android**](https://hisplayer.github.io/UnityAndroid-SDK/#/./setup-guide?id=_12-configure-unity-for-android)
  - iOS ->  [**Configure Unity for iOS**](https://hisplayer.github.io/UnityiOS-SDK/#/./setup-guide?id=_12-configure-unity-for-ios)
  - WebGL ->  [**Configure Unity for WebGL**](https://hisplayer.github.io/UnityWebGL-SDK/#/./setup-guide?id=_12-configure-unity-for-webgl)
  - Windows ->  [**Configure Unity for Windows**](https://hisplayer.github.io/UnityWindows-SDK/#/./setup-guide?id=_12-configure-unity-for-windows)
  - UWP ->  [**Configure Unity for UWP**](https://hisplayer.github.io/UnityWindows-SDK/#/./setup-guide?id=universal-windows-platform-uwp-settings)
  - macOS ->  [**Configure Unity for macOS**](https://hisplayer.github.io/UnityMacOS-SDK/#/./setup-guide?id=_12-configure-unity-for-macos)

- Open the scene **Assets/HISPlayerSample/Scenes/HISPlayerAddStreamSample.unity**

<p align="center">
  <img width=60% alt="image" src="https://github.com/user-attachments/assets/5c95e0a5-7e6f-4921-9f7e-4262b34fc559">
</p>

- Import TextMesh Pro Essential

- Input the license key through the Inspector. **HISPlayerController** GameObject -> **HISPlayerAddStreamController** component -> **License Key**

<p align="center">
  <img width=80% alt="image" src="https://github.com/user-attachments/assets/90da9872-10d2-4b17-a324-d92094ebce97">
</p>

- Open **File** > **Build Settings** > **Add Open Scenes**

<p align="center">
  <img width="70%" alt="BuildSettings" src="https://github.com/user-attachments/assets/1d3fd1e5-edab-4ad3-aaf1-f004dd87067b">
</p>

- Build and Run

To check how to set up the SDK and API usage, please refer to **Assets/HISPlayerSample/Scripts/HISPlayerAddStreamController.cs** and **HISPlayerController GameObject** in the Editor.

## HISPlayer Add Stream UI Demo
The UI components in the sample scene are fully modifiable and each stream has its own UI. The sample is intended to show a comprehensive scene using the HISPlayer SDK to help demonstrate the AddStream feature at runtime. Please, refer to the **AddStreamButton GameObject** in the Editor and the **OnAddStream function** in the **HISPlayerAddStreamController.cs script**.

```C#
/// <summary>
/// Add a new stream following the order from the screens array
/// </summary>
public void OnAddStream()
{
    int playerIndex = totalScreens;

    // 1. Prepare the StreamProperties to be added
    StreamProperties stream = new StreamProperties();
    stream.renderMode = HISPlayerRenderMode.RawImage;
    stream.rawImage = screens[playerIndex].rawImage;
    stream.autoPlay = true;

    // 2. Add prepared stream
    AddStream(stream);

    // 3. Add a video content to the stream
    AddVideoContent(playerIndex, hlsSamples[playerIndex]);

    // 4. Initialize the UI for the stream
    InitializeUI(playerIndex);

    // 5. When the limit has been reached, disable the Add Stream Button
    totalScreens++;
    if (totalScreens >= screens.Length)
        addStreamButtonGO.SetActive(false);
}
```

<p align="center">
  <img width=90% alt="image" src="https://github.com/user-attachments/assets/74cd1d09-0ac5-410e-b9e4-88083f5ad421">
</p>

<p align="center">
  <img width=90% alt="image" src="https://github.com/user-attachments/assets/ff67a32c-2612-40fb-8e34-65fdd27403af">
</p>
