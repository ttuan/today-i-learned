Today, I have to do a task: Dectect current device which is accessing a website.
I have tried to google and find some solutions:

1. The first solution comes from [this
   topic](http://stackoverflow.com/questions/3514784/what-is-the-best-way-to-detect-a-mobile-device-in-jquery)

   ```
   if( /Android|webOS|iPhone|iPad|iPod|BlackBerry|IEMobile|Opera Mini/i.test(navigator.userAgent) ) {
      // some code..
    }
   ```
   It seems quite easy when use user_agent to detect device. But it has 2
   problems:
   + Whenever a new device or new OS was born, you need to change this code.
   + User agent strings are a constant moving target, they should not be trusted alone
   + Some browser is configed to not send user argent.

2. Use some library like: [detectmobiledevice](http://detectmobilebrowsers.com/)
   or [wurfl](https://web.wurfl.io/). However, we just use a small of code in
   this library, we don't need to import whole lib files.

3. This is my solutions: We will call a function: `window.orientation` to dectect.
   If it !== "undefined" ---> this device is mobile because this command
   returns "Lancapse" or "Portrait" for mobile and returns `undefined` for
   Desktop.
