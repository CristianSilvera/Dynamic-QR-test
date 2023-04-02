# Dynamic-QR-test

![image](https://user-images.githubusercontent.com/22043269/229323781-7de88dfc-3f31-4232-9013-eb7abf79188e.png)

## App script Dynamic QR code

``` function doGet(e) {
  if(!e.parameter.k)
    return ContentService.createTextOutput("");
  var k = e.parameter.k;
  var keys = SpreadsheetApp.getActive().getRange("Config!A3:A").getValues();
  var urls = SpreadsheetApp.getActive().getRange("Config!C3:C").getValues();

  for(var i=0;i<keys.length;i++){
    if(keys[i][0]==k){
      var url = urls[i][0];
      console.log(url);
      SpreadsheetApp.getActive().getSheetByName("Hits").appendRow([k,url,new Date()]);
      return ContentService.createTextOutput(url); 
    }
  }

  return ContentService.createTextOutput("");
}
