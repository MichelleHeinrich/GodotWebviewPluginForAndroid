# GodotWebviewPluginForAndroid

This is a simple android plugin to be used in Godot (tested with 4.4) and allows for webview access. 

What the plugin does:
- display any url in a webview (using openUrl)
- save and load last visited url (using saveUrl and openLastUrl)
- set a default website which is a url you explicitly code in GDscript (using openUrl)
- allow users to input an url to be displayed in a webview (Noted: you need to use signals and pass the input url as an argument to openUrl)
- NOTE: none of these are global settings, so a link set in one script won't affect the url in another; kept separate by using instanceName (string argument) so any instance can have their own save and last visited url


Functions/methods exposed to Godot (and can be used in GDscript):
  
  - openUrl(string url, string instanceName)
  - saveUrl(string url, string instanceName,)
  - openLastUrl(string defaultUrl, string instanceName)
  - onPause
  - onBackPressed

  What each function/method does in GDScript:
  - if an instanceName is null, openUrl won't save the url as last visited, and saveUrl won't save the last visited url properly
  - openUrl = opens an url that is either explicitly stated or received by a signal with the url as the argument; if istance name is not null, it'll save that opened url as last url (calls saveUrl)
  - saveUrl = saves the url to a named instance (string argument); choose any instance name, perfect for managing webviews in separate nodes for which you want to keep the last url separate
  - openLastUrl = opens the last url by instanceName (string argument), and takes an url as another string argument to set a fallback/default url
  - onPause = saves the last visited url when the app is minimised (takes an instance name)
  - onBackPressed/OnKeyDown = webview isn't closed when going back

  Use cases: 
  - want the user to press a button upon which a webview is opened in a specific node
    - you create a signal for the button that will pass the url to the node that is connected to this signal
    - this url could be a custom url that the user of the app input through the ui BUT without the signal this custom url can't reach the openUrl function
    - it could also be a default url that you defined in your script and won't change; send that url as a signal to the connected node by passing the default urk as a signal argument
  - want to display a website without any user input
    - you can load the last visited url (lastLastUrl), or if none exist, the url you specify as an argument in openLastUrl will be opened; no signals needed
    - you can load a default url that you hard code in GDscript as an argument in openUrl
 - mix and match
     - load the last visited url in a node (which would happen when scene is initialised) but allow the user to choose a different default/set url or input their own (using buttons)
    - you could create a menu with multiple options (one or multiple default url, user input, last visited) and send a signal to where you run openURL (if default or input) or loadLastUrl(pass instanceName as signal argument)
  
What it/you can't do: 
- specify trusted sites through the plugin though I imagine you could do so using GDscript by handling url names (match string or the like)


Known issues/limitations:
- none currently (18/03/2025)
- save url to preferences each time the url changes; currently it saves when app is minimised (onPause) or is opened (saveUrl)

Future plans:
- create an iOS plugin version (I don't own a mac and currently can't compile the plugin)
