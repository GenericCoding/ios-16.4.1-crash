# ios-16.4.1-crash
Simple crash of Safari, demonstrating a POC for a crash described in a webkit commit

How to: Open index.html on your device (I used a webserver), and press share->print
The print preview will crash the app. May take several refreshes and attempts due to it being a timed condition. 

Explain: 

There is a conditional event listner with a short timer if the print preview is open, at which point the page contents is cleared.

the amount of total pages will change, and this triggers a kernel adress (0x8) to be called, which is then blocked and the application is terminated.

Lorem Ipsum is used to meet the condition of the initial print total number of pages being greater (181~, padded to add time to condition), than the number which it is changed to when the page is cleared. (1)
Source commit: 
https://github.com/WebKit/WebKit/commit/4456ae32f14391aefedccdc1a70b6c9d0205567d
