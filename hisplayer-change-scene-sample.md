# HISPlayer Change Scene Sample

## Import sample package

Please, download the sample here -> [**HISPlayer Change Scene Sample**](https://downloads.hisplayer.com/Unity/AllPlatforms/HISPlayerChangeSceneSample.unitypackage) 
(no need to download it if you have received it in the email).

Importing the package is the same as importing other normal packages in Unity. Select the downloaded package and import it.

- **Assets > Import Package > Custom Package > HISPlayerChangeSceneSample.unitypackage**

<p align="center">
<img src="https://github.com/user-attachments/assets/fddf534c-e09b-44c6-8138-be69b2ae6f11">
</p>


## HISPlayer Sample configuration

- Select the target platform and complete the HISPlayer configuration
  - Android ->  [**Configure Unity for Android**](https://hisplayer.github.io/UnityAndroid-SDK/#/./setup-guide?id=_12-configure-unity-for-android)
  - iOS ->  [**Configure Unity for iOS**](https://hisplayer.github.io/UnityiOS-SDK/#/./setup-guide?id=_12-configure-unity-for-ios)
  - WebGL ->  [**Configure Unity for WebGL**](https://hisplayer.github.io/UnityWebGL-SDK/#/./setup-guide?id=_12-configure-unity-for-webgl)
  - Windows ->  [**Configure Unity for Windows**](https://hisplayer.github.io/UnityWindows-SDK/#/./setup-guide?id=_12-configure-unity-for-windows)
  - UWP ->  [**Configure Unity for UWP**](https://hisplayer.github.io/UnityWindows-SDK/#/./setup-guide?id=universal-windows-platform-uwp-settings)
  - macOS ->  [**Configure Unity for macOS**](https://hisplayer.github.io/UnityMacOS-SDK/#/./setup-guide?id=_12-configure-unity-for-macos)

- Open the scene **Assets/HISPlayerChangeSceneSample/Scenes/HomeScene.unity**

<p align="center">
  <img width=80% alt="image" src="https://github.com/user-attachments/assets/ff033bea-c2b4-4180-967b-1c2a072c358b">
</p>

- Import TextMesh Pro Essential

- Open **File** > **Build Settings** > **Add Open Scenes**

- Open the scene **Assets/HISPlayerChangeSceneSample/Scenes/HISPlayerSample.unity**

- If you received a license key from HISPlayer, input the license key through the Inspector. **HISPlayerController** GameObject -> **HISPlayerController** component -> **License Key**

<p align="center">
  <img width=60% alt="image" src="https://github.com/user-attachments/assets/9ba9dea9-2f0f-451d-80bd-f61fff3a566a">
</p>

- Open **File** > **Build Settings** > **Add Open Scenes**.

- Your **Build Settings** > **Scenes In Build** will be like image below:

<p align="center">
  <img width="100%" alt="BuildSettings" src="https://github.com/user-attachments/assets/8bcee0a4-7090-44f7-8ed3-a721dfd8c4c8">
</p>

- Build and Run

To check how to set up the SDK and API usage, please refer to **Assets/HISPlayerChangeSceneSample/Scripts/HISPlayerController.cs** and **HISPlayerController GameObject** in the Editor.

## HISPlayer Change Scene UI Demo
The UI components in the sample scene are fully modifiable and each stream has its own UI. 
The sample is intended to show how to change between 2 Unity scenes at runtime with HISPlayerSDK attached in one of the scene. 

**HomeScene** is the first scene where you will start the game. To change to the next **HISPlayerSample scene**, please refer to **LoadSceneButton GameObject** in the Editor and the **OnChangeScene() function** in the **SceneLoader.cs script**.

<p align="center">
  <img width=90% alt="image" src="https://github.com/user-attachments/assets/7cc89e11-d29e-4724-a772-ddd7c23f2061">
</p>

**HISPlayerSample** is the second scene where you have the HISPlayerSDK control attached. To go back to the previous **HomeScene**, please refer to the **ChangeSceneButton GameObject** in the Editor and the **OnChangeScene() function** in the **HISPlayerController.cs script**.

<p align="center">
  <img width=90% alt="image" src="https://github.com/user-attachments/assets/43d7be58-2cae-41a3-b3be-b291b283623a">
</p>

If you are using HISPlayerSDK v4.3.0 and below, before changing scene from the scene where you have HISPlayer attached, please call **Release()** API to release all of the HISPlayer resources.

If you are using HISPlayerSDK v4.4.0 and above, the **Release()** is called automatically.


```C#
    public void ReleasePlayer()
    {
        for (int i = 0; i < totalScreens; i++)
        {
            StopCoroutine(UpdateVideoPosition(i));
        }

        Release();  // Not needed for HISPlayerSDK v4.4.0 and above
    }

    public void OnChangeScene()
    {
        ReleasePlayer();

        SceneManager.LoadScene("HomeScene");
    }
```

When entering or re-entering the HISPlayer scene, make sure that you call **SetUpPlayer()** API to reinitialize HISPlayer, otherwise the video will not be loaded.
```C#
    protected override void Awake()
    {
        base.Awake();
        SetUpPlayer();
    ....
    }
```
