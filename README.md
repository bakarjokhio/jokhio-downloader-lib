# jokhio-downloader-lib

Jokhio Downloader is a java library developed especially for Sketchware to add support of old file path and new content Uri to enable them to download files while using SAF (storage access framework).

## 1.Set Up

### Download library and add to your project

you can download 

• jokhio-downloader.zip from here [click to download](https://github.com/bakarjokhio/jokhio-downloader-lib/raw/main/jokhio-downloader.zip)

• or from my app

• or from our telegram

if you are using android studio or something like that i hope you know how to add ***jar*** libraries to your project, however of you're using sketchware you can watch the video to learn how to add library.

### import required class

After adding library to your project in order to use it you have to add this important statement 

```import jokhio.downloader.DownloadService;```


![Screenshot_20211128-114957](https://user-images.githubusercontent.com/61370010/143732668-f0a20872-1e28-4f70-8cae-d4f2d031d13f.png)

### declare DownloadService variable

```private  DownloadService downloadService;```
![Screenshot_20211128-115605](https://user-images.githubusercontent.com/61370010/143732842-fc6e38c2-63c0-4709-ae91-feffc60b8693.png)

### initialize DownloadService 

```
Intent intent = new Intent(this, DownloadService.class);

bindService(intent, conn, Context.BIND_AUTO_CREATE); 
``` 
![Screenshot_20211128-230540](https://user-images.githubusercontent.com/61370010/143780531-06077efc-ddd8-4861-a0da-a338b1b27b12.png)

### unbinding service

we should always make sure to unbind the service when it is no longer used. on destroy is also a good spot to unbind.

` unbindService(conn); ` ![Screenshot_20211128-231722](https://user-images.githubusercontent.com/61370010/143780904-a6c96c5f-fb8b-4d97-ac87-4bce64657dec.png)

### Creating service connection

if you notice we are using `conn` object while binding and unbinding the service so what is `conn` ? it is actually ` ServiceConnection` i have created that object there in a moreblock 
```
ServiceConnection conn = new ServiceConnection() {

	@Override

	public void onServiceDisconnected(ComponentName name) {

		

	}

		@Override

	public void onServiceConnected( ComponentName name, IBinder service) {

		//RETURN AN MsgService object 

		downloadService = ((DownloadService.MsgBinder) service). getService ();

	}

	

};

```
![Screenshot_20211128-232321](https://user-images.githubusercontent.com/61370010/143781082-b2d88363-f564-490c-b87d-7b186a3a117c.png)

### Add Permissions

Add required Permissions such as internet and storage

```
        <uses-permission android:name="android.permission.INTERNET" />
	<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
	<uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
	<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
```

![PicsArt_11-29-07 51 02](https://user-images.githubusercontent.com/61370010/143886266-d5489bc5-831a-43cd-95a4-0f5860d246a4.jpg)

### Declare Service in manifest

You also have to declare that service in App Manifest. 
AndroidStudio users know how to do it sketchware users just copy and paste below code to app components asd.


```
<service
			android:name="jokhio.downloader.DownloadService"
			android:enabled="true" />
```

![Screenshot_20211129-193712~2](https://user-images.githubusercontent.com/61370010/143888373-9520cc2c-42e9-4e9a-9945-b6abbba34377.png)


## 2. Downloading 

 before downloading you should also check if doenloadService is not null using this code ` downloadService != null `

![Screenshot_20211129-194852~2](https://user-images.githubusercontent.com/61370010/143891359-3a19467b-f4f2-44a2-aff6-8d6a0cfd3ec5.png)

### Legacy download 

for downloading files while using old storage access you can use 

`startDownload(String link, String filename, String path); ` 
for example I'm using :-

```
downloadService.startDownload(link_edit.getText().toString(), filename, path);
```
![Screenshot_20211129-194852](https://user-images.githubusercontent.com/61370010/143910514-b2bf608e-3223-4f8c-813b-95eab630ace1.png)

in above example I'm using values stored in **string** for **path** and **filename** and as for **link** I'm getting it from **edit text** .



### Download with new Storage Framework

If you are using content Uri instead of old fashion file path use `startDownload1(String link, String filename, Uri fileUri) ` more details and blocks about it coming soon.

## what's next?

Details about how to get progress and other information are coming soon.
Your suggestions are welcomed.
