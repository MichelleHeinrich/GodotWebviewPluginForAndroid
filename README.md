# GodotWebviewPluginForAndroid

This is a simple android plugin to be used in Godot (tested with 4.4) and allows for webview access. 

What it does:
- allow http and https website access
- save and load last played video
- default website set to youtube.com
- choose to display either of the following from GDscript by choosing one of three arguments (default_url, lastUrl, inputUrl):
  a) default url (specify the url in your script),
  b) last visited url (plugin saves the last visited url; but need to use an argument) 
  c) user provided url; i.e. custom Url (for instance by linking it to LineEdit node for user input)

Functions/methods exposed to Godot (and can be used in GDscript):
  
  - openUrl(string url, string instanceName)
  - saveUrl(string instanceName)
  - openLastUrl(string instanceName)
  - onPause
  - onBackPressed

  What each function/method does in GDScript:
  - openUrl = opens an url that is either specfied as an argument locally or received by a signal with the url as the argument; if istance name is not null, it'll save that opened url as last url
  - saveUrl = saves the Url to a named instance (string argument); choose any instance name, perfect for managing webviews in separate nodes for which you want to keep the last url separated
  - openLastUrl = opens the last url by instanceName (string argument), and takes an url as another string argument to set a fallback url
  - onPause = saves the last visited url when the app is minimised (takes an instance name)
  - onBackPressed/OnKeyDown = webview isn't closed when going back
  
  
What it/you can't do: 
- specify trusted sites through the plugin but you should be able to disallow certain website by using a match or similar statement in GDscript

Possible use case:
- want to resume the url after app is minimised (Saves url as last visited when initially opened)
- want the user to choose between multiple website (you set the default ones in the script but the labels are whatever you like)
- allow ability to input their own, either from the get go or alongside the option of a default, or perhaps even last visited, url.

Known issues:
- none currently (18/03/2025)

Future plans:
- create an iOS plugin version (I don't own a mac and currently can't compile the plugin)
