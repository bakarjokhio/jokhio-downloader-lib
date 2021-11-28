# jokhio-downloader-lib

Jokhio Downloader is a java library developed especially for Sketchware to add support of old file path and new content Uri to enable them to download files while using SAF (storage access framework).

## 1.Set Up

### a) Download library and add to your project

you can download 

• jokhio-downloader.zip from above files

• or from my app

• or from our telegram

if you are using android studio or something like that i hope you know how to add ***jar*** libraries to your project, however of you're using sketchware you can watch the video to learn how to add library.

### b) import required class

After adding library to your project in order to use it you have to add this important statement 

```import jokhio.downloader.DownloadService;```


![Screenshot_20211128-114957](https://user-images.githubusercontent.com/61370010/143732668-f0a20872-1e28-4f70-8cae-d4f2d031d13f.png)

### c) declare DownloadService variable

```private  DownloadService downloadService;```
![Screenshot_20211128-115605](https://user-images.githubusercontent.com/61370010/143732842-fc6e38c2-63c0-4709-ae91-feffc60b8693.png)

### d) initialize DownloadService 

```Intent intent = new Intent(this, DownloadService.class);

bindService(intent, conn, Context.BIND_AUTO_CREATE); 
``` 
![Screenshot_20211128-230540](https://user-images.githubusercontent.com/61370010/143780531-06077efc-ddd8-4861-a0da-a338b1b27b12.png)

