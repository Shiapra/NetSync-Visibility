# What is NetSync Visibility?

This prefab gives you specific controls over whats visible on your avatar and to who + It’s easy to set up!

There are 5 visibility options
- Off
- Self Only
- Friends Only
- Everyone
- Secret Mode

## What is Secret Mode?

Secret mode allows you to show things with **specific people** in an instance!

Simply walk up to each other and use the Send Secret Menu option at the same time. The best part is you only need to do this once per instance.

Changing between visibility modes will not overwrite if someone has already synced with you, this means if you change to Local Only, then return to Secret mode later, you wont need to re-send your secret with that person, it will persist for the entire time your avatar is loaded.

You can also disable this in settings, disabling it will immediately reset the saved secret for anyone you have synced with.

You must both be sending a secret at the same time for you to see each others hidden objects, this prevents abuse by others who may try to send a secret without your consent.

For further protection, by default secrets are restricted to friends only, you can change this in the radial menus.

## Performance Ranking
- Synced bits: 10
- Senders: 1
- Receivers: 1

# How do I Get this?
I've made a free repo for the Creator Companion!

Just add it to your VCC by going to: https://vcc.shia.gay/free
or add it manually with the same URL

## VRCFury
You will need the VRCFury Repository too, so if you get an error, check that it’s on your VCC

It can be added by visiting https://vrcfury.com/download or adding https://vcc.vrcfury.com to your VCC

# Setting Up in Unity

After you've added the prefab to your project, nativate to ```Packages > Shiapra - NetSync Visibility``` in your Project Files, then drag and drop the ```NetSync Visibility Prefab``` onto your Avatar.

Then Just drop whatever you want to hide under ```NetSync Visibility Prefab > NetSync Object``` on your avatar! 

If you need to hide more items that don't automatically re-parent to your avatar, or need to be under a specific bone, drag and drop the ```Object - Netsync``` prefab into the same area of your Heirarchy and put the items you wish to hide under that.

## Complex Items & Usage in Animators

If what you need to hide is more complex, add the ```NetSync_Toggle``` parameter to your animator as a _boolean_ or _float_, then use it to control the transition states or blend values in your animator. 

The NetSync Prefab will set this to ```True``` or ```1``` when something should be visible to a user. You don't need to handle any other visibility logic.

**DO NOT**: Add the parameter to your VRChat parameters menu, it will automatically be added by VRCFury. If the NetSync toggle parameter is accidentally set to **Sync** this will cause all visibility settings to be visible to **EVERYONE** 

I do not recommend using any of the other parameters from the NetSync Prefab, the only parameter that is expected to be used outside of the prefab is the **NetSync_Toggle Boolean**

## Write Defaults

The Write Defaults of your avatar is the state the objects and components on your avatar was in at the time of upload. This means any objects enabled in the heirarchy, shapekey values set, etc. 

Each NetSync object uses both a VRCFury toggle and a VRCFury Apply During Upload Script. THIS IS IMPORTANT.

VRCFury toggles state that they will automatically disable the object, this is true.  **HOWEVER,** they do NOT disable the component in the heirarchy at upload time, only during runtime when you avatar is loaded in game. 

This means that without the Apply During Upload component, all objects would be visible to anyone who has animators disabled & in impostors.

## Objects with pre-exisiting toggles
If an object already has a toggle on it, placing it under the NetSync Object prefab will override its toggle, although you will still need to enable that second toggle in your menu in game.

I would recommend either removing redundant toggles (unless you want those to be individually toggleable, such as conflicting items) or using the ```NetSync_Toggle``` parameter directly in the exisitng toggle.

If the toggle is a VRCFury toggle, you can do this by modifying the toggle to use a **Global Parameter** and use the ```NetSync_Toggle``` parameter.

Please note that this parameter is always being driven, so it can not be disabled outside of the NetSync Menu

# Usage in Game

You will find a new menu called ```NetSync``` with all the visibility settings.

Changing between settings will cause all objects to breifly be disabled and re-enabled, this is intentional to make sure the NetSync_Toggle Boolean is always being written to & to avoid more complex logic that might break.
If this becomes an issue for you, or breaks certain prefabs, please make an issue request and let me know. 

## Nothing Visible?
Check to make sure the objects you're trying to toggle don't already have another toggle to enable or disable them, you might need to enable that toggle too, or remove it in unity.

# Can I use this in a product?
Yes! You are welcome to use NetSync Vsibility in your product!

Ideally the end user should be directed to add NetSync Visibility to their project via the VCC URL, and modifications/additions you make should be additive to the base NetSync Visibility animator & Prefabs.

Please credit the NetSync Visibility project on your product page if you use it in your product!

## Some things to keep in mind
Please keep your modified versions of NetSync Visibility compatible with the NetSync Visibility Project. The goal of this system is to create a unified tool to sync with others in game, this becomes very difficult if your fork becomes incompatible with everyone elses!

If you wish to integrate the controls into your own menus rather than use the included menu, please maintain feature parity. 

The License for NetSync Visibility is Copyleft, any modifications you make should be available to the project. Please just fork this repository and commit your changes to your fork. If you're unfamiliar with github and forking, please just provide a copy of the modified animator, menus and prefabs if asked.

