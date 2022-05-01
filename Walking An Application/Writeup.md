Local IP - 10.4.65.102
Victim IP - 10.10.137.4

https://10-10-137-4.p.thmlabs.com

Navigating to the webpage above reveals multiple sub pages and directories
Inspecting the source code reveals a comment that appears to be another webpage under the directory `/new-home-beta`
Navigating here reveals the 1st flag.

![](Screenshots/new-home-beta_comment.png)
![](Screenshots/flag_1.png)


I continued to search through source code & located a "secret page" class.  Navigating to the webpage with the /secret-page added to the end reveals flag 2.

![](Screenshots/secret_page.png)
![](Screenshots/flag-2.png)


The source code also reveals an image called staff.png located under /assets.  Now I can attempt to navigate to the /assets directory.  I click on the image and remove staff.png from the URL and locate a hidden directory with a flag.txt file for flag 3.

![](Screenshots/staff_png_photo.png)
![](Screenshots/staff_png_url.png)
![](Screenshots/flag_3.png)

The source code also reveals a comment with another web page that reveals webpage with sub pages, home, change log and documentation.

![](Screenshots/URL_static_labs.png)
![](Screenshots/THM_framework_page.png)


Navigating to Change log reveals a file in a web directory called /tmp.zip.  Altering the url to `https://10-10-137-4.p.thmlabs.com/tmp.zip` prompts to save a zip file.  Opening that reveals flag 4.

![](Screenshots/change_log.JPG)
![](Screenshots/tmp_zip.png)
![](Screenshots/flag_4.png

Navigating back to the main link https://10-10-137-4.p.thmlabs.com/ and to the sub page news reveals an article hidden behind a paywall. (Note IP has changed to 10.10.153.143)
Inspecting the source code here reveals a line `<div class="premium-customer-blocker">` which appears to block the display.  Changing this to `none` and refreshing the page reveals another flag.
![](Screenshots/Paywall.png)
![](Screenshots/Inspect_element_div_class.png)
![](Screenshots/flag5_display_none.png)

Navigating to the contact us page reveals a quick red blip.  Inspecting the page and identifying the code reveals a .js file being loaded from the assets directory we located earlier.  Inspecting this reveals a function on line 48 called `flash['remove']();`.  Within the debugging tool of the browser you can implement a "breakpoint" which stops code from executing.  I do this by clicking the line number and then I refresh the page and reveal the flag.

![](Screenshots/Debugger_Flag.png)

Back on the contact page I test input by entering random data into the contact us form and hit send as I have the network dev tool open.  This reveals a post 200 json method in the background which indicates the text I inputed is being sent somewhere.  Opening this reveals the final flag.

![](Screenshots/POST_200_NETWORK.png)
![](Screenshots/Final_Flag.png)