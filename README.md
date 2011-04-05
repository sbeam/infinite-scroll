# Infinite Scroll jQuery Plugin

based on the original found here:

> http://www.infinite-scroll.com/
> the jQuery and Wordpress Plugins
> 
> jQuery Plugin:
> http://www.infinite-scroll.com/infinite-scroll-jquery-plugin/

## Changes

1. removed useless (to us) wordpress and site cruft (gregplaysguitar)
2. removed broken attempts to auto-parse next-page URL (gregplaysguitar)
3. does not depend on jQuery's filtering of returned HTML using the `itemSelector` option (although this is still available)
4. allows option to specify a function to get the next-page URL
5. recover 'localMode' option to allow use within an `overflow:auto` container, as opposed to the whole window - but renamed this option 'flowContainer'

## Example
    // usage:
    // $(elem).infinitescroll(options,[callback]);
     
    // infinitescroll() is called on the element that surrounds 
    // the items you will be loading more of
    $('#content').infinitescroll({
     
      navSelector  : "div.navigation",            
                     // selector for the paged navigation (it will be hidden)
     
      nextSelector : "div.navigation a:first",    
                     // selector for the NEXT link (to page 2), will use the
                     // 'href' attribute and this needs to be included with the
                     // returned content

                     // OR define a function to parse or generate the URL
                     // yourself. First arg will be the next page, eg:
      nextSelector : function(next) { return $('#next_page').attr('href').replace(/page=\d+\b/, 'page='+next); },
     
      itemSelector : "#content div.post",          
                     // selector for all items you'll retrieve. ie, the returned
                     // HTML for the page will be filtered by jQuery down to the 
                     // given selector.
                     // (set this to `null` if this is not needed (maybe your
                     // system is smart enough not to return the entire page)
     
      debug        : true,                        
                     // enable debug messaging ( to console.log )
     
      loadingImg   : "/img/loading.gif",          
                     // loading image.
                     // default: "http://www.infinite-scroll.com/loading.gif"
     
      loadingText  : "Loading...",      
                     // text accompanying loading image
                     // default: "<em>Loading the next set of posts...</em>"
     
      animate      : true,      
                     // boolean, if the page will do an animated scroll when new content loads
                     // default: false
     
      extraScrollPx: 50,      
                     // number of additonal pixels that the page will scroll 
                     // (in addition to the height of the loading div)
                     // animate must be true for this to matter
                     // default: 150
     
      donetext     : "I think we've hit the end, Jim" ,
                     // text displayed when all items have been retrieved
                     // default: "<em>Congratulations, you've reached the end of the internet.</em>"
     
      bufferPx     : 40,
                     // increase this number if you want infscroll to fire quicker
                     // (a high number means a user will not see the loading message)
                     // default: 40

      loadMsgSelector : '#posts-list',
                     // loading message will be appended to this element

      loadingMsgRevealSpeed : 'fast', 
                     // controls how fast you want the loading message to come
                     // in, ex: 'fast', 'slow', 200 (milliseconds)
     
      errorCallback: function(){}
                     // called when a requested page 404's or when there is no more content
     
     
        },function(arrayOfNewElems){
     
         // optional callback when new content is successfully loaded in.
     
         // `this` matches the element you called the plugin on (e.g. #content)
         // all the new elements that were found are passed in as an array
     
    });

