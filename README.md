# Voice-Call-Firebase-Android
WebRTC is a framework that supports browsers for instant video and audio conversations

It is an industry standard (W3C, IETF). Recently, I have studied this thing because I wanted to make an application with audio call inclusion  for cognitive behavior therapy . If you just want to try WebRTC , you can directly try AppRTC, a Google example, but this is the version of the Web, I wanted to use the WebRTC for the  phone (Android, iOS), AppRTC also has Android version to match In order to get familiar with the whole process of creating a video call with WebRTC, I decided to change the Android version. The original version of Google is through the Web Socket.

Switching the Web RTC segment to Firebase (well, I actually regretted choosing Firebase to implement it) is actually replacing the Signaling section, and the process is 

#Image 

This part is actually the process of exchanging SDP and ICE candidate on  both sides 
here WebRTC abbreviated terms related to introduction: http://blog.mozilla.com.tw/posts/3261/webrtc-%E7%9B%B8%E9%97%9C%E7%B8%AE%E5%AF%AB%E5%90%8D%E8%A9%9E%E7%B0%A1%E4%BB%8B

Building WebRTC lib on Android

In fact, if you write WebRTC application, you don't have to start from scratch. Google has already implemented it inChromium, or you can build a library separately. with here are the officialAndroid version of how to build a Web RTClibrary,however, 
We need to build the RTC Libraries for our android version which might seem simple, but ... there are several issues, first is the only build on Linux, therefore in windows it needed high demands on the hardware, used VM to build, I found that at least 4G RAM, hard disk requires more than 20G of instance (needed a lot of time)

. After the build, the required things include libjingle_peerconnection.jar and libjingle_peerconnection_so.so, these are backed up. Waiting for build apk need to use

We need to compile it for the Android studio project format, so you need to use the import method, or you can directly fork versionTo change, because the original version uses Web socket to do singaling pipeline, so we need Autobahn,	but we must remember to use Autobahnofficial latest jar file,  the difference is that the originalAutobahnis not SSL-websocket, but AppRTCwebsocket is to come through the SSL connection

Afterwith the jar files into the corresponding directory so go, remember to change it build.gradle join in the app directory (because the import will not help you produce plus):
dependencies {
    Compile fileTree(dir: 'libs', Include: ['*.jar'])
}


Plus firebase

In addition to the original Webcoket and Direct connect, in order to run his process once I added the Firebase part, use its realtime database to do the Signaling part, as for how began developing firebase, on refer to the fficial documentation 
https://firebase.google.com/docs/database/android/start/

refer to the Firebase section in order to furtehr understand the server calling , TURN Server, Callactivity setup etc. 


