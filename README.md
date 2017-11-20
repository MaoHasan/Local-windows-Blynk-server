# Local-windows-Blynk-server

This is an up to date tutorial on how to set up a local windows Blynk server with a mention of some issues, giving you more security and inf. energy points.

## Getting Started

these insturction will guide you on how to build your own windows local Blynk server, other online tutorials found to be out of date or not mentioning some special cases, it is highly recommended to start using blynk cloud at first to get an overview about blynk platform, then move to the local server -it's a bit buggy-.

**PS1**: you will find other tutorials on how to build it on Mac and Linux, it's easy.

**PS2**: if you have some experiance in the field, follow the [original repository](https://github.com/blynkkk/blynk-server).

## Requirements
- [Blynk Library](https://github.com/blynkkk/blynk-library/releases/latest).

- Blynk APP: [Google Play](https://play.google.com/store/apps/details?id=cc.blynk) , [Apple Store](https://itunes.apple.com/us/app/blynk-control-arduino-raspberry/id808760481?ls=1&mt=8).

- [Java 9](http://www.oracle.com/technetwork/java/javase/downloads/jre9-downloads-3848532.html).

- Open ports 8443 (for app), 8442 (for hardware without ssl), 8441 (for hardware with ssl), **Open by default**.

- The latest Blynk local server to be found [here](https://github.com/blynkkk/blynk-server).

- Mail and Server properties to be found in this repository.

---

## Installing
- Install Java v9 via a normal double click, you can check your existing version by opening the `cmd` and typing:
```
java -version
```
You should get the following output:
```
java version "9.0.1"
Java(TM) SE Runtime Environment (build 9.0.1+11)
Java HotSpot(TM) 64-Bit Server VM (build 9.0.1+11, mixed mode)
```

- Create a folder, let say for example `C:/BlynkServer`, put the installed server, the downloaded mail and server properties files in it.

- Right click the mail file, add your email and password in where requested:
```
mail.smtp.username=xxx@gmail.com
mail.smtp.password=xxxx
```

- Make sure your E-mail accepts unknown apps requests, to do that go to your email's security, if you have a two way authentication you have to add Blynk to the approved apps, else just go [here](https://myaccount.google.com/lesssecureapps) and **allow less secure apps**.

## Running the Server
- Start the `cmd as administartor`: to start a **command prompt** as an **administrator**. Click Start, click All Programs, and then click Accessories. Right-click Command prompt, and then click Run as administrator. If the User Account Control dialog box appears, confirm that the action it displays is what you want, and then click Continue.

1. Now we need to go to the path where we created the folder, simply type `cd` and the folder path after it, for example:
```
cd c:/BlynkServer
```

2. Run the server:
```
  java -jar server-0.28.6.jar -dataFolder /Path

```
You should get the following:
```
Blynk Server 0.28.6 successfully started.
All server output is stored in folder 'c:\BlynkStuff\.\logs' file.
```
3. Thats it, now you should see two new folders being created, Keep it running, if you want to stop it just `Ctrl + C`.

- Get your local IP by by going to `cmd` and type:
```
ipconfig
```
this should return lots of info including **your local IP** that looks something like this:
```
IPv4 Address. . . . . . . . . . . : 192.168.1.55
```
Save it somewhere, you are going to need it later.

---

## Connecting to the Server

- Run the Blynk Application, and go to `Create New account`, follow the picture by adding **your own local IP**, and enter any email and password.
<img src="https://github.com/MaoHasan/Local-windows-Blynk-server/blob/master/images/blynk-create-account-local-server-.png" width="400">

- You should be logged in, Create a project and check if you recived an auto token via your E-mail, if not; check your email security as said above or disable antivirus SSL sheild in your mail scanning, if the problem remains, you can still get it via the admin panel as we will see later.

- After creating the project you will have 100,000 Energy points to use and you will be connected to the local server.

---

## Uploading a sketch

- After downloading the Blynk library and extracting it to the Arduino's library folder -usually located under `Documents\Arduino\Libraries`, open the Arduino IDE.

- pick any sketch, the only thing it change will be as follows:

**OLD**

```

  Blynk.begin(auth);
  // You can also specify server:
  //Blynk.begin(auth, "blynk-cloud.com", 8442);
  //Blynk.begin(auth, IPAddress(192,168,1,100), 8442);
  
  ```
  
  ***NEW***
  
  ```
  
  //Blynk.begin(auth); , //We will comment this
  // You can also specify server:
  //Blynk.begin(auth, "blynk-cloud.com", 8442);
  Blynk.begin(auth, IPAddress(192,168,1,100), 8442);  //Uncomment this, enter your local server's IP
  
  ```

that's all, **Upload the sketch**, you're ready to go.

---

## Accessing the admin panel
- Usually when you start the server for the first time, it will give you admin email and password as follows:
> Email : admin@blynk.cc

> Password: admin

- Go to:
```
https://your_ip:9443/admin
```
**OR**

```
https://localhost:9443/admin
```

From there you will monitor your server, access signed users, check their projects and **auth tokens**.

That's All.
# Good luck tinkering around!
