# Google Script For Email Notification
---
```
function email_high() {
  
   //var currentStatus, statusFromSS;
  
  //var ssNotiStatus =
      SpreadsheetApp.openById("1YXoYv2f4yBUP0KtlIU1tbRVn9bjeDWICJ9R7x2tDla8");
  //var sheetNotiStatus =ssNotiStatus.getSheets()[0];
  //statusFromSS = sheetNotiStatus.getRange(2,1).getValue();
  
  //currentStatus = statusFromSS;
  var ssCurr = SpreadsheetApp.getActiveSpreadsheet();
  var sheetCurr = ssCurr.getSheets()[0];
  var lastRowNum= sheetCurr.getLastRow();
  
  var current_noise = sheetCurr.getRange(lastRowNum, 2).getValue();
  var prev_noise = sheetCurr.getRange(lastRowNum-1, 2).getValue();
  var timestmp = sheetCurr.getRange(lastRowNum, 1).getValue();
  
  
  if (current_noise >20 && prev_noise <20) {
    var emailSubject = "\[Alert\] pet shop alert: High level noise ";
  var emailrecipientto ="chungangster18@gmail.com";
    var emailmessage ="Data from sensor <p> Noise: " +current_noise + "<p>Time: " +timestmp;
    
    
    MailApp.sendEmail(
          { to: emailrecipientto,
          subject: emailSubject,
           htmlBody: emailmessage}
        )


  } // end if

  
}
```
