# ControlRaspberryNodeJS
ControlRaspberryNodeJS

https://apiko.com/blog/how-to-build-home-automation-app-with-raspberry-pi-and-javascript/amp/

Building Home Automation Open-Source App With React Native, Node, Express and Raspberry Pi
by Tymets Volodymyr

2018-01-26

Imagine that you own a large aquarium at home, full of fish shoal. To make it look more aesthetic, you’ve decided to plant some exotic seaweed. Like every living entity, seaweed needs a proper care, it needs enough and specific dose of light. Let's say, it needs the lighting during particular period of time, i.e. from 9 am till 4 pm. Another issue emerges there since you can’t physically control the light supply. The reason is your working schedule which is set from 8 am to 6 pm. ‘It would be nice to have some kind of app that can turn on/off the light or adjust its supply to the specific hours, while I’m at work’- you might think.

Or let’s consider another similar situation. Your house’s heating system is electric, but right now, you have a lot of tasks to do at work + your boss assigns you business trips from time to time.You’re rarely at home these days. Nevertheless, you’d like to control the heat supply as you’re leaving home. The home automation mobile app that allows to do it, is a nice finding indeed.

In this article, apart from the mentioned examples, we’d like to share personal experience on how to build a home automation system with Raspberry Pi, React Native and Node. Our aim is to demonstrate how with the help of such JavaScript-based open-source app you can manage electricity supply in one of your power sources/sockets.

Main concept behind this home automation mobile app
The major idea of the project hides behind the presence of a certain ‘controller’ that can manage the state of electricity and other devices in your house. We also need to create a specific smart home mobile app to interact with the controller remotely (‘smart house’ system concept). Let’s take a look at the scheme provided below:

home-automation-app-with-react-native-nodejs-expressjs-raspberrypi-scheme
Home automation via controller

We can use Raspberry Pi, a small single-board computer as the ‘controller’ for this domotics mobile app. The device contains the same advantages and opportunities as of ordinary computers. The only difference is that it’s smaller in size and allows to control various household appliances and devices. To manage the ‘controller’ a user can interact with it by means of their smartphone (in our case, it’s the Android-based one, but you can experiment with whatever OS you wish). As the result it turns out to be quite a comfortable home automation and control system.

Required tech equipment for the smart home mobile app creation
The list of required tech equipment looks like this:

Power/electricity source (socket)

Raspberry Pi microcomputer

Micro SD flash memory

Wi-Fi adapter or Ethernet cable

Relay

Smartphone

Since Raspberry Pi has 5V GPIO outputs, we’ll need additional 220V power supply.

Raspberry Pi
As we’ve noted it earlier, Raspberry Pi is a small single-board computer which is used to control various devices and softwares mostly remotely. Here’s a short list of hardware that you can use with this microboard:

GPIO controllers

Ethernet cable or Wi-Fi adapter

Bluetooth

Sound, microphone, camera

GPS coordinates

Environmental sensors - temperature, pollution sensors

There are lots of business usecase opportunities for Raspberry Pi, like:

Smart house systems and home automation mobile apps creation

Robotics

Public transport GPS tracking

Visual monitoring systems (video, audio signal streaming to server or client)

Environment monitoring systems in the agrarian or scientific sector (temperature or pollution level sensors)

Medical sector

220 Power supply
To control the power supplied, we’ve connected a relay to the power supply and Raspberry Pi. Two types of relays are shown in the picture below. The devices which require higher input voltage and current, work best with the 1st type of relay. The 2nd type of relay can be a good match for the less power-hungry devices. We’ll go further with the 2-nd type of relay, since it's a test version of this home automation app project. The working scheme is clear as a day. If the current supply of input connectors is 3-5V, the relays close the electrical circuit which is connected to the output connectors of the controlled object.

home-automation-app-with-react-native-nodejs-expressjs-raspberrypi-220-power
Two types of relay

User interface/ interaction with user
I’ve written an Android home automation mobile app (in fact, you can utilize any OS you’re fond of) and used smartphone as the way to provide user interaction mechanism /OR: to let user control the ‘controller’ via smartphone.

The app is plain in design and interface since it serves as a test one. Its aim is to demonstrate the home automation opportunities we can reach using JS technologies.


App’s interface

Putting it all together
To prove that the scheme works, we’ve tested it on an ordinary fairy lights garland. It's a quite a simple and trivial example to show the potential of home automation with the help of mobile devices. We’ve cut one of the garland’s wires and connected it to the relay (look at the picture below). That’s how we’ve broke the circuit. Then we’ve connected the relay to Raspberry Pi outputs.


To connect Raspberry to relay you can use 3 inputs here: GND ground (green), UCC 5V Power (red) IN 3V programmed pin (yellow). Please, refer to Raspberry Pi outputs map

You can use this method to connect any electric circuit or electricity source in your house. As a result, you’ll receive a completely controlled power source for any type of devices.

Now, the only thing you need is to plug our garland in the socket and check if everything works. Below you’ll see the results of this stage:

Ta-da!

Software implementation
We need to make sure that the communication between devices works well. This is an important step, since Raspberry GPIO serves as a ‘controller’ for garland. User manages the garland’s state via the Raspberry ‘controller’ by using their phone accordingly. The most optimal way that worked best for us was REST API creation that would do both:

Work for Raspberry

Receive commands from phone

I’ve used the following tech stack for this smart home mobile app project:

Express JS - with this framework, we’ve created JavaScript Server API

React Native - UI framework for building native mobile apps

home-automation-app-with-react-native-nodejs-expressjs-raspberrypi-home-control
Note that there are other methods of interaction with Raspberry, including:

Via Ethernet wire

Via remote server (in this case, you create cloud API and send commands to the server. The server, in its turn, sends these commands to Raspberry)

Via Bluetooth protocol

Read more about Bluetooth connection Hackster’s article on mobile app that connects to your Raspberry Pi 3 using BLE.

How to build a mobile сlient for the domotics mobile app?
For this mission a mobile client was needed, that’s why I’ve written a small mobile smart house app with the help of React Native.

To build the app, I’ve gone with Expo, a toolset for React Native. Check Expo docs for the detailed app creation tutorial. After you complete all the instructions described in the docs, the app’s start screen will pop up. Then it's neccessary, to somehow replace it with the screen we need. That’s why I’ve created a directory to place there screen which depicts the app’s logic and view in src/view/views/LightControl. (Read more about the effective ways to organize React Native project in the blog post by Spencer Carli).

Below you can see the code snippet for the screen we’ve mentioned above:

In this article I’ve decided to omit the detailed explanations of each technology’s features. My major aim is to generally highlight the topic on how to build a home automation system by means of JS-based technologies.

The code above displays two 'turn on' and 'turn off' buttons. Since the mobile client sends requests to our server, I’ve written a certain class for the interaction with the server src/utils/api.js.

I recommend to replace the IP you’ve got in BASE URL to your Raspberry’s IP. Enter ifconfig after you’ve connected to your Raspberry.

I’ve used Recompose to describe all of the domotics mobile app's business logic. Here you’ll find the code snippet which is responsible for clicking actions.

As the result we’ve got a small project, written by one person and with the help of which we can interact and control the devices and supplement at home. Apart from this, we can run the home automation mobile app on Android or iOS which will surely save more time to develop similar business projects.

Raspberry server development
First thing we need is to install OS for our new Raspberry Pi. You can find the tutorial to do this on Dave Johnson’s website. Then, with the help of Ethernet, I’ve connected PC to Raspberry. Given the fact that this smart house app is clearly JavaScript-based, the server side was written in NodeJS and Express JS.

To generate Express project, you can use express-generator . This npm will form the required project’s structure. The only thing needed from us, is to expand the project’s functionality by means of code.

Let’s get to ‘controller’ development part. I’ve started from home devices operation. To manage the state of various devices, Raspberry PI uses GPIO. I’ve utilized onoff library to manage Raspberry Pi with NodeJS. The library has helped me to program one of the GPIO outputs to control the power supply. The control is realized with GpioController class in utils/GpioController.js.

The represented class contains 2 methods - lightOn and lightOff. With their help we can control power supplied to one of outputs.

The output number and the sequence number on the same Raspberry Pi board are not the same things. Below is depicted Pin numbers map.


To let Raspberry receive REST request, I’ve created 2 routes to control Pin outputs.

Take a look at how to implement one of these routes:

As you could see it earlier, the mobile client contains the interface that allows you to set working time for a specific device at your home. For this logic realization, we can use node-cron package. The task will be implemented in tasks/.

Please note. I’ve used global.time.from constant in the code provided above, to demonstrate the general workflow of this test home automation mobile app and shorten the development time. It’s not recommended though to use this constant for the creation of larger projects with a specific business value.

We also need to write a new route to save the working time returned/OR: output from the client.

How we can implement one of these routes:

As you can see, this part mostly referred to how to build a home automation system with Raspberry Pi. I’ve described here how to create working API to control Raspberry Pi via your local network in several steps. You can deploy the written server via your git repository or use ssh methods to do it locally. Then run it with the simple npm start command. You can use npm forever package to make the server work after you’ve turned Raspberry on .

The current smart house app is open source and the code is available at the ‘Home Control’ GitHub repository.

The outcome
The aim of this article was to demonstrate how to build a mobile home automation system with Raspberry Pi and and the technologies based around JavaScript only. Apart from this, my purpose was to show how far JavaScript evolution can go and that only one person can mange the entire process of home automation app creation.

Read also: "How to Create Home Automation App for Clap Detection with Node.js and Raspberry PI" You can create similar commercial domotics mobile app using only one language that can help you save time and costs. With the bunch of skillful JS developers in house, there’s a minimum to none need to hire experts in separate technologies (Raspberry Pi specialist, Android/iOS Native Developer). One person can control the entire development process.
If we reflect on a bit, there is an endless field of opportunities for Raspberry Pi and mobile devices. It can go far beyond home automation systems, it’s just a matter of skills, invention, state of innovations and imagination.
