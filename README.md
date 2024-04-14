# Rapport
Det första steget vara att skapa en fork av projektet på LenaSYS Github. Först ut var att ändra namnet på applikation samt att ge den tillgång till internet. Detta gjordes genom att att ändra _"app_name"_ i **strings.xml** till A new funny name. Internetåtkomst fixades enkelt genom att lägga till en extra kod rad i **AndroidManifest.xml**. 

**strings.xml**
```
<string name="app_name">A funny new name</string>
```
**AndroidManifest.xml**
```
<uses-permission android:name="android.permission.INTERNET"/>
```

Därefter lägga till en _WebView_ som skulle ersätta den tidigare _TextView_ (gick att byta typ). Denna webbvy fick sedan ett ID, **myWebView** som senare användes för att skapa en instans med hjälp av en funktionen _findViewById(R.id.myWebView)_. Detta skedde i funktionen _onCreate()_ i **MainActivity.java**.
```
android:id="@+id/myWebView"
```
```
// Member variable for WebView
private WebView myWebView;   
// Find webview by ID specified in layout file
myWebView = findViewById(R.id.myWebView);
```

Nästa steg var att skapa och lägga till en ny webb-klient för *myWebView* samt uppdaterades inställningarna för att tillåta JavaScript. Samtidigt lades en hemsida till för som visas när applikationen startar.
```
// Create and attach a new webview-client
WebViewClient myWebViewClient = new WebViewClient();
myWebView.setWebViewClient(myWebViewClient);

myWebView.loadUrl("https://his.se/");

// Enable JavaScript on client
myWebView.getSettings().setJavaScriptEnabled(true);
```

Uppgiften fortsätter sedan med att lägga till en ny .html fil som kommer att användas till den interna webbsidan. Denna html fil innehåller en titel, huvudrubrik samt en kort paragraf. 

Sista steget går ut på att implementera _showInternalWebPage()_ och _showExternalWebPage()_. I detta fall handlade det om att lägga till sökvägar i funktionen **loadUrl()** för att visa den specifika sidan.
Intern:
```
public void showInternalWebPage(){
    // TODO: Add your code for showing internal web page here
    myWebView.loadUrl("file:///android_asset/index.html");
}
```
Extern:
```
public void showExternalWebPage(){
    // TODO: Add your code for showing external web page here
    myWebView.loadUrl("https://github.com");
}
```

Slutligen uppdaterades även _onOptionSelected()_ för att kalla på de funktionerna så att innehållet visas i applikationen. 

Nedanför visas några skärmbilder från applikationen:
## Extern
![Screenshot_20240414_221935](https://github.com/a20gabpa/mobileapp-programming-webview/assets/102604680/f153055d-caad-4950-b025-23527f3b24bf)
## Intern
![Screenshot_20240414_221958](https://github.com/a20gabpa/mobileapp-programming-webview/assets/102604680/b6bcddcd-abc7-4f8c-b6ab-01a5252b1067)
## Startsida
![Screenshot_20240414_222013](https://github.com/a20gabpa/mobileapp-programming-webview/assets/102604680/7f209bdd-5165-4850-aeaa-aba9a3f70aed)
