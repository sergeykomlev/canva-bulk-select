# Bulk select your media uploads on Canva

This task started when I needed to transfer all the content from my Canva uploads to another account. Unfortunately, Canva didn't have a feature to select all uploads and move them to a folder. 

Using simple social engineering techniques and a developer console in the browser, we will solve this problem, which will save us a significant amount of time.

If my solution helped you, there is nothing better than a cup of coffee as a thank you.

[!["Buy Me A Coffee"](https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png)](https://www.buymeacoffee.com/graftype)

# Let's do it

## Step 1. Login to Canva.

Login to your Canva account and open Uploads page. Scroll down to load all your media files.

<img width="467" alt="Screenshot at Apr 09 02-51-08" src="https://user-images.githubusercontent.com/40078038/230747258-5bfc2291-29e9-4331-b1fc-0334e41e5f58.png">

## Step 2. Developer Console.

Open the developer console. Yes, you have to do it from a computer.

### Chrome
To open the developer console window on Chrome, use the keyboard shortcut Cmd-Shift-J on Windows or Cmd-Option-J on a Mac.

###  Edge
To open the console on Edge, hit F12 to access the Developer Tools. Once in the Developer Tools, navigate to the Console tab.

###  Firefox
To open the console on Firefox, use the keyboard shortcut Cmd-Shift-K on Windows or Cmd-Option-K on a Mac. The toolbox will appear at the bottom of the browser window, with the Web Console activated.

###  Safari
To open the console on Safari, you will first need to turn on the Develop menu. To do this, open the Safari menu in the Mac menu bar, then select Preferences. Once in the Preferences dialog, navigate to the Advanced tab, then check the "Show Develop menu in the menu bar" box.

## Step 3. Append jQuery to Canva page.

Once you opened a console go to `Console tab` and append jQuery to current Canva page.

<img width="759" alt="Screenshot at Apr 09 02-47-37" src="https://user-images.githubusercontent.com/40078038/230747283-5924c9cc-a600-47e1-87c9-6cbce0a1877c.png">

Add following code and click `Enter` on your keyboard:

```js
var script = document.createElement('script');
script.src = "https://ajax.googleapis.com/ajax/libs/jquery/1.6.3/jquery.min.js";
document.getElementsByTagName('head')[0].appendChild(script);
```

## Step 4. Checkbox CSS class.

After you append jQuery to current Canva page, now you need to find DOM element class of select checkbox. 

To do that do a right button click on your mouse and click `View code` in dropdown menu.

<img width="404" alt="Screenshot at Apr 09 03-10-31" src="https://user-images.githubusercontent.com/40078038/230747733-0e5cc4f3-29a5-45d0-8005-2febda590d34.png">

You will see the source code of the checkbox. Now you need to find a class. On the screenshot, I highlighted this with red color.

<img width="1291" alt="Screenshot at Apr 09 03-12-37" src="https://user-images.githubusercontent.com/40078038/230747815-bc00e7f3-96fe-4322-b0fc-6e07eb64b0e0.png">

Copy that value. On my screen it's a `ZJon7Q nv35GQ`.

## Step 5. Script for bulk select.

Once you have a class of checkbox. You can select your media assets.

Perform following code in console and click `Enter` on your keyboard:

```js
$(".ZJon7Q.nv35GQ").each(function(index) {
  if (index >= 0 && index <= 99) {
    $(this).click();
  } else {
    return;
  }
});
```

- where `.ZJon7Q.nv35GQ` is previouslt found class of checkbox. We need to remove whitespaces and add `.` before class names to make our script functional.
- `index >= 0 && index <= 99` means that script will select only first 100 images in your Upload feed

## Step 6. Waiting for execution. 

After a few minutes (you need to wait a while script slecting your images) you will see that our script selected first 100 images in your Upload feed automatically. Now you can move your files to selected folder. You can retry step 5 multiple times.

That's all! Enjoy your time! 

<img width="908" alt="image" src="https://user-images.githubusercontent.com/40078038/230748085-d1a9eb58-df82-46ea-b962-c5044fdb8329.png">
