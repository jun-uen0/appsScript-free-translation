# appsScript-free-translation
Web API that contains google translate function, but it's completely free



If you use VS code and want to use JavaScript syntax for `.gs`
1. Click F1 and go to `settings.json`
2. Paste `files.association`
```
{
...
  "files.associations": {
    "*.gs": "javascript"
  }
...  
}
```

# Create WEB API using AppsScript
1. Enter to "[Apps Script Project](https://script.google.com) "
3. Chose "New Project"
4. Delete all code  "`function myFunction~`"
5. Paste code below ([translate.gs](https://github.com/JayU-ML/translate-with-gas/blob/main/translation.gs))
```
function doGet(e) {
    let p = e.parameter;
    let translatedText = LanguageApp.translate(p.text, p.source, p.target);
    let body;
    if (translatedText) {
        body = {
          code: 200,
          text: translatedText
        };
    } else {
        body = {
          code: 400,
          text: "Bad Request"
        };
    }
    let response = ContentService.createTextOutput();
    response.setMimeType(ContentService.MimeType.JSON);
    response.setContent(JSON.stringify(body));

    return response;
}
```


5. Click "Deploy"
6. Click gear icon and chose "Web App"

* **User who can access:  All**
