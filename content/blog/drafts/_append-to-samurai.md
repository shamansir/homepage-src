---
title: "Append to Way of Samurai"
author: ["Anton Kotenko"]
draft: false
---

```javascript
var __s = Array.prototype.slice; function deferrable_as(ctx, f) { return
function() { return (function(args) { return function(result, next) {
return f.apply(ctx, args.concat([result, next])); };
})(__s.call(arguments)); } } function queue(//f...//) { var as =
__s.call(arguments); console.log(as); if(!(as.slice(-1)[0] instanceof
Function)){ var prev_res = as.slice(-1)[0]; } if(as.slice(1).length){
var callback = function(res) { as.push(res); queue.apply(null,
as.slice(1)); } } as[[file:prev_res,%20callback][0]]; }

function /read_file(name, prev_readed, next){ //console.log(arguments);
setTimeout(function() { alert('readed'+name); if(prev_readed){ name =
prev_readed+'/'+name; } next(name); }, 1000); }

function _notify_success(name, next){ alert(name + ' was read');
next('next_file'); }

var read_file = deferrable_as(null, _read_file); var notify_success =
deferrable_as(null, _notify_success);

queue(read_file('book_name_1'), read_file('book_name_2'),
read_file('book_name_3'), notify_success());

var __s = Array.prototype.slice; function deferrable_as(ctx, f) { return
function() { return (function(args) { return function(result, next) {
return f.apply(ctx, args.concat([next, result])); };
})(__s.call(arguments)); } } function queue(//f...//) { var as =
__s.call(arguments), prev_res = as.slice(-1)[0];
as[[file:prev_res,%20function(res)%20%7B%20as.push(res);%20queue.apply(null,%20as.slice(1));%20%7D][0]];
}

function _read_file(name, next){ setTimeout(function() {
alert('reading'+name); next(name); }, 2000); }

function _notify_success(name, next){ alert(name + ' was read');
next('next_file'); }

var read_file = deferrable_as(null, _read_file); var notify_success =
deferrable_as(null, _notify_success);

queue(read_file('book_name_1'), read_file('book_name_2'),
read_file('book_name_3'), notify_success());
```


This text is auto inserted at the end of the exported Markdown.