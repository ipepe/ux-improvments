# Presentation of concept code
```javascript
document.querySelectorAll('span.yt-uix-simple-thumb-wrap.yt-uix-simple-thumb-related img').forEach(function(item, index){
  if(!item.id){
    item.id = 'drag_poc_' + index + '_' + Date.now().toString()
  }
  item.draggable=true;
  item.ondragstart=function(event){
    event.dataTransfer.setData("id", item.id);
  }
  item.ondragover=function(event){event.preventDefault();};
  item.ondrop=function(event){
    event.preventDefault();
    var target = item;
    var source = document.getElementById(event.dataTransfer.getData("id"));
    console.log(target,source)
    var tmp = target.parentNode.parentNode.parentNode.parentNode.innerHTML;
    target.parentNode.parentNode.parentNode.parentNode.innerHTML = source.parentNode.parentNode.parentNode.parentNode.innerHTML;
    source.parentNode.parentNode.parentNode.parentNode.innerHTML = tmp;
  }
});
```
