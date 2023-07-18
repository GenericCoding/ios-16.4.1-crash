# ios-16.4.1-crash
Simple crash of Safari, demonstrating a POC for a crash described in a webkit commit

How to: Open index.html on your device (I used a webserver), and press share->print
The print preview will crash the app, and give you a crash log stack tracing the crash. 
Explain: 
There is a conditional event listner for if the share preview is open, at which point the page contents is cleared. 
This is due to a timing preview bug wherein if there is a delay between the eventlistner, and the time the preview is rendered 
the amount of total pages will change, and this triggers a kernel adress (0x8) to be called, which is then blocked and the application is terminated.

Source commit: 
https://github.com/WebKit/WebKit/commit/4456ae32f14391aefedccdc1a70b6c9d0205567d
