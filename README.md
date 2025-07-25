# ActiveZ
An ActiveX clone for Windows 96

## What is ActiveZ?
ActiveZ is a drop-in ActiveX replacement for [Windows 96](https://windows96.net/) (the website). Out-of-the-box, ActiveZ supports `Microsoft.XMLHTTP`, `WScript.Shell`, and `InternetExplorer.Application`, but you can always install more by putting them in `C:/local/ActiveZ`.

## Can any app use ActiveZ controls?
Yes! Any app can use ActiveZ controls by running this command:
```
active-z create nameOfControl
```
You can create an ActiveZ control in JavaScript like this:
```js
//!wrt
const control = await w96.sys.execCmd("active-z", ["create", "nameOfControl"]);
```

## Can I make my own ActiveZ control?
Yes, you can! In order to learn about how ActiveZ works, please see our [developer documentation](/docs/index.md)! Please note these all apply to the upcoming ActiveZ v1 release, not the current version (v0).
