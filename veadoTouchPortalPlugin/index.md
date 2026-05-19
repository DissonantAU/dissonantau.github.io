---
layout: default
title: veadotube Plugin for Touch Portal
description: A plugin to control veadotube with Touch Portal

show_repo_link: true
repository_url: https://github.com/DissonantAU/VeadotubeTouchPortalPlugin

show_latest_release: true
latest_release_url: https://github.com/DissonantAU/VeadotubeTouchPortalPlugin/releases/latest
latest_release_version: 0.8.3-beta
---

_This is an **unofficial plugin**, please don't harass the devs of either program if you have issues with the plugin._  
_This Plugin is free, but you need to buy the Touch Portal Pro upgrade to install and use Plugins._

[![Made for Touch Portal](img/logos/madeForTPWhite_256.png)](https://www.touch-portal.com)
[![Veadotube](img/logos/veado_outline_512.png)](https://veado.tube)

## Table of Contents

<!-- TOC -->
  * [Table of Contents](#table-of-contents)
  * [Requirements](#requirements)
  * [Releases](#releases)
  * [Getting Help](#getting-help)
  * [Links](#links)
  * [License](#license)
  * [Installing the Plugin](#installing-the-plugin)
  * [Plugin Settings](#plugin-settings)
* [Setting up Pages in Touch Portal for veadotube mini](#setting-up-pages-in-touch-portal-for-veadotube-mini)
  * [Basic Button Setup](#basic-button-setup)
  * [Reactive Buttons](#reactive-buttons)
  * [Use Current Avatar State as an Icon](#use-current-avatar-state-as-an-icon)
  * [Show active Avatar State name](#show-active-avatar-state-name)
  * [Advanced - Custom JSON Requests](#advanced---custom-json-requests)
  * [Advanced - Multiple Instances](#advanced---multiple-instances)
  * [Advanced - Plugin Refresh Buttons](#advanced---plugin-refresh-buttons)
* [Setting up Pages in Touch Portal for veadotube](#setting-up-pages-in-touch-portal-for-veadotube)
  * [Enable Websocket in veadotube](#enable-websocket-in-veadotube)
  * [Example Scene](#example-scene)
    * [Creating and Getting State Values](#creating-and-getting-state-values)
      * [Using Scene State Groups to Show/Hide Avatars](#using-scene-state-groups-to-showhide-avatars)
    * [Change by Windows Title](#change-by-windows-title)
    * [Mic Mute Example](#mic-mute-example)
    * [Other Examples](#other-examples)
<!-- TOC -->


## Requirements

- Java 8 Runtime or later
- Touch Portal (The pro upgrade bought through the Android/iOS Store needed to use Plugins)

And one of both of the following:
- veadotube Mini v2.0 or higher (Older versions are NOT supported)
- veadotube v0.6 (Access is currently in [early access](https://olmewe.itch.io/veadotube-mini/devlog/914644/the-april-twenty-twenty-five-devlog))

## Releases

The [latest version](https://github.com/DissonantAU/VeadotubeTouchPortalPlugin/releases/latest) is 0.8.3.

- Beta release - stable enough for general use but testing is ongoing.
- Tested with
  - **veadotube mini v2.0a**, **v2.1**, & **v2.2** 
  - **veadotube v0.6**
- The following features are planned before 1.0 release
  - Update Notification (In place but not fully tested)
  - Actions for controlling specific named instances (In place for veadotube but not fully tested, not complete for Mini)

All releases are [available here](https://github.com/DissonantAU/VeadotubeTouchPortalPlugin/releases).

## Getting Help
The easiest way to get help is to ask in the [Touch Portal Discord](https://discord.gg/MgxQb8r) under **Plugins > Streaming** > **Veadotube**


## Links
- [Project GitHub](https://github.com/DissonantAU/VeadotubeTouchPortalPlugin)
- [Veadotube](https://veado.tube)
- [Touch Portal](https://www.touch-portal.com)
- [BleatKan Library](https://github.com/DissonantAU/bleatkan)
- [Touch Portal Plugin SDK](https://github.com/ChristopheCVB/TouchPortalPluginSDK)


## License
- This Plugin Licensed under GPL v3, and is Free to use in accordance with any Licenses and Agreements

---

## Installing the Plugin
1. Download the latest release from GitHub
   - There are 2 Versions: 'Regular' and 'Internal'/'Bundled' Java.
     - 'Regular' Requires Java 8 or later installed and works on Windows/MacOS/Linux.
       - **If in doubt, install Java and use this version.**
     - 'Internal Java' uses the version of Java Bundled with Touch Portal (JRE 17).
         - Doesn't require Java installed separately and tends to use less CPU and Memory.
         - This is tested as working on Windows, but macOS and Linux _may_ have issues.
2. Import the plugin into Touch Portal on the computer veadotube is running on  
  ![Screenshot of Touch Portal Plugin Screen](img/screenshots/plugin-import-1.png)
3. Touch Portal will show a warning, asking if you want to allow the Plugin to run.  
  Select **Yes** or **Trust Always** to let it run
  **Yes** will make Touch Portal ask you again each time it starts  
  ![Screenshot of Touch Portal Plugin Warning](img/screenshots/plugin-import-2.png)


## Plugin Settings
_These are optional, but you will want to enable **Auto Request Current State Thumbnail** if you plan to have Touch Portal display a State/Avatar_  
![Screenshot of veadotube Plugin Settings Panel in Touch Portal](img/screenshots/plugin-options.png)

**Primary Instance Name Override (mini)**  
If you run more than one copy of veadotube mini and have changed the window title, you can enter it here to force the plugin to treat it as the 'Primary Instance' when control it.  
_Note: If nothing is entered, or if no match is found, the **oldest** running window/instance is controlled by default_

**Auto Request Current State Thumbnail**  
If you want a Button to show the thumbnail current Avatar State, type 'enable' and the plugin will fetch it for you

**Example:**  
_Only one copy of veadotube Mini is running, it has the default title._  
_A Primary Instance name has been entered, but no mini with the title is running - the plugin has fallen back to the oldest instance._  
_'enable' has been entered for Auto Request Thumbnail_  
![Screenshot of Touch Portal Plugin Screen with example settings](img/screenshots/plugin-settings-example.png)  


# Setting up Pages in Touch Portal for veadotube mini
**You can find an example Touch Portal Page you can download and import [here](https://github.com/DissonantAU/VeadotubeTouchPortalPlugin/tree/main/touchPortalPageExample)**

The example page and the examples below use one of the default avatars, _O Gato by BELLA!_  
You can find it in veadotube Mini by clicking _Avatar Settings > Load Default Avatar..._  
![Screenshot of the Example Touch Portal Page on Android](img/screenshots/example_button_adv_2.png)



## Basic Button Setup
The Plugin Actions can be found under **Veadotube - Primary Instance**

**Basic Avatar Change Trigger**
1. Make sure you have the Avatar you want to use open in veadotube

2. Add **Set Primary Mini Avatar State from List** to your button
   - Alternatively you can use **Set Primary Mini Avatar State by Name** if you'd prefer to use a text box or Touch Portal Value to set the name

3. Set the avatar you want this button to activate. 
   - If using **Set Primary Mini Avatar State from List**, click the dropdown arrow to show all the current Avatars.
     You will see the state name, or number assigned by veadotube if you didn't set one.  
    ![Screenshot of the Touch Portal showing 'Set Avatar State to' and a dropdown list with Avatar States](img/screenshots/example_button_1.png)  
   - Alternatively if you're using **Set Primary Mini Avatar State by Name**, you can copy & paste the State name from veadotube into the text box.  
    ![Screenshot of the Touch Portal showing 'Set Avatar to State with Name' and a text box with the name #3](img/screenshots/example_button_2.png)  

   **Note:** Changing the name of a State in veadotube will break your Touch Portal buttons - you will need to come back and update the buttons of any you change.

4. Set the Button Text, Background, etc.  
   ![Closer Screenshot of the Touch Portal showing a button labeled "Change to #1" 'Set Avatar State to' with State #1 selected](img/screenshots/example_button_3.png)  

5. Repeat with other buttons

![Screenshot of veadotube with State #2 selected and open so the State Name is visible](img/screenshots/example_button_4.png)
_Opening the avatar state in veadotube shows the name box - you can copy this into Touch Portal text boxes_

You can now press the buttons and change the active avatar!  
Note: Here **When Plug-in state changes** has been used to make the buttons reactive - If you want buttons to change with the state, even when changed directly in veadotube, see under _Advanced Buttons_ below

![Screenshot of the Example Touch Portal Page on Android with 3 Example Change Buttons. State #3 showing as an Icon](img/screenshots/example_button_adv_4.png)
_After Pressing Button #3_

![Screenshot of the Example Touch Portal Page on Android with 3 Example Change Buttons. Now State #1 showing as an Icon](img/screenshots/example_button_adv_2.png)
_After Pressing Button #1_



## Reactive Buttons
You can set up the buttons to react to the Avatar State Changing - this also works if you change it by clicking directly in veadotube

Add:
1. _Event: When Plugin State Changes_  
   Choose _Veadotube Plugin > Primary Instance > Current Avatar State - Name_  
   ![Screenshot of the Touch Portal showing 'When the plugin State' event as Current State Avatar - Name changed to #1 and the Change Button Visuals action set to change the background colour to Green and Gray. A Do not Change to #1 Event has the 'Restore Button visuals for' 'Background settings' inside](img/screenshots/example_button_adv_1.png)

2. Set the 2nd box to 'changes to' and the 3rd to the Avatar Name (you can copy and paste this from veadotube)

3. Add a _Change Button Visuals_ action inside the event and choose how you want the button to show the Avatar State is active

4. Copy the _When Plugin State Changes_ event but set the 2nd box to _does not change to_ and add a _Restore button visuals_ action

5. Repeat on your other buttons

Now you can see which avatar is active by the button that's highlighted

![Screenshot of the Example Touch Portal Page on Android with 3 Example Change Buttons. Change to #1 Button is Green-Gray and State #1 showing as an Icon](img/screenshots/example_button_adv_3.png)
_Avatar State #1 is Active_

![Screenshot of the Example Touch Portal Page on Android with 3 Example Change Buttons. Change to #3 Button is Green-Gray and State #3 showing as an Icon](img/screenshots/example_button_adv_4.png)
_Avatar State #3 is Active_


## Use Current Avatar State as an Icon
If you've enabled _Auto Request Current State Thumbnail_ you can create a 'button' that shows the current Avatar

You can create this by adding:
1. Event: When Plugin State Changes  
   Choose _Veadotube Plugin > Primary Instance > Current Avatar State - Thumbnail_

   ![Screenshot of the Touch Portal showing 'When the plugin State' event and the plugin state dropdown open to 'Veadotube Plugin', 'Veadotube Primary Instance' and 'Current Avatar State - Thumbnail' highlighted](img/screenshots/example_button_icon_1.png)

   Set the 2nd box to _does not change to_, and leave the 3rd box blank
   ![Screenshot of the Touch Portal showing 'When the plugin State' event, the plugin state 'Current Avatar State - Thumbnail' chosen, 'does not change to' chosen and a blank text box](img/screenshots/example_button_icon_2.png)

2. Inside the Event, add _Change visuals by Plugin State_ and select _Icon_ and _Current Avatar State - Thumbnail_  
   ![Screenshot of the Touch Portal showing 'When the plugin State' event with Change Visuals by plug-in state action. It is set to change the Icon with the value from "Current Avatar State - Thumbnail"](img/screenshots/example_button_icon_3.png)

Now the Icon will change when the Avatar does - even if it's changed directly in the app!



## Show active Avatar State name
You can set a 'button' to show the name of the currently active avatar

Add:
1. _Event: When Plugin State Changes_

   Choose _Veadotube Plugin > Primary Instance > Current Mini Avatar State - Name_ and _does not change to_
   ![Screenshot of the Touch Portal showing 'When the plugin State' event as 'Current State Avatar - Name' does not change to blank and the Change Button Visuals action set to change Text. The Text Box is empty](img/screenshots/example_button_name_1.png)  
    _You can leave the next box blank to only change when the value is not blank, or enter something else (e.g._ ` _) to also change when the value is cleared._

2. Add a _Change Button Visuals_ action inside the event and set it to use the Name to change the button text
   ![Screenshot of the Touch Portal showing 'When the plugin State' event as 'Current State Avatar - Name' does not change to blank and the Change Button Visuals action set to change Text. The Variable selector is open to Veadotube Plugin, Primary Instance, 'Current Mini Avatar State - Name'](img/screenshots/example_button_name_2.png)  
   ![Screenshot of the Touch Portal showing 'When the plugin State' event as 'Current State Avatar - Name' does not change to blank and the Change Button Visuals action set to change Text.](img/screenshots/example_button_name_3.png)  
   _You can add other Text to the change action as well_

The Button should now show the current active Avatar Name


## Advanced - Custom JSON Requests
You can send custom JSON Messages to the API, useful if you want to use an API feature that's not supported directly by this plugin
![Screenshot of the Touch Portal showing 'Send Custom JSON Request' with 'nodes' in the channel text box and a JSON Message String to set the avatar state to '#2'](img/screenshots/example_button_5.png)  
_In this example you can see a Custom JSON Request to set the avatar state to '#2' to be sent to the 'nodes' channel_

## Advanced - Multiple Instances
You can manage multiple mini instances at the same time though *Instance Numbers* and *Titles*  
**Note: Currently functions for Sending commands by Title aren't available for Mini, but values are accessible as Plugin States**

**Instance Numbers** are based on the order that each instance started (1 is first) and that number is held until it is fully closed.  
- The number will persist even if websockets are turned off and on again and will only clear on full close, after which a newly started instance can take it.

**Instance Titles** are a shortened, version of the title with the start ('veadotube mini - ') and some character types removed.  
- If an instance doesn't have a custom title, the mini 'ID' generated at launch is used instead.  
If the Title is updated, the old title values will be deleted and new ones for the new title will be created.


**Titles and Numbers of Instances are also available under _Mini Instances > Active Mini Instances_**
![Screenshot of the Touch Portal showing veadotube mini Dynamic Text Variable 'Active Mini Instances'](img/screenshots/example_mini_instNum_1.png)

**Dynamic Plugin Variables**
![Screenshot of the Touch Portal showing veadotube mini Dynamic Text Variables by Instance Number](img/screenshots/example_mini_instNum_2.png)  
![Screenshot of the Touch Portal showing veadotube mini Dynamic Text Variables by Instance Title](img/screenshots/example_mini_instNum_3.png)  

Depending on your version of Touch Portal, the Instance values may appear under 'Dynamic States' instead of Mini Number or Mini (Title)
![example_mini_instNum_4.png](img/screenshots/example_mini_instNum_4.png)


Similar to the Primary Instance, commands can be sent using **Change Avatar State**
![Screenshot of the Touch Portal showing veadotube mini Instance Number Change Avatar State'](img/screenshots/example_mini_instNum_5.png)

_Button active in Touch Portal_
![tempFileForShare_20260519-212443.png](img/screenshots/example_button_adv_2.png)

## Advanced - Plugin Refresh Buttons
You can create buttons to Force a refresh of the State List or current State.  
![Screenshot of the Touch Portal showing 'Refresh Avatar State List' and 'Refresh Current Avatar State' Actions under On Pressed Actions](img/screenshots/example_button_refresh_1.png)    
You won't need these normally:
- The Plugin will be told when the State is switched (any veadotube version).  
- Newer versions (mini 2.1+) send API updates when a State is _edited_ (e.g. order/name/image changed), so state lists will update automatically.  
- Older versions (e.g. mini 2.0a) need to be forced to refresh State Lists using this command after edits, or by restarting either Touch Portal or veadotube.  


# Setting up Pages in Touch Portal for veadotube
**You can find an example Touch Portal Page you can download and import [here](https://github.com/DissonantAU/VeadotubeTouchPortalPlugin/tree/main/touchPortalPageExample)**

The example page and the example images below use one of the default avatars mini avatar, _O Gato by BELLA!_  
You can find it in veadotube Mini by clicking _Avatar Settings > Load Default Avatar..._

## Enable Websocket in veadotube
Websocket can be enabled under Edit > Settings  
![example_veado_websocket_1.png](img/screenshots/example_veado_websocket_1.png)  
![example_veado_websocket_2.png](img/screenshots/example_veado_websocket_2.png)

## Example Scene
![example_veado_overview.png](img/screenshots/example_veado_overview.png)

### Creating and Getting State Values
Right-Click the State Websocket and copy the ID (Make sure IDs in the scene are unique)  
![example_veado_state_1.png](img/screenshots/example_veado_state_1.png)

Add the Action 'Instance #: Change State Node by ID' and pase in the Websocket Node ID  
![example_veado_state_2.png](img/screenshots/example_veado_state_2.png)

Get the name of the State Name/ID (Shown here by Right-Clicking State Storage, and clicking Set to bring up the list)  
![example_veado_state_3.png](img/screenshots/example_veado_state_3.png)

Enter the ID and select the action  
![example_veado_state_4.png](img/screenshots/example_veado_state_4.png)

Pressing the button changes the state to #5. You can see the action stored in the 
![example_veado_state_5.png](img/screenshots/example_veado_state_5.png)

The Button can be made Reactive using the state under Full (Title) or Dynamic States. User Current State ID
The item will have the Websocket Node Name
![example_veado_state_6.png](img/screenshots/example_veado_state_6.png)


#### Using Scene State Groups to Show/Hide Avatars
Similar to above, Scene States can be controlled

Click the + to create a new State Group - a State Group Object will Spawn in the Node editor
![example_veado_stateGroup_1.png](img/screenshots/example_veado_stateGroup_1.png)

Name the 1st slot (e.g. 1x), make sure it's selected.  
Click the Eyes next to each object to Unhide the 'main' avatar and Hide the 'secondary'.  
They should be green to indicate the setting is changed in the selected (Note that 'Off' is the  
![example_veado_stateGroup_2.png](img/screenshots/example_veado_stateGroup_2.png)

Add a second State, enable both avatars. Select both and adjust the Size/Position/etc.
![example_veado_stateGroup_3.png](img/screenshots/example_veado_stateGroup_3.png)


Find the Scene State Group object that was spawned in the node editor, attach a State Storage to the node, and attach a State Events Websocket object to that.  
![example_veado_stateGroup_4.png](img/screenshots/example_veado_stateGroup_4.png)

Get the ID of the Websocket node (activeAvatars)
![example_veado_stateGroup_5.png](img/screenshots/example_veado_stateGroup_5.png)

Create a Button with Chance State Node by ID, enter the Websocket node ID and State Group Name (1x)  
![example_veado_stateGroup_6.png](img/screenshots/example_veado_stateGroup_6.png)

Repeat for each State

### Change by Windows Title
The Window Title can also be used instead of Instance Number to select where to send commands and what values to get.  
This is useful if you want to run multiple windows and want buttons etc to only act/react for one Scene file and don't want to worry about start order (and don't care about reusing them across files)  
![example_veado_instanceTitle_1.png](img/screenshots/example_veado_instanceTitle_1.png)

Using the veadotube Full Title Action, enter all or any part of the Title can be used to choose the veadotube window that will be sent a command (excluding the Star (*) that shows if the Scene is unsaved)  
_Note: Each active connection title is checked, oldest to newest, and the **first** match is used. In this example, 'veadotube' will match **any** window, so the first one launched is sent the command_  
![example_veado_instanceTitle_2.png](img/screenshots/example_veado_instanceTitle_2.png)

Under the Full (Title) or Dynamic Values Menu, select find the value staring with **Instance (_End of Title_) (_Instance Number_)**  
In this example, **Instance TouchPortal_Example_Scene.veadoscene (#1)**  
![example_veado_instanceTitle_3.png](img/screenshots/example_veado_instanceTitle_3.png)  
![example_veado_instanceTitle_4.png](img/screenshots/example_veado_instanceTitle_4.png)


### Mic Mute Example
Insert a Branch on Boolean Node after the Mic Activity Slider on the False Node, and add a Websocket Boolean Node to the Boolean Value  
![example_veado_mic_1.png](img/screenshots/example_veado_mic_1.png)

Get the Boolean Node ID  
![example_veado_mic_2.png](img/screenshots/example_veado_mic_2.png)

Create a Button with Change Boolean by Node ID, set the Node ID and action (Toggle in this case)
![example_veado_mic_3.png](img/screenshots/example_veado_mic_3.png)

Optionally, use the Node Value to change the button when the Value Changes
![example_veado_mic_4.png](img/screenshots/example_veado_mic_4.png)

Test the button - when true, Mic input is disconnected  
![example_veado_mic_5.png](img/screenshots/example_veado_mic_5.png)

### Other Examples
**Show Instance #1 Title**  
![example_veado_otherEx_title_1.png](img/screenshots/example_veado_otherEx_title_1.png)

Uses 'does not change to' tick (`) to show current value (including blank)
![example_veado_otherEx_title_2.png](img/screenshots/example_veado_otherEx_title_2.png)


**Show Connected/Disconnected**  
Using Plug-in State Title with 'changes to'/'does not change' to blank to change the text  
![example_veado_otherEx_connDisc_1.png](img/screenshots/example_veado_otherEx_connDisc_1.png)

![example_veado_otherEx_connDisc_2.png](img/screenshots/example_veado_otherEx_connDisc_2.png)