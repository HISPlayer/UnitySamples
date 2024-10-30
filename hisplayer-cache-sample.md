# HISPlayer Cache Sample

## Requirements

#### HISPlayer SDK
- Minimum SDK: 3.4.3

## Import HISPlayer SDK
If you have not imported HISPlayer SDK yet, please follow the [Quickstart Guide](https://hisplayer.github.io/UnityAndroid-SDK/#/./setup-guide?id=quickstart-guide).

## Import HISPlayer Cache Sample
Please, download the sample here: [**HISPlayer Cache Sample**](https://downloads.hisplayer.com/Unity/AllPlatforms/HISPlayerCacheSample.unitypackage) (no need to download it if you have received it in the email). 

Before using the sample, please make sure you have followed the above requirements to set-up your Unity project for Oculus and HISPlayer SDK. To use the sample, please follow these steps :
  - Import HISPlayer SDK
  - Import HISPlayer Cache Sample
  - Open Assets/HISPlayerCacheSample/Scenes/HISPlayerCacheSample
  - If you received a license key from HISPlayer, input the license key through the Inspector Unity window: **StreamController GameObject > HISPlayerSample component > License Key**
  - Open File > Build Settings > Add Open Scenes
  - Build and Run

To check how to set up the SDK and API usage, please refer to **Assets/HISPlayerCacheSample/Scripts/Sample/HISPlayerCacheStreamController.cs** and StreamController GameObject in the Editor.


## HISPlayer Cache Sample

The sample is intended to show a comprehensive scene using the HISPlayer SDK to help demonstrate the cache features:

 * InitCacheInstance
 * AddURLToCache
 * IsURLCached
 * GetRemainingCacheSpace
 * Cache Events:
   * EventCacheFlushed

The sample uses 2 streams to swap the video content between them. There are 2 buttons (Previous Stream and Next Stream) to change the current video content. While one stream is 
displaying the video, the other one is loading the next video in the list to be ready to play as fast as possible.

## Initialize Cache Instance

In order to use the cache API, it is needed to call the InitCacheInstance(). You can find an example of this on the Awake() function inside the script mentioned above: HISPlayerCacheStreamController.cs.

After the **base.Awake()** function is called, the cache is initialized using 300 MB and all the URLs listed in **videoSamples string array** are added to the cache.
Then the cache space is checked and finally the SetUpPlayer() API is called to start the HISPlayerSDK functionalities.

The following HISPlayer APIs are used in this function:

* Awake and base.Awake()
* InitCacheInstance
* IsURLCached
* AddURLToCache
* GetRemainingCacheSpace
* SetUpPlayer

```C#
    protected override void Awake()
    {
        base.Awake();

        InitCacheInstance(maxCacheSize);

        for (int i = 0; i < videoSamples.Length; i++)
        {
            if (!IsURLCached(videoSamples[i]))
                AddURLToCache(videoSamples[i]);
        }

        cacheByteSize = GetRemainingCacheSpace();
        float remainingSpace = 100f * cacheByteSize / maxCacheSize;
        Debug.Log("Awake | Percentange of cache remaining " + remainingSpace + "%");

        // Force to portrait mode
        if (runtimePlatform == RuntimePlatform.Android || runtimePlatform == RuntimePlatform.IPhonePlayer)
            Screen.orientation = ScreenOrientation.Portrait;

        SetUpPlayer();
        StartCoroutine(AddCachedStreamsFromScript());
    }
```

## AddCachedStreamsFromScript

We provide an auxiliar function to add streams from the script instead of the Editor. This way, the streams can load the videos from the cache.
It is a Unity Coroutine that waits until the first video in the list is cached. 

The following HISPlayer APIs are used in this function:

* IsURLCached
* StreamProperties constructor and parameters
* AddStream
* AddVideoContent

```C#
    /// <summary>
    /// Adds new streams using AddStream API and adds the respective video
    /// content using AddVideoContent API
    /// </summary>
    IEnumerator AddCachedStreamsFromScript()
    {
        yield return new WaitUntil(() => IsURLCached(videoSamples[0]));

        totalScreens = streamsScreens.Count;
        for (int i = 0; i < totalScreens; i++)
        {
            isPlaybackReady.Add(false);

            // 1. Create the new 'StreamProperties stream' to be added
            StreamProperties stream = new StreamProperties(isLoopPlaybackEnabled: true);
            stream.autoPlay = true;
            stream.renderMode = HISPlayerRenderMode.RawImage;
            stream.rawImage = streamsScreens[i];

            // 2. AddStream API
            AddStream(stream);

            // 3. AddVideoContent API
            AddVideoContent(i, videoSamples[i], mimeType);

            // 4.1 Enable the rendering of the stream 0 
            if (i == 0)
            {
                streamsScreens[i].gameObject.SetActive(true);
                continue;
            }

            // 4.2 Disable the rendering of the other streams
            streamsScreens[i].gameObject.SetActive(false);
            StartCoroutine(PauseWhenReady(i));
        }
    }
```

## Sample Update

We use the **Unity Update()** function to monitor the cache space. When a change is detected, the information will be logged. 
In the case, the remaining space is less than 10%, the cache will be flushed and the callback EventCacheFlushed will be triggered.

The following HISPlayer APIs are used in this function:

* GetRemainingCacheSpace
* FlushCacheFolder

```C#
    private void Update()
    {
        if (GetRemainingCacheSpace() == cacheByteSize)
        {
            return;
        }

        cacheByteSize = GetRemainingCacheSpace();
        float remainingSpace = 100f * cacheByteSize / maxCacheSize;
        Debug.Log("Update | Percentange of cache remaining " + remainingSpace + "%");

        if (remainingSpace <= 10f)
            FlushCacheFolder();
    }
```

## Callback EventCacheFlushed

This is event is triggered when the HISPlayer internal cache folder has finished of freeing the space. We use this event to add the previous and the next video from the variable 
the variable **currentVideoContent** following the list of the URLs mentioned above. This operation is needed if you want to keep videos in cache, otherwise the FlushCacheFolder() API will remove the cached data.

The following HISPlayer APIs are used in this function:

* GetRemainingCacheSpace
* FlushCacheFolder

```C#
    protected override void EventCacheFlushed(HISPlayerEventInfo eventInfo)
    {
        base.EventCacheFlushed(eventInfo);

        int nextVideo = currentVideoContent + 1;
        if (nextVideo > videoSamples.Length)
            nextVideo = 0;

        AddVideosToCacheFromVideoIndex(nextVideo);
    }
```
