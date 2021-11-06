---
title: roam/js/roam42
---

- https://roamresearch.com/#/app/roamhacker/page/UeoxCm8rm

- [[Smartblocks]]

- https://drive.google.com/drive/folders/1MV3DdOFIHyLeS246QHaN0j35dZwTOwGK

- {{[[roam/js]]}}
	 - ```javascript
var existing = document.getElementById("roamjs-roam42-main");
if (!existing) {
  var extension = document.createElement("script");
  extension.src = "https://roamjs.com/roam42/main.js";
  extension.id = "roamjs-roam42-main";
  extension.async = true;
  extension.type = "text/javascript";
  document.getElementsByTagName("head")[0].appendChild(extension);
}
```
