# FAQ Command Center and Co

### 1. Is the client robot already configured upon arrival to the client if it has been configured on Command Center? 

* The robot will be shipped from Paris with the latest release of Naoqi installed.
* If you see it on your Command Center, then you can configure it with your app and the Kiosk Client app. (If you don't, you will have to open us to the Customer Care).
* When the client receives his robot, he will have to do the **Getting started wizard**, the first steps where he has to connect Pepper to a wifi, log with a SoftBank account, choose the robot password  etc...
* Then he can open the application **SBR applications Updater** and click **Update**. The robot will download and install the android applications that you have configured on Command Center.
* If you set a language on Command Center, the client would have to open the android settings, go to the robot area at the bottom, click **Update system / Robot apps** then **Update all Robot apps**
* Then he can start the application **Kiosk Client**(if you have set your app "As Default" on Command Center), this should start your app in **Kiosk Mode**.


### 2. How does the client connect its robot to WiFi since it is in kiosk mode?

* As mentioned above, the connection to wifi will be during the Getting Started Wizard, if for any reason, the GSW is already done, as the Kiosk Client app won't be installed, your client will have access to the android settings so he will be able to connect Pepper to the wifi. (if robot is in Kiosk Mode, the [documentation](https://developer.softbankrobotics.com/blog/kiosk-mode) will explain you how to exit)


### 3. Can we establish a remote connection with the client robot via VPN to see the screen of the robot in real-time?

* As Pepper's tablet is an android tablet, you can create your own VPN service inside your App.


### 4. Can we see the robot status, installed app version, whether the robot is connected to the internet on Command Center?

* It is possible to see the version of Naoqi installed on Pepper on Command Center.
* It is not possible to see if the apps are really installed on Pepper (only the ones that are configured with the version).
* It is not possible to see if the robot is connected or not to internet on Command Center.


### 5. How easy it is to work with robots remotely?

* Our systems will allow you to manage Pepper remotely but not to monitor it.
* Unfortunately if you want to have access to more logs, information etc... remotely, you should integrate those functions inside your application.

### 6. What will happen in case KioskClient is installed and our application is a default application and robot is moved to a different place with a different WiFi? Is it possible to change the WiFi without exiting the application?

* It is always possible with the [Magic gesture](https://developer.softbankrobotics.com/blog/kiosk-mode) to exit the kiosk mode to change some settings or do an update and relaunch kiosk manually after it. 
* It is also possible to add a snippet of code inside your application to launch the settings from your app without exiting the kiosk mode (this code is available in Pepper App Launcher).

### 7. What will happen when there is Pepper system update and Pepper has an app launched in Kiosk mode?

* It is necessary to exit the app, go into settings, install the update and Kiosk Client Application. As we do not know when the client want to do the update, we do not start it automatically (If it is during a presentation with Pepper for example).

### 8. Can we launch/deploy app via Command Center for the client without QA review?

* There is a constraint on Command Center. When you upload an application on it, its status is beta by default.
* You can share a beta application with someone for 30 days only.
* If you want to be able to share your app with no restriction, you will have to do a private release on Command Center then share it with your customer. 

### 9. when I share a beta version with someone, what happens after 30 days?

* After the 30 days the mission is removed from the missions of the person you shared with and from the robot if it is connected to internet and ON.
* If Pepper is off, as soon as it synchronizes with Command Center, it will uninstall the app.

### 10. And when I want to renew the 30 days sharing, should I delete the contributor and add him again? Is he losing the mission and has to reassign after this?

* Yes you should remove the sharing then redo it.
* The mission is removed from the Missions of the person then added again.
* Yes, the person will have to reassign 

### 11. Can I add a beta version of a mission in a Group in Command Center

* No it is not possible. You have to do a private release to add an app to a group.

### 12. My client want to manage its robot in Command Center, how can we open the access?

Open a ticket to our Customer Care team [here](https://account.aldebaran.com/support/) with the information below to create the account :
* The name of the Company
* First and last name of the administrator of Command Center
* Email of the administrator of Command Center
* Head and Body ids of all their robots.

### 13. How can I delete a contributor from my mission?

* When your are in the Dev interface with the list of all your missions, click on the icon below **Contributors**.
Here you will be able to remove them.