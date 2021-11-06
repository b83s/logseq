---
title: roam/js/smartblock-v2
---

- {{[[roam/js]]}}
	 - ```javascript
var existing = document.getElementById("roamjs-smartblocks-main");
if (!existing) {
  var extension = document.createElement("script");
  extension.src = "https://roamjs.com/smartblocks/main.js";
  extension.id = "roamjs-smartblocks-main";
  extension.async = true;
  extension.type = "text/javascript";
  document.getElementsByTagName("head")[0].appendChild(extension);
}

```
