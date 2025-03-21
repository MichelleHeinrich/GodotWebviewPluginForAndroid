# GodotWebviewPluginForAndroid

This is a simple android plugin to be used in Godot (tested with 4.4) and allows for webview access. 

What the plugin does:
- display any url in a webview (using openUrl)
- save and load last visited url (using saveUrl and openLastUrl)
- set a default website (using openUrl)
- allow users to input an url to be displayed in a webview (Noted: you need to use signals and pass the input url as an argument to openUrl)
- NOTE: none of these are global settings, so a link set in one script won't affect the url in another; kept separate by using instanceName (string argument) so any instance can have their own save and last visited url


Functions/methods exposed to Godot (and can be used in GDscript):
  
  - openUrl(string url, string instanceName)
  - saveUrl( string url, string instanceName,)
  - openLastUrl(string defaultUrl, string instanceName,)
  - onPause
  - onBackPressed

  What each function/method does in GDScript:
  - openUrl = opens an url that is either explicitly stated or received by a signal with the url as the argument; if istance name is not null, it'll save that opened url as last url (calls saveUrl)
  - saveUrl = saves the url to a named instance (string argument); choose any instance name, perfect for managing webviews in separate nodes for which you want to keep the last url separate
  - openLastUrl = opens the last url by instanceName (string argument), and takes an url as another string argument to set a fallback/default url
  - onPause = saves the last visited url when the app is minimised (takes an instance name)
  - onBackPressed/OnKeyDown = webview isn't closed when going back
  
  
What it/you can't do: 
- specify trusted sites through the plugin though I imagine you could do so through GDscript

Possible use case:
- want to resume the url after app is minimised (Saves url as last visited when initially opened)
- want the user to choose between/from multiple website (you set the default ones in the script but the labels are whatever you like)
- allow ability to input their own, either from the get go or alongside the option of a default, or perhaps even last visited, url.

Known issues:
- none currently (18/03/2025)

Future plans:
- create an iOS plugin version (I don't own a mac and currently can't compile the plugin)
