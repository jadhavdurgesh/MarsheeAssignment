
https://github.com/user-attachments/assets/4f42b199-2a81-4b56-8270-876c862deae6

# Food Recipe App - Flutter

Theme Switching Implementation

This Flutter project includes a feature that allows users to toggle between light and dark themes dynamically using GetX for state management.

How Theme Switching is Implemented:

	1.	ThemeController:
The ThemeController is responsible for managing the theme state (light or dark) across the app. It uses an RxBool variable isLight to track the current theme state.

import 'package:flutter/material.dart';
import 'package:get/get.dart';

class ThemeController extends GetxController {
  // Observing the theme state
  RxBool isLight = true.obs;

  // Method to set theme
  void setTheme(bool value) {
    isLight.value = value;
    if (isLight.value) {
      // Apply light theme
      Get.changeTheme(ThemeData.light());
    } else {
      // Apply dark theme
      Get.changeTheme(ThemeData.dark());
    }
  }
}


	2.	Theme Toggling in the UI:
In the Introduction screen, an IconButton is used in the app bar to allow users to toggle between light and dark themes. The button updates the theme state via the setTheme method in the ThemeController.

import 'package:flutter/material.dart';
import 'package:get/get.dart';
import 'controller/theme_controller.dart';

class Introduction extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    final ThemeController themeController = Get.find<ThemeController>();

    return Scaffold(
      appBar: AppBar(
        actions: [
          // Obx(
          //   () => Switch(
          //       value: themeController.isLight.value,
          //       onChanged: (value) {
          //         themeController.setTheme(value);
          //       }),
          // ),
          Obx(
            () => IconButton(
              icon: Icon(
                themeController.isLight.value
                    ? Icons.dark_mode
                    : Icons.light_mode,
              ),
              onPressed: () {
                themeController.setTheme(!themeController.isLight.value);
              },
            ),
          ),
        ],
      ),
      body: Center(child: Text('Toggle the theme using the icon in the app bar!')),
    );
  }
}



Key Features:

	•	GetX State Management: The theme is managed globally using GetX’s reactive state management (Obx).
	•	Dynamic Theme Switching: Users can toggle between light and dark themes with a single tap on an icon button in the app bar.
	•	Icon Feedback: The icon dynamically changes to indicate the current theme (sun for light mode, moon for dark mode).

How to Use:

	1.	Clone the repository.
	2.	Run flutter pub get to install dependencies.
	3.	Run the app using flutter run.
	4.	In the app, tap the theme icon (sun/moon) in the app bar to toggle between light and dark themes.

Preview:

	•	Light Mode: 

	•	Dark Mode: 





https://github.com/user-attachments/assets/6330caa3-d7f8-4012-ad45-5a44faca389c






Download the apk from here : https://drive.google.com/file/d/16-Cdv01Ws6yhXKyhvYuh5efan2U5c3MX/view?usp=sharing


