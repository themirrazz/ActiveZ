### Table of Contents
* Getting Started


# Getting Started
So, you wanna develop an ActiveZ control, you say? Well, lucky for you, you've came to the right place! To create your ActiveZ control, you'll need to have ActiveZ and [WScript for Windows 96](https://github.com/themirrazz/wscript96) installed.

## Creating your first ActiveZ control
First, create a file in `C:/local/ActiveZ`. Whatever you name it is how other apps will call it - we're going to name ours `Sample`. ActiveZ controls must end with the `.activez` file extension. Since ours is called `Sample`, the full path would be `C:/local/ActiveZ/Sample.activez`. After that, open it up in Monaco, and select `Document > Language > JavaScript`. Now, paste in the following code:
```js
/ACTIVE-Z/

return { }
```
Now, go to your home directory (recommended, but it can be anywhere), and create a new file called `test.js` (or whatever you want), and open it in Monaco. Put the following code inside of it:
```js
new ActiveXObject("Sample"); // replace with the name of yours here
WScript.Echo("It works!");
```
Then, run this in a terminal:
```
wscript test.js
```

If you see a popup that says "It works!", then congratulations - you've just made your first ActiveZ control!

## Making it useful
Okay, but, our ActiveZ control isn't really useful right now. So how do we make it useful? First off, how do we even know what it is? Well, we're going to be making a simple ActiveZ control that opens YouTube videos in Border(if you don't have Border installed, substitue all commands that use `border` with `internete`). don't Now, put this code in your `test.js` file.
```js
var yt = new ActiveXObject("YouTube");
yt.open("dQw4w9WgXcQ");
```
Doesn't work, right? But before we make this actually work, there's a few things we have to do.

## Adding metadata
Even though apps might know exactly what this control does, do users? Let's add some metadata to help the user understand what this app is supposed to do. Add the following lines right under `/ACTIVE-Z/` to your ActiveZ control:
```js
NAME: "YouTube"
DESC: "Launch YouTube videos in Border!"
AUTHOR: "(your name here)"
VER: 1.0
```
The whole file should look like this now:
```js
/ACTIVE-Z/
NAME: "YouTube"
DESC: "Launch YouTube videos in Border!"
AUTHOR: "(your name here)"
VER: 1.0

return { }
```
This metadata is used by the ActiveZ dashboard, which lets users easily manage which ActiveZ controls they have installed.

## Adding the code
Now, just use Windows 96 APIs as normal. Let's use `w96.sys.execCmd` to create an open function:

```js
return {
    open: async (videoId, embed) => {
        return await w96.sys.execCmd('border', [`https://www.youtube.com/${embed ? "embed/" : "watch?v=}${videoId}`]);
    }
}
```
Now, your ActiveZ control should look like this:
```js
/ACTIVE-Z/
NAME: "YouTube"
DESC: "Launch YouTube videos in Border!"
AUTHOR: "(your name here)"
VER: 1.0

return {
    open: async (videoId, embed) => {
        return await w96.sys.execCmd('border', [`https://www.youtube.com/${embed ? "embed/" : "watch?v="}${videoId}`]);
    }
}
```
Congratulations! You've just made your first working ActiveZ control!
