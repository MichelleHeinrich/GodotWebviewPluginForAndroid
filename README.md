# GodotWebviewPluginForAndroid

This is a simple android plugin to be used in Godot (tested with 4.4) and allows for webview access. 

What it does:
- allow http and https website access
- save and load last played video
- default website set to youtube.com
- choose to display either of the following from GDscript by choosing one of three arguments (default_url, lastUrl, inputUrl):
  a) default url (specify the url in your script),
  b) last visited url (plugin saves the last visited url; but need to use this argument) 
  c) user provided url (for instance by linking it to LineEdit node for user input)
  
What it doesn't: 
- specify trusted sites

Possible use case:
- want to resume the url after app is minimised (Saves url as last visited when initially opened)
- want the user to choose between multiple website (you set the default ones in the script but the labels are whatever you like)
- allow ability to input their own, either from the get go or alongside the option of a default, or perhaps even last visited, url.

Known issues:
- none currently (18/03/2025)

Future plans:
- create an iOS plugin version (I don't own a mac and currently can't compile the plugin)
