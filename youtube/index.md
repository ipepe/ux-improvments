## YouTube drag'n'drop for autoplay
YouTube has introduced autoplay function quite some time ago. But I ofter meet myself with a need to change video that is going to play next. This is beneficial for both parties (me and YouTube). I will get video I want to watch, and YouTube is getting their suggestions improved.

### Presentation of concept - gif
![Presentation of concept](/youtube/autoplay.gif)

### Presentation of concept - code
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
