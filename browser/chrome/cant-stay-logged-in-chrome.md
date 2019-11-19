# Can't stay logged in on Google Chrome

Yesterday, I install chrome 78.0 on Ubuntu 16.04. Everything works fine before I
close Chrome.

After I reopen Chrome, I'm automatically logged off all sites (facebook, google,
chatwork, ...).

After searching for a while, I realize that my problem is that I had a corrupt
Cookies file. So just delete google chrome cookies file and all will be ok :D

Just open terminal and run this command:

`rm -rf ~/.config/google-chrome/Profile*/Cookies`
