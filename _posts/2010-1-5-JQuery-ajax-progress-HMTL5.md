---
layout: post
title: JQuery ajax progress - HTML5
redirects:
- /quick-tips/jquery-ajax-progress-html5/
---

> Update: See end of post for jQuery versions after 1.5.1

This is just another reason to love HTML5 and never let it leave your life &hearts;

The second version of XMLHttpRequest (XMLHttpRequest2) supports progress events... for upload and download!!!!

This is very easy to implement if your familiar with JQuery, example code below.

{% highlight javascript linenos %}
$.ajax({
  type: 'POST',
  url: "/",
  data: {},
  beforeSend: function(XMLHttpRequest)
  {
    //Upload progress
    XMLHttpRequest.upload.addEventListener("progress", function(evt){
      if (evt.lengthComputable) {  
        var percentComplete = evt.loaded / evt.total;
        //Do something with upload progress
      }
    }, false); 
    //Download progress
    XMLHttpRequest.addEventListener("progress", function(evt){
      if (evt.lengthComputable) {  
        var percentComplete = evt.loaded / evt.total;
        //Do something with download progress
      }
    }, false); 
  },
  success: function(data){
    //Do something success-ish
  }
});
{% endhighlight %}

This is done by modifying the XMLHttpRequest provided by "beforeSend" to create event handlers within the AJAX call.

This is only a simple working example, it should be tested before production use, I have not tested this code when using multiple asynchronous requests.

Please keep in mind that HTML5 is still under development and this is by no means a perfect solution to upload progress as yet as some browsers do not support it. This does work in Chrome 5, Safari 4 and Firefox 3.1+, don't know when Internet Explorer might catch up... 

Updated version for jQuery > 1.5.1

{% highlight javascript linenos %}
$.ajax({
  xhr: function()
  {
    var xhr = new window.XMLHttpRequest();
    //Upload progress
    xhr.upload.addEventListener("progress", function(evt){
      if (evt.lengthComputable) {
        var percentComplete = evt.loaded / evt.total;
        //Do something with upload progress
        console.log(percentComplete);
      }
    }, false);
    //Download progress
    xhr.addEventListener("progress", function(evt){
      if (evt.lengthComputable) {
        var percentComplete = evt.loaded / evt.total;
        //Do something with download progress
        console.log(percentComplete);
      }
    }, false);
    return xhr;
  },
  type: 'POST',
  url: "/",
  data: {},
  success: function(data){
    //Do something success-ish
  }
});
{% endhighlight %}

Creates a new XHR object for use, would need to also detect IE and deliver the activeX in production.

Have fun, Cya