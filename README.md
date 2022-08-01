### Before
![image](https://user-images.githubusercontent.com/46839654/151513613-ccfa8973-dd6b-4b04-9286-08a08356ccea.png)

### After
![image](https://user-images.githubusercontent.com/46839654/151640387-83985da9-5958-4689-ad69-04d640adc6d7.png)

### Nginx.conf

    server {
      location / {
        autoindex on;
        autoindex_exact_size off;
        autoindex_localtime on;
        add_before_body "/theme/before.html";
        add_after_body "/theme/after.html";
      }
      location = /favicon.ico {
        return 204;
      }
      location /theme/ {
        alias /your/html/dir/path/;
      }
    }

### before.html

    <!DOCTYPE html> <html lang="en"> <head> <meta charset="UTF-8"/> <meta http-equiv="X-UA-Compatible" content="IE=edge"/> <meta name="viewport" content="width=device-width, initial-scale=1.0"/> <link rel="stylesheet" href="/theme/styles.css" /> </head> <body>
      
### after.html

    <script src="/theme/main.js"></script> </body> </html>
    
### styles.css

    body{-webkit-box-orient:vertical;-webkit-box-direction:normal;-webkit-box-align:center;-ms-flex-align:center;align-items:center;display:-webkit-box;display:-ms-flexbox;display:flex;-ms-flex-direction:column;flex-direction:column}a{color:#333;text-decoration:none}table{border-collapse:collapse;font-size:1em}thead{background-color:#eee}thead,thead>tr>th{border:1px solid #333}thead>tr>th{padding:5px 10px}tbody{border:1px solid #333}tbody>tr:hover{background-color:#eee}tbody>tr>td{padding:0}tbody>tr>td:not(:first-child){padding:5px}tbody>tr>td:first-child>a{display:-webkit-box;display:-ms-flexbox;display:flex;padding:5px}
    
    
### main.js

    ##
    # A table with filename, date, size
    ##
    !function(){"use strict";const e=document.querySelector("body"),t=Array.from(document.querySelectorAll("a")).filter(((e,t)=>t>0)),n=function(e){const t=Array.from(document.querySelector(e).childNodes).filter(((e,t)=>"#text"===e.nodeName)).filter(((e,t)=>t>0));return t.map((e=>{const t=e.textContent.split(" ").filter((e=>""!==e)),n=t[0],o=t[1],r=t[2];return" -"===r&&(r=r.trim()),{date:n,time:o,size:r}}))}("pre"),o=document.querySelector("pre"),r=Array.from(document.querySelectorAll("hr")),d=document.createElement("table"),c=document.createElement("thead"),l=document.createElement("tr"),m=document.createElement("th"),a=document.createElement("th"),i=document.createElement("th");m.textContent="Filename",a.textContent="Date",i.textContent="Size",l.appendChild(m),l.appendChild(a),l.appendChild(i),c.appendChild(l),d.appendChild(c),e.insertBefore(d,r[1]);const p=document.createElement("div");e.insertBefore(p,d);const u=document.createElement("a");u.href="/",u.textContent="🏠",u.style.marginRight="10px",u.style.fontSize="30px",p.appendChild(u);const C=document.querySelector('a[href="../"]');C.textContent="⬅️",C.style.fontSize="30px",p.appendChild(C),e.removeChild(o),r.forEach((t=>e.removeChild(t)));const h=document.createElement("tbody");Array.from(t).map(((e,t)=>{const o=document.createElement("tr"),r=document.createElement("td"),c=document.createElement("td"),l=document.createElement("td");e.textContent.endsWith("/")?e.textContent=`📁 | ${e.textContent}`:e.textContent=`💾 | ${e.textContent}`,r.appendChild(e),c.textContent=`${n[t].date} ${n[t].time}`,l.textContent=n[t].size,o.appendChild(r),o.appendChild(c),o.appendChild(l),h.appendChild(o),d.appendChild(h)}))}();
    
    ##
    # A table with filename and size
    ##
    !function(){"use strict";const e=document.querySelector("body"),t=Array.from(document.querySelectorAll("a")).filter(((e,t)=>t>0)),n=function(e){const t=Array.from(document.querySelector(e).childNodes).filter(((e,t)=>"#text"===e.nodeName)).filter(((e,t)=>t>0));return t.map((e=>{const t=e.textContent.split(" ").filter((e=>""!==e)),n=t[0],r=t[1],o=t[2];return" -"===o&&(o=o.trim()),{date:n,time:r,size:o}}))}("pre"),r=document.querySelector("pre"),o=Array.from(document.querySelectorAll("hr")),d=document.createElement("table"),c=document.createElement("thead"),l=document.createElement("tr"),m=document.createElement("th"),a=document.createElement("th");m.textContent="Filename",a.textContent="Size",l.appendChild(m),l.appendChild(a),c.appendChild(l),d.appendChild(c),e.insertBefore(d,o[1]);const i=document.createElement("div");e.insertBefore(i,d);const p=document.createElement("a");p.href="/",p.textContent="🏠",p.style.marginRight="10px",p.style.fontSize="30px",i.appendChild(p);const u=document.querySelector('a[href="../"]');u.textContent="⬅️",u.style.fontSize="30px",i.appendChild(u),e.removeChild(r),o.forEach((t=>e.removeChild(t)));const C=document.createElement("tbody");Array.from(t).map(((e,t)=>{const r=document.createElement("tr"),o=document.createElement("td"),c=document.createElement("td");e.textContent.endsWith("/")?e.textContent=`📁 | ${e.textContent}`:e.textContent=`💾 | ${e.textContent}`,o.appendChild(e),c.textContent=n[t].size,r.appendChild(o),r.appendChild(c),C.appendChild(r),d.appendChild(C)}))}();
