# FAQ NAOqi 2.9

Please find below a medley of the frequently asked questions on NAOqi 2.9

### Is there any demo application available on Command Center?

There is no standard application on Command Center but we share applications example on Github :

* QiSDK tutorials:
https://github.com/aldebaran/qisdk-tutorials
* If you want to demonstrate a retail use case :
https://github.com/softbankrobotics-labs/Retail-Demo
* You can use this application template to build your own applications:
https://github.com/softbankrobotics-labs/App-Template
* Other examples are available on this repository :
https://github.com/softbankrobotics-labs
* The documentation is available here : 
https://developer.softbankrobotics.com/

### How can I install the Basic channel for NAOqi 2.9?

The Basic Channel is not available in NAOqi 2.9 as there is no autonomous life in idle state anymore. No dialog can be running if there is no application launched on Pepper's Tablet.
However, we have made the different dialogs available to be easily integrated in your android applications if you desire to. 
The documentation is [here](https://qisdk.softbankrobotics.com/experimental/conversational_content_library.html)
Today it is available in English, French and Japanese.

### How can I setup the sound localisation in 2.9?

On Naoqi 2.9, the sound localization is disabled, so Pepper won't react to sound stimuli.


### How can I update my 2.9 Pepper to the latest OS version?

If the robot doesn’t received a 2.9 update (when it is already on 2.9+) do a factory reset from the android settings on the tablet then retry.
If it still doesn’t work please create a customer support ticket [here](https://account.aldebaran.com/support/).


### How do I setup the Kiosk mode on my robot?

Please refer to the dedicated [article]((https://developer.softbankrobotics.com/blog/kiosk-mode)

### Are NAOqi 2.5 and the python SDK still supported?

The branch 2.5 ( Python/Choregraphe) is still working but we won't add new features on it.
Choregraphe and settings webpage are not compatible with NAOqi 2.9.
However, Choregraphe 2.8 remains supported for NAO6.

### Is Nuance Remote Compliant with GDPR ?

Please find Nuance official statement on GDPR [here](https://www.nuance.com/content/dam/nuance/en_us/collateral/corporate/white-paper/wp-nuance-general-data-protection-regulation.pdf)

### Is it possible to scan QRCode / flashcode on Naoqi 2.9?

Pepper Code Scanner has been released on the [SoftBank Robotics Labs Github repository](https://github.com/softbankrobotics-labs/pepper-code-scanner)

This sample shows developers how to make Pepper scan barcodes and QR codes using the Google Vision library, with a helper library for easier integration. It is a common request in different Business environments,

it uses the tablet camera, thus allowing to have no latency on camera stream display on tablet’ screen.

it wraps an optimized Android Library (Google Vision), which allows an efficient scan even in difficult conditions (luminosity, angles)


### Do you have a list of hardware changes between 1.8 and 1.8a?

Basically, the most important changes can be found below:
* The Head had the biggest rework, for improving mostly Weight and Thermal + Audio 
* Other improvements :
 - 3D Camera has been replaced by stereo cameras
 - Lenses and Iris 
 - pretty much all the electronic boards were changed, including audio codecs
 - fan & cooling modified (supports, radiators and fans)
 - wifi board updated
 - new microphones
* Neck connection revamped for higher stability and bandwidth
* Neck rework to decrease the over heat issues
* Many motors changed to more robust ones in the chest and the wheels 

### Could you summarize the compatibilities between Hardware and Software versions?

Naoqi 2.5 is compatible with Pepper 1.7 and 1.8a and 1.8.
Naoqi 2.9 will offer its full performances on Pepper 1.8, nevertheless it is also compatible with Pepper 1.8a.


### I have this mysterious error message in my logcat  

Error Message:
_E/qi.path.sdklayout: Cannot create directory '"/mnt/sdcard/.config/qimessaging"' error was: boost::filesystem::create_directories: Permission denied: "/mnt/sdcard/.config"_
This is a known error, it shouldn’t prevent your application from functioning normally

### How to reduce the size of my apk?

Unlike typical android apps, NAOqi 2.9 application don't need to support multiple devices size. That's why you can use the following code
In your **build.gradle(Module: app)** in **android { }**.
Add the lines below to reduce APK size :
<pre>
splits {
   // Configures multiple APKs based on ABI.
   abi {
       enable true
       reset()
       include "x86", "armeabi-v7a"
       universalApk false
   }
}
</pre>
  

### I got a GoToBookmark failed with exception error

**Uncaught exception on Future: goToBookmarkedReply: Only empty rules could be matched for %validmail in email**
proposal: %validmail Thanks, I'm Sending the email right away ! ^execute(FragmentExecutor, feedback)
That means that a bookmark is deactivated, or a variable is not set, or an Executor is not correctly defined.


### How many languages can I install on my robot?

By default, customers have access to 2 languages on their pepper, English and another one of their choice (see [Language list](languages_list.md)).
If they need more they need to buy an additional licence. 
In any case there should not be more than 4 languages on a client robot.

### Can you help me with navigation?

Please refer to the dedicated [article](User_Guide-Best_Practices_for_Navigation.md)


### Can I use ^execute in a rand[] or [] ?

It is not allowed to use an ^execute inside of choice delimiters.
Use instead a ^goto(%bookmark) to go to a proposal which contains the ^execute.
For example:

<pre>
topic: ~hallo()
# Defining extra concepts out of words or group of words
concept:(hello1) [hallo hi hey "grüße dich"]
concept:(hello2) ["guten morgen" "guten tag" "guten abend" ]

# Replying to speech
u:(~hello1) ^gotoRandom(hi)

proposal: %hi ^execute(doHelloAnimation) ~hello1
proposal: %hi ^execute(doWaveAnimation) ~hello2

u:(Was geht?) alles was fuesse hat
</pre>


### How can I deactivate Pepper reaction stimuli Hold/release autonomous abilities

Please refer to the following [tutorial](https://qisdk.softbankrobotics.com/sdk/doc/pepper-sdk/ch4_api/abilities/tuto/autonomous_abilities_tutorial.html)


### I want to control my robot with a remote:

You can find code sample of how to do so on our [github](https://github.com/softbankrobotics-labs/pepper-gamepad).


### How to make Pepper Laugh?

You can play sounds on the robot and use [animations](https://android.aldebaran.com/sdk/doc/pepper-sdk/ch4_api/movement/reference/animation.html?highlight=anim).

### Where do I find additional animations?

Pepper Core Anims have been released on the [SoftBank Robotics Labs Github repository](https://github.com/softbankrobotics-labs/pepper-core-anims);

It does not contain any code, but instead is a collection of animation files for Pepper QiSDK, selected and organized by the DX Animators among what they made for many past B2B projects.
Pepper’s design and movements are above other robots on the market, and we want anybody making applications to be able to take full advantage of that.

They contain animations for:
* Solitary and Attract animations for when Pepper is not interacting with somebody
* Indicating her body parts, including the tablet
* Making space in preparation for a dance
* Loading
* Enumeration

Please take a look at this selection of animations [here](https://youtu.be/eveWttBWKvM).

### How to cut Pepper speech while he is talking?

In order to stop Pepper speech when a goToBookmark from java has been done, you just have to cancel its future
<pre><code class="java">
private void goToBookmark(String bookmark, String topic) {
        if (topicNames.contains(topic)) {
            if (!bookmark.equals("")) {
                Log.d(TAG, "going to bookmark " + bookmark + " in topic : " + topic);
                Map<String, Bookmark> tmp = bookmarks.get(topic);
                cancelcurrentGotoBookmarkFuture().thenConsume(uselessFuture ->
                        currentGotoBookmarkFuture = qiChatbot.async().goToBookmark(tmp.get(bookmark),
                                AutonomousReactionImportance.HIGH, AutonomousReactionValidity.IMMEDIATE));
            }
        } else {
            Log.e(TAG, "could not find topic: " + topic + " in topicNames");
        }
    }

    public Future<Void> cancelcurrentGotoBookmarkFuture() {
        if (currentGotoBookmarkFuture == null) return Future.of(null);
        currentGotoBookmarkFuture.cancel(true);
        return currentGotoBookmarkFuture;
    }
</code>
</pre>

If it has been made inside a topic, you can launch a goToBookmark to an empty proposal.

<pre><code class="java">
protected void stopTalking() {
      goToBookmark(“chut”, “myTopic”);
}
</code></pre>

Put this empty proposal in your topic :
<pre>
proposal: %chut ^empty
</pre>

### How to get an optimal interaction use case with Pepper

Please find a code sample of a minimal interaction flow for Pepper using the QiSDK, aimed at being a useful starting point for various interactive applications. Available on our [GitHub](https://github.com/softbankrobotics-labs/pepper-interaction-sample).


### My robot is not able to perform an animation when a human is engaged

This is completely normal as you asked Pepper to engage the human so it will track his face using, at least the motors of the neck (maybe those of the wheels).
So the solution here is to remove in the animation, the head movement and it works.
To deactivates the motors of the head in the animation it is very easy, just click the head circle.


### What is the tablet resolution?

The resolution is 1280*800.
In order to develop the interface in android studio editor we are using the device **Generic Phones and tablets** --> **Pepper 1.9 (1280 x 800, tvdpi)**.


### How to create a topic from a string?

Here is the way to create a topic from a String.
<pre>
public TopicBuilder withText(java.lang.String text)

Set a topic content from text
Parameters:
text - the text
Returns:
the builder
</pre>
So you can put the text of your dialog online and when you want pull it from your application to build it without installing your application each time.


### My App crashes when I am setting android:background in style

This is indeed an issue and it's happening because your style tries to modify all the views of the application, and one of them is the SpeechBar.
In the meantime, the workaround is to use a custom style that you apply on your own views : android:style="@style/your_style"


### What is the color of the SpeechBar? 

If you speak about the shoulders leds color in listening state, this is : #00d7ff

### How can I modify the sound level from my application?

It is possible to modify the volume of Pepper by modifying the volume of "stream audio" of the android tablet. It's linked.
<pre><code class="java">
AudioManager audioManager = (AudioManager)getSystemService(Context.AUDIO_SERVICE);

//Raise the volume of Pepper
audioManager.adjustStreamVolume(AudioManager.STREAM_MUSIC, AudioManager.ADJUST_RAISE, AudioManager.FLAG_PLAY_SOUND);

//Decrease the volume
audioManager.adjustStreamVolume(AudioManager.STREAM_MUSIC, AudioManager.ADJUST_LOWER, AudioManager.FLAG_PLAY_SOUND);

//Set the volume to 70% of the maximum
audioManager.setStreamVolume(AudioManager.STREAM_MUSIC, (int) (70.0/100.0*(double)audioManager.getStreamMaxVolume(AudioManager.STREAM_MUSIC)), AudioManager.FLAG_PLAY_SOUND);
</code></pre>


### How can I get the battery level of Pepper from my app?

Use the code below:

<pre>
IntentFilter ifilter = new IntentFilter(Intent.ACTION_BATTERY_CHANGED);
        Intent batteryStatus = getBaseContext().registerReceiver(null, ifilter);

        int level = batteryStatus.getIntExtra(BatteryManager.EXTRA_LEVEL, -1);
        int scale = batteryStatus.getIntExtra(BatteryManager.EXTRA_SCALE, -1);

        Log.d(TAG, "onCreate: Battery : "+ level);
</pre>

### Can we preventively catch a missing bookmark in our side?

It is possible to check that your bookmark exists before doing a goToBookmark using:
<pre>
 if(topic.getBookmarks().containsKey("Your_Bookmark_Name")) qiChatbot.async().goToBookmark(bookmark, AutonomousReactionImportance.HIGH, AutonomousReactionValidity.IMMEDIATE);
</pre>

### Could you tell me more about Pepper battery?

It's Energy is 795Wh. Which means we are in PI 967 section of IATA as it is more than 100 Wh.

### How can I know if my application is compatible with new QiSDK version?

it should generally work. However you will need to re robotify it if you desire to access new APIs
Please find below the compatibility table

<pre>
API     |  3  |  4  |  5  |  6  |  7  |
2.9.1   |  X  |     |     |     |     |
2.9.2   |  X  |  X  |     |     |     |
2.9.3   |  X  |  X  |  X  |     |     |
2.9.4   |  X  |  X  |  X  |  X  |     |
2.9.5   |  X  |  X  |  X  |  X  |  X  | 
</pre>

### How do I know that a language is installed on my Pepper?

Unfortunately there is no API in the QiSDK to know if a language is installed on your robot.
Please find here a workaround :
<pre>
private boolean isLanguageAvailable(com.aldebaran.qi.sdk.object.locale.Locale locale, QiContext qiContext) {
        if(!allQiLocales.contains(locale)) {
            Log.i(TAG, String.format("Language %s does not exist.", locale));
            return false;
        }
        if(qiContext == null) {
            Log.e(TAG, "Missing QiContext!");
            return false;
        }
        try {
            PhraseSet phraseSet = PhraseSetBuilder.with(qiContext).withTexts("1", "2").build();
            ListenBuilder.with(qiContext).withLocale(locale).withPhraseSet(phraseSet).build();
            return true;
        } catch (Exception e) {
            Log.e(TAG, String.format("Could not build LISTEN in %s: %s", locale, e));
            if (e.getMessage().contains("language is not installed.") ||
                    e.getMessage().contains("is not supported.")) {
                return false;
            } else {
                throw e;
            }
        }
    }

    private static final List<com.aldebaran.qi.sdk.object.locale.Locale> allQiLocales = new ArrayList<>(
            Arrays.asList(
                    new com.aldebaran.qi.sdk.object.locale.Locale(Language.FRENCH, Region.FRANCE),
                    new com.aldebaran.qi.sdk.object.locale.Locale(Language.CHINESE, Region.CHINA),
                    new com.aldebaran.qi.sdk.object.locale.Locale(Language.CHINESE, Region.TAIWAN),
                    new com.aldebaran.qi.sdk.object.locale.Locale(Language.ENGLISH, Region.UNITED_STATES),
                    new com.aldebaran.qi.sdk.object.locale.Locale(Language.ARABIC, Region.EGYPT),
                    new com.aldebaran.qi.sdk.object.locale.Locale(Language.DANISH, Region.DENMARK),
                    new com.aldebaran.qi.sdk.object.locale.Locale(Language.DUTCH, Region.NETHERLANDS),
                    new com.aldebaran.qi.sdk.object.locale.Locale(Language.FINNISH, Region.FINLAND),
                    new com.aldebaran.qi.sdk.object.locale.Locale(Language.GERMAN, Region.GERMANY),
                    new com.aldebaran.qi.sdk.object.locale.Locale(Language.ITALIAN, Region.ITALY),
                    new com.aldebaran.qi.sdk.object.locale.Locale(Language.JAPANESE, Region.JAPAN),
                    new com.aldebaran.qi.sdk.object.locale.Locale(Language.NORWEGIAN_BOKMAL, Region.NORWAY),
                    new com.aldebaran.qi.sdk.object.locale.Locale(Language.SPANISH, Region.SPAIN),
                    new com.aldebaran.qi.sdk.object.locale.Locale(Language.SWEDISH, Region.SWEDEN),
                    new com.aldebaran.qi.sdk.object.locale.Locale(Language.TURKISH, Region.TURKEY),
                    new com.aldebaran.qi.sdk.object.locale.Locale(Language.CZECH, Region.CZECH_REPUBLIC),
                    new com.aldebaran.qi.sdk.object.locale.Locale(Language.POLISH, Region.POLAND),
                    new com.aldebaran.qi.sdk.object.locale.Locale(Language.SLOVAK, Region.SLOVAKIA),
                    new com.aldebaran.qi.sdk.object.locale.Locale(Language.GREEK, Region.GREECE),
                    new com.aldebaran.qi.sdk.object.locale.Locale(Language.KOREAN, Region.REPUBLIC_OF_KOREA),
                    new com.aldebaran.qi.sdk.object.locale.Locale(Language.HUNGARIAN, Region.HUNGARY),
                    new com.aldebaran.qi.sdk.object.locale.Locale(Language.ENGLISH, Region.UNITED_STATES),
                    new com.aldebaran.qi.sdk.object.locale.Locale(Language.HEBREW, Region.ISRAEL),
                    new com.aldebaran.qi.sdk.object.locale.Locale(Language.BULGARIAN, Region.BULGARIA)
            )
    );
</pre>

### How do you know what is the right QiSDK Locale matching an android Locale?

You just have to call this function with the android Locale as parameter, it will return the QiSDK Locale.

<pre>
    /**
     * Translates the android Locale to a qiLocale if available, otherwise will return en_US
     *
     * @param locale the android locale
     * @return the qiLocale
     */
    public static com.aldebaran.qi.sdk.object.locale.Locale getQiLocale(Locale locale) {
        com.aldebaran.qi.sdk.object.locale.Locale qiLocale;
        String strLocale = locale.toString();
        if (strLocale.contains("fr")) {
            qiLocale = new com.aldebaran.qi.sdk.object.locale.Locale(Language.FRENCH, Region.FRANCE);
        } else if (strLocale.contains("zh")) {
            if (strLocale.equals("zh_CN")) {
                qiLocale = new com.aldebaran.qi.sdk.object.locale.Locale(Language.CHINESE, Region.CHINA);
            } else {
                qiLocale = new com.aldebaran.qi.sdk.object.locale.Locale(Language.CHINESE, Region.TAIWAN);
            }
        } else if (strLocale.contains("en")) {
            qiLocale = new com.aldebaran.qi.sdk.object.locale.Locale(Language.ENGLISH, Region.UNITED_STATES);
        } else if (strLocale.contains("ar")) {
            qiLocale = new com.aldebaran.qi.sdk.object.locale.Locale(Language.ARABIC, Region.EGYPT);
        } else if (strLocale.contains("da")) {
            qiLocale = new com.aldebaran.qi.sdk.object.locale.Locale(Language.DANISH, Region.DENMARK);
        } else if (strLocale.contains("nl")) {
            qiLocale = new com.aldebaran.qi.sdk.object.locale.Locale(Language.DUTCH, Region.NETHERLANDS);
        } else if (strLocale.contains("fi")) {
            qiLocale = new com.aldebaran.qi.sdk.object.locale.Locale(Language.FINNISH, Region.FINLAND);
        } else if (strLocale.contains("de")) {
            qiLocale = new com.aldebaran.qi.sdk.object.locale.Locale(Language.GERMAN, Region.GERMANY);
        } else if (strLocale.contains("it")) {
            qiLocale = new com.aldebaran.qi.sdk.object.locale.Locale(Language.ITALIAN, Region.ITALY);
        } else if (strLocale.contains("ja")) {
            qiLocale = new com.aldebaran.qi.sdk.object.locale.Locale(Language.JAPANESE, Region.JAPAN);
        } else if (strLocale.contains("nb")) {
            qiLocale = new com.aldebaran.qi.sdk.object.locale.Locale(Language.NORWEGIAN_BOKMAL, Region.NORWAY);
        } else if (strLocale.contains("es")) {
            qiLocale = new com.aldebaran.qi.sdk.object.locale.Locale(Language.SPANISH, Region.SPAIN);
        } else if (strLocale.contains("sv")) {
            qiLocale = new com.aldebaran.qi.sdk.object.locale.Locale(Language.SWEDISH, Region.SWEDEN);
        } else if (strLocale.contains("tr")) {
            qiLocale = new com.aldebaran.qi.sdk.object.locale.Locale(Language.TURKISH, Region.TURKEY);
        } else if (strLocale.contains("cs")) {
            qiLocale = new com.aldebaran.qi.sdk.object.locale.Locale(Language.CZECH, Region.CZECH_REPUBLIC);
        } else if (strLocale.contains("pl")) {
            qiLocale = new com.aldebaran.qi.sdk.object.locale.Locale(Language.POLISH, Region.POLAND);
        } else if (strLocale.contains("sk")) {
            qiLocale = new com.aldebaran.qi.sdk.object.locale.Locale(Language.SLOVAK, Region.SLOVAKIA);
        } else if (strLocale.contains("el")) {
            qiLocale = new com.aldebaran.qi.sdk.object.locale.Locale(Language.GREEK, Region.GREECE);
        } else if (strLocale.contains("ko")) {
            qiLocale = new com.aldebaran.qi.sdk.object.locale.Locale(Language.KOREAN, Region.REPUBLIC_OF_KOREA);
        } else if (strLocale.contains("hu")) {
            qiLocale = new com.aldebaran.qi.sdk.object.locale.Locale(Language.HUNGARIAN, Region.HUNGARY);
        } else {
            qiLocale = new com.aldebaran.qi.sdk.object.locale.Locale(Language.ENGLISH, Region.UNITED_STATES);
        }
        return qiLocale;
    }
</pre>

### How do I get the Head Id or Body Id of my robot to allow my application to identify / authenticate it? 

Unfortunately there is no API in the QiSDK to know the Head and Body IDs of Pepper.
Your can access the Serial number (Uuid) that is written on the Command Center Page of Pepper with this function.
<pre>
    final String TAG = "MSI GetUUIDActivity";
    private String robotUUID;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_get_uuid);

        ServiceConnection cloudServiceConnection = new ServiceConnection() {

            public void onServiceConnected(ComponentName name, IBinder service) {
                ICloudService cloudService = ICloudService.Stub.asInterface(service);
                try {
                    cloudService.getRobotUUID(new Callback.Stub() {
                        @Override
                        public void onSuccess(String response) {
                            robotUUID = response;
                            Log.d(TAG,"onCreate: Robot UUID  = " + response);
                        }

                        @Override
                        public void onError(int errorCode, String errorMessage) {
                            Log.d(TAG, "onCreate: Robot UUID Error " + errorCode + " :" + errorMessage);

                        }
                    });
                } catch (RemoteException e) {
                    Log.e(TAG, "onCreate: RobotService call failed", e);
                }
            }

            @Override
            public void onServiceDisconnected(ComponentName name) {
                Log.e(TAG, "onCreate: RobotService disconnected");
                IRobotService robotService = null;
            }
        };

        bindService(RobotServiceUtil.getCloudServiceIntent(), cloudServiceConnection, Context.BIND_AUTO_CREATE);
    }
</pre>

### How do I make Pepper take a pose and hold it?

Hello,

There is an easy way to keep a pose.

You have to hold the [Autonomous Abilities](https://developer.softbankrobotics.com/pepper-qisdk/api/autonomous-abilities/tutorials/hold/release-autonomous-abilities) then start your Animate.

Please find here a [code example](AnimateAndHold.zip)

### How to make Pepper pronounce the date and time?

You can use sayTime and sayDate to define the sentence Pepper will use when you request the Time with ^currentTime and the Date with ^currentDate.
<pre>
u:(["What is the time"]{Pepper}) it is ^currentTime
def: sayTime($hour, $minutes)   it is $hour - $minutes

u:(["which day is today"] {Pepper}) ^currentDate
def: sayDate($year, $month, $day) Today is $day - $month - $year
</pre>

### How to regain focus when robot is re-awakening (after a rest position or some crashes)?

When Pepper goes to rest position (double click on chest button), if an application is running, it loses its Focus.

In order to regain the focus when Pepper goes to stand position, the Idea is to start another activity then close it every n seconds.
When the other activity is closed, the main one goes through onResume function and regain the focus.

We have created a sample app to regain the focus, it is available [here](RobotFocus.zip).

### What is Tethys?

So far, Tethys is a tool only dedicated to an Academic program in USA.
We will keep you informed if we plan to bring it to Europe.

### What is the meaning of those Errors in logs **The call request could not be handled** or **Error when using QiChatExecutor: RemoteObject destroyed**?

The issue is an Android issue, not a QiSDK one. The issue here is that an object that is present in the tablet memory is wiped out by the garbage collector so the calls to it cannot be executed and the log: "The call request could not be handled" is displayed. Sometimes we see this one right before: [Error when using QiChatExecutor: RemoteObject destroyed].
This is not a bug in the QiSDK here but rather an expected behavior of the Android system, see the following garbage collector explanation, especially in the Step 1 and 2:
https://www.oracle.com/webfolder/technetwork/tutorials/obe/java/gc01/index.html#t2

In order to avoid that, you have to keep a reference to the qiChatBot in the mainactivity instead of defining it in the onrobotFocusGained.
<pre>
private QiChatbot qiChatbot;
</pre>Then in onrobotFocusGained :
<pre>
this.qiChatbot = QiChatbotBuilder.with(qiContext)
                 .withTopic(topic)
                 .build();
</pre>