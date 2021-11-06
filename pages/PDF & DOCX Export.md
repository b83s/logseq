---
title: PDF & DOCX Export
---

- v0.2
	 - Fixed: removal of trigger phrase before rendering of pdf/docx file.

	 - 

- Configuration:
	 - This SB allows you to export a page from Roam Research to either PDF or DOCX format. It relies on @roamhacker's [Roam42](https://roamresearch.com/#/app/roamhacker/page/jI-X_cwaf) conversion engine, using the Markdown flattening and Markdown to HTML functions.

	 - You can choose to only export the body of your page, or you can include the linked references section from the bottom of the page as well.

	 - If you wish to include linked references, change the 42Setting on the next line to show true
		 - #42Setting PDFDOCXLinkedRefs false

	 - You need to uncomment (remove the // at the start of the line) in the roam/js block below. For PDF export, uncomment the first addScripts line as shown. For DOCX, uncomment the three addScripts lines at the bottom of the code block. You can choose whether you want either or both functions to be available. If you want both, uncomment all four addScripts lines.

	 - Then, click the Yes, I know what I'm doing button. Then, reload Roam Research.

	 - {{roam/js}}
		 - ```javascript
 function addScripts(url) {
     var script = document.createElement('script');
     script.type = 'application/javascript';
     script.src = url;
     document.head.appendChild(script);
 }

// uncomment the line below for PDF (remove the //)
addScripts('https://raw.githack.com/eKoopmans/html2pdf/master/dist/html2pdf.bundle.js');

// uncomment the below three lines for DOCX (remove the //)
addScripts('https://evidenceprime.github.io/html-docx-js/build/html-docx.js');
addScripts('https://cdnjs.cloudflare.com/ajax/libs/FileSaver.js/1.3.8/FileSaver.js');
addScripts('https://tinymce.cachefly.net/4.1/tinymce.min.js');
```

	 - You should now be able to export any page you wish as pdf by typing `jjpdf` or as docx by typing `jjdocx`.

	 - Note: all the available scripts to convert html to pdf do so by creating an image and then printing that to pdf. This will mean your pdf is __not__ searchable. I will be happy to update if/when someone smarter than me figures out how to export html to pdf without doing so via image.

- ---

- #42SmartBlock PDF export
	 - <%JAVASCRIPTASYNC:
```javascript
async function clearTrigger() {
  var triggerBlockUID = document.activeElement.id.split('-').pop();
  var refInfo = await roam42.common.getBlockInfoByUID(triggerBlockUID, true, false);
  var triggerBlock = refInfo[0][0].string;
  triggerBlock = triggerBlock.split("jj");
  triggerBlockText = triggerBlock[0].trim();
  await roam42.common.updateBlock(triggerBlockUID, triggerBlockText, true);
  return;
}

var PDFDOCXLinkedRefs = await roam42.settings.get('PDFDOCXLinkedRefs');

async function flatten(uid) {
var md =  await roam42.formatConverter.iterateThroughTree(uid, roam42.formatConverter.formatter.markdownGithub, true );
    marked.setOptions({
      gfm: true,
      xhtml: false,
      pedantic: false,
    });
    md = md.replaceAll('- [ ] [', '- [ ]&nbsp;&nbsp;['); //fixes odd isue of task and alis on same line
    md = md.replaceAll('- [x] [', '- [x]&nbsp;['); //fixes odd isue of task and alis on same line
    md = md.replaceAll(/\{\{\youtube\: (.+?)\}\} /g, (str,lnk)=>{
      lnk = lnk.replace('youtube.com/','youtube.com/embed/');
      lnk = lnk.replace('youtu.be/','youtube.com/embed/');
      lnk = lnk.replace('watch?v=','');
      return `<iframe width="560" height="315" class="embededYoutubeVieo" src="${lnk}" frameborder="0"></iframe>`
    });

    //lATEX handling
   md = md.replace(/  \- (\$\$)/g, '\n\n$1'); //Latex is centered
    const tokenizer = {
      codespan(src) {
        var match = src.match(/\$\$(.*?)\$\$/);
        if (match) {
          var str = match[0];
              str = str.replaceAll('<br>',' ');
              str = str.replaceAll('<br/>',' ');
              str = `<div>${str}</div>`;
          return { type: 'text', raw: match[0],text: str };
        }
        // return false to use original codespan tokenizer
        return false;
      }
    };
    marked.use({ tokenizer });
    md = marked(md)

    return  `<html>\n
              <head>
              </head>
              <body>\n${md}\n
              </body>\n
            </html>`;
}

var pageTitle = null;
if(document.activeElement.closest('.sidebar-content')!=null) {
    if(document.activeElement.closest('.rm-sidebar-outline').querySelector('h1.rm-title-display'))
        pageTitle = document.activeElement.closest('.rm-sidebar-outline').querySelector('h1.rm-title-display').innerText;
    else if(document.activeElement.closest('.rm-sidebar-outline').querySelector('.rm-zoom-item-content'))
        pageTitle = document.activeElement.closest('.rm-sidebar-outline').querySelector('.rm-zoom-item-content').innerText;
} else if (document.activeElement.closest('.roam-article')!=null) {
    if(document.activeElement.closest('.roam-log-page'))
        pageTitle = document.activeElement.closest('.roam-log-page').querySelector('.rm-title-display').innerText;
    if(pageTitle==null && document.querySelector('.rm-title-display'))
        pageTitle = document.querySelector('.rm-title-display').innerText;
}

clearTrigger().then(async () => {
  console.log("Starting parse");
  var pageUID = await roam42.common.currentPageUID();
  var page = await flatten(pageUID);
  if (PDFDOCXLinkedRefs == "true") {
    var list = document.getElementsByClassName("rm-reference-container");
    if (list.length) {
      page = page.replace("</body>", "<br><hr><br>"+list[0].innerHTML+"</body>")
    } 
  }

  var opt = {
    margin:       1,
    filename:     pageTitle+'.pdf',
    image:        { type: 'jpeg', quality: 0.98 },
    enableLinks:	true,
    pagebreak: 	{ mode: ['avoid-all', 'css', 'legacy'] },
    html2canvas:  { scale: 2 },
    jsPDF:        { unit: 'in', format: 'letter', orientation: 'portrait' }
  };
  
  var worker = html2pdf().set(opt).from(page).save();
});

return'';
```%>

- #42SmartBlock DOCX export
	 - <%JAVASCRIPTASYNC:
```javascript
async function clearTrigger() {
  var triggerBlockUID = document.activeElement.id.split('-').pop();
  var refInfo = await roam42.common.getBlockInfoByUID(triggerBlockUID, true, false);
  var triggerBlock = refInfo[0][0].string;
  triggerBlock = triggerBlock.split("jj");
  triggerBlockText = triggerBlock[0].trim();
  await roam42.common.updateBlock(triggerBlockUID, triggerBlockText, true);
  return;
}

var PDFDOCXLinkedRefs = await roam42.settings.get('PDFDOCXLinkedRefs');

var pageUID = await roam42.common.currentPageUID();
var pageTitle = null;
if(document.activeElement.closest('.sidebar-content')!=null) {
    if(document.activeElement.closest('.rm-sidebar-outline').querySelector('h1.rm-title-display'))
        pageTitle = document.activeElement.closest('.rm-sidebar-outline').querySelector('h1.rm-title-display').innerText;
    else if(document.activeElement.closest('.rm-sidebar-outline').querySelector('.rm-zoom-item-content'))
        pageTitle = document.activeElement.closest('.rm-sidebar-outline').querySelector('.rm-zoom-item-content').innerText;
} else if (document.activeElement.closest('.roam-article')!=null) {
    if(document.activeElement.closest('.roam-log-page'))
        pageTitle = document.activeElement.closest('.roam-log-page').querySelector('.rm-title-display').innerText;
    if(pageTitle==null && document.querySelector('.rm-title-display'))
        pageTitle = document.querySelector('.rm-title-display').innerText;
}

async function flatten(uid) {
var md =  await roam42.formatConverter.iterateThroughTree(uid, roam42.formatConverter.formatter.markdownGithub, true );
    marked.setOptions({
      gfm: true,
      xhtml: false,
      pedantic: false,
    });
    md = md.replaceAll('- [ ] [', '- [ ]&nbsp;&nbsp;['); //fixes odd isue of task and alis on same line
    md = md.replaceAll('- [x] [', '- [x]&nbsp;['); //fixes odd isue of task and alis on same line
    md = md.replaceAll(/\{\{\youtube\: (.+?)\}\} /g, (str,lnk)=>{
      lnk = lnk.replace('youtube.com/','youtube.com/embed/');
      lnk = lnk.replace('youtu.be/','youtube.com/embed/');
      lnk = lnk.replace('watch?v=','');
      return `<iframe width="560" height="315" class="embededYoutubeVieo" src="${lnk}" frameborder="0"></iframe>`
    });

    //lATEX handling
   md = md.replace(/  \- (\$\$)/g, '\n\n$1'); //Latex is centered
    const tokenizer = {
      codespan(src) {
        var match = src.match(/\$\$(.*?)\$\$/);
        if (match) {
          var str = match[0];
              str = str.replaceAll('<br>',' ');
              str = str.replaceAll('<br/>',' ');
              str = `<div>${str}</div>`;
          return { type: 'text', raw: match[0],text: str };
        }
        // return false to use original codespan tokenizer
        return false;
      }
    };
    marked.use({ tokenizer });
    md = marked(md)

    return  `<html>\n
              <head>
              </head>
              <body>\n${md}\n
              </body>\n
            </html>`;
}

clearTrigger().then(async () => {
  var page = await flatten(pageUID);
  if (PDFDOCXLinkedRefs == "true") {
    var list = document.getElementsByClassName("rm-reference-container");
    if (list.length) {
      page = page.replace("</body>", "<br><hr><br>"+list[0].innerHTML+"</body>")
    } 
  }

  var converted = htmlDocx.asBlob(page);
  saveAs(converted, pageTitle+'.docx');
});

return'';
```%>
