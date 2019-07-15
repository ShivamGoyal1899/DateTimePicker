# How to build a Flutter DateTime Picker in just 15 minutes

## Introduction

With the [Flutter DateTime Picker plugin](https://pub.dev/packages/flutter_datetime_picker), you can add date & time pickers to your native application. The plugin’s interface is inspired by iOS Cupertino style menu.

### What you’ll build?

In this tutorial, you’ll build a mobile app featuring a DateTime Picker using the Flutter SDK. Your app will:

* Display separate Date & Time Pickers with a minimalistic interface

* Display the selected data as outputs to console

![That’s how our DateTime Picker gonna look](https://cdn-images-1.medium.com/max/4096/1*Q90FHAfT2z5cImKivaL9BA.png)*That’s how our DateTime Picker gonna look*

This tutorial focuses on adding a DateTime Picker to a Flutter app. Non-relevant concepts and code blocks are glossed over and are provided for you to simply copy and paste.

### Github Repository | @ShivamGoyal1899
[ ShivamGoyal1899/DateTimePicker 
*An app featuring DateTimePicker using the Flutter SDK - ShivamGoyal1899/DateTimePicker*github.com](https://github.com/ShivamGoyal1899/DateTimePicker)

### Package Used | flutter_datetime_picker
[ flutter_datetime_picker | Flutter Package 
*A date time picker for flutter, you can choose date / time / date&time in English Dutch and Chinese, and you can also…*pub.dev](https://pub.dev/packages/flutter_datetime_picker)

## Setting up Flutter on your machine

The detailed steps to install Flutter on your personal computer & getting started with Flutter is available at the following blog

[ How to install Flutter and create a simple Flutter app 
*Learn what is Flutter and how to set it up on Windows and Mac systems and get started with Flutter apps*medium.com](https://medium.com/enappd/install-flutter-on-windows-and-mac-1fd1dde453ba)

## Coding the component

### Component Syntax

The basic format of a DateTime Picker looks like the one below:

    FlatButton(
         onPressed : () {
            DatePicker.showDatePicker(context,
               showTitleActions : true,
               minTime : DateTime(2000, 1, 1)
               maxTime : DateTime(2022, 12, 31),
               onChanged : (date) {print('change $date');},
               onConfirm : (date) {print('confirm $date');},
               currentTime : DateTime.now(), locale: LocaleType.en);},
         child : Text('Show DateTime Picker',)
    );

### Adding DateTime Picker plugin as a dependency

Adding additional capability to a Flutter app is easy using [Pub packages](https://pub.dev/flutter). In this tutorial, you introduce the [DateTime Picker plugin](https://pub.dev/packages/flutter_datetime_picker) by adding a single line to the pubspec.yaml file.

<iframe src="https://medium.com/media/35e2e6922496e866ba2b9fb829d87a91" frameborder=0></iframe>

### Importing plugin to main.dart file

Import  flutter_datetime_picker  dependency to your main.dart file by adding the following line at the starting of the file:

     import  'package:flutter_datetime_picker/flutter_datetime_picker.dart';

### Putting Code in action

Amend your main.dart file as per the following code:

<iframe src="https://medium.com/media/8a842e663ded02fa79e9a68d06eab584" frameborder=0></iframe>

###  Building & running the application 

* Connect your Emulator or physical Android device to test the application.

* Click on Build & Run.

* And Boooom, your app is ready.
The final build would look like the below illustration.

![The final output of the implementation](https://cdn-images-1.medium.com/max/2000/1*yMUKAc0Z2tNcEV-eMI2UfA.gif)*The final output of the implementation*

## Customization Options

There are three functional variations of the plugin available as follows:

* Solo DatePicker

* Solo TimePicker

* Dual DateTimePicker

### Language Options

There are various language options available to implement the plugin for international use. For changing the language of the component amend the following with preferred  LocaleType .

    locale: LocaleType.en

* English(en)

* Persian(fa)

* Chinese(zh)

* Dutch(nl)

* Russian(ru)

* Italian(it)

* French(fr)

* Spanish(es)

* Polish (pl)

* Portuguese(pt)

* Korean(ko)

* Arabic(ar)

* Turkish(tr)

* Japanese(jp)

* German(de)

* Danish(da)

* Bengali(bn)

* Vietnamese(vi)

* Armenian(hy)

### Further Customisations

If you want to customize your own style of date time picker, there is a class called CommonPickerModel, every type of date time picker is extended from this class, you can refer to other picker models (eg. DatePickerModel), and write your custom one, then pass this model to showPicker method, so that your own date time picker will appear, it’s easy, and will perfectly meet your demand.

How to customize your own picker model:

 class CustomPicker extends CommonPickerModel  {
      String digits(int value, int length) {
         return  '$value'.padLeft(length, "0");
      }

    CustomPicker({DateTime currentTime, LocaleType locale}) :  super (locale: locale) {
         this .currentTime = currentTime ?? DateTime.now();
         this .setLeftIndex( this .currentTime.hour);
         this .setMiddleIndex( this .currentTime.minute);
         this .setRightIndex( this .currentTime.second);
      }

     @override 
      String leftStringAtIndex(int index) {
         if  (index >= 0 && index < 24) {
           return this .digits(index, 2);
        }  else  {
           return  null;
        }
      }

     @override 
      String middleStringAtIndex(int index) {
         if  (index >= 0 && index < 60) {
           return this .digits(index, 2);
        }  else  {
           return  null;
        }
      }

     @override 
      String rightStringAtIndex(int index) {
         if  (index >= 0 && index < 60) {
           return  this.digits(index, 2);
        }  else  {
           return  null;
        }
      }

     @override 
      String leftDivider() {
         return  "|";
      }

     @override 
      String rightDivider() {
         return  "|";
      }

     @override 
      List<int> layoutProportions() {
         return  [1, 2, 1];
      }

     @override 
      DateTime finalTime() {
         return  currentTime.isUtc
            ? DateTime.utc(currentTime.year, currentTime.month, currentTime.day,
                 this .currentLeftIndex(),  this .currentMiddleIndex(),  this .currentRightIndex())
            : DateTime(currentTime.year, currentTime.month, currentTime.day, this.currentLeftIndex(),
                 this .currentMiddleIndex(),  this .currentRightIndex());
      }
    }

## Enappd Store | Premium App Starters
[ Enappd | Ionic, React Native, Firebase themes, templates and starters 
*Get the full source code for Ionic, React Native, Firebase mobile app templates and starters. Use free templates and…*store.enappd.com](https://store.enappd.com/)

## More resources for Flutter

* [Getting Started with Flutter](https://medium.com/enappd/install-flutter-on-windows-and-mac-1fd1dde453ba)

* [Implementing Facebook Auth in Flutter](https://medium.com/enappd/flutter-tutorial-for-native-app-building-and-facebook-authentication-978f0ee44976)

* [Flutter Documentation](https://flutter.dev/docs)

* [Flutter Community](https://flutter.dev/community)

* [Flutter YouTube Channel](https://www.youtube.com/flutterdev)

* My GitHub Profile [@ShivamGoyal1899](https://github.com/ShivamGoyal1899)
