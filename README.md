# Text Count
Over 25 hours—didn’t bother with sleep—with Google AI and Mozilla we extremely optimized this applet that tells you the number of pages, lines, words, numbers, digits, and figures selected on a webpage.  Thanks to LLMs I’m more familiar with JS than the last time earlier this spring when I wrote a script to rewrite Wikimedia timestamps intelligently.
* One page every viewport of lines
* One line every vertical figure
* One word every boundary pair
* One number every boundary pair
* One digit every place value
* One figure every entry position
  * This applet cannot count actual pages, those that go laterally or longitudinally wherefore selections break or proprietary software doesn't allow selecting at all.
    * But keyboards say screenfuls are pages so assume the primitive terminal term.
  * Line count doesn't mean full lines but the ceiling of every line, the numerical ceiling not the top margin.
  * Any string of nonspace makes a word, especially nonwords.
    * Translate all visibles to maybe-hyphenated names to verbify them.
  * Numbers may include any intermittent multiple of .,'− as separators or affixes, thus even phone numbers, social security numbers, concatenated tuples, Swiss numbers, and IPv4 addresses quantify.
    * Confusables and measure tuples shall never be supported, besides the luckily-hyphenated date, thus /:;()°&prime;&Prime; and any space (as _a_ _b_ = _ab_).
  * Only denary and smaller is supported, according to dumb regex but also for name/identifier confusables.
  * I don't know whether this thing picks up zero-size controls.
    * I could look but don't need to.  Maybe you can tell me.
* The best−looking text counter.
  * All this needs are contextual menu and hotkey hooks, OS integration, floating window, and popularity.
    * Beware: sone embedded text fields don't tell their rectangle positions for line and page count.
 
# Installation
Make a bookmark/favorite with this code as the address:  
```javascript:(function(S,b,d,l,n,p,r,s,t,w,_,$){S=window.getSelection(),s=S.rangeCount?S.getRangeAt(0):null,t=S.toString(),w=(t.match(/\b[^\s]+\b/gs)||[]).length,n=(t.match(/(?<![\d.,'-])[.,'-]?\d+(?:[.,'-]\d+)*[.,'-]?(?!\d)/g)||[]).length,d=(t.match(/\d/g)||[]).length,p=(!s||S.isCollapsed)?0:s.getBoundingClientRect().height/window.innerHeight;for(r of s?[...s.getClientRects()].sort((A,a)=>A.top-a.top):[])r.width>0&&(!l||r.top>=b)&&(l=-~l,b=r.bottom);_=document.createElement("div");_.style.cssText="position:fixed;top:0;left:0;width:100%;height:100%;background:rgba(128,128,128,.6);display:flex;align-items:center;justify-content:center;z-index:9";_.onclick=()=>_.remove();$=document.createElement("div");$.style.cssText="background:rgba(255,255,255,.7);color:#000;padding:4px;border-radius:8px;box-shadow:0 4px 15px rgba(0,0,0,.5)";$.onclick=(e)=>e.stopPropagation();document.body.appendChild(_).appendChild($);$.innerHTML=`${p.toFixed(2)} page${p>0&&p<=1?"":"s"}<br>${l||0} line${l==1?"":"s"}<br>${w} word${w==1?"":"s"}<br>${n} number${n==1?"":"s"}<br>${d} digit${d==1?"":"s"}<br>${t.length} figure${t.length==1?"":"s"}`})()```  
I came up with this on stupid iPadOS Safari so even a shackled platform can surprise a regular user.  This has not been stress tested.  I disclaim any liability for data loss.
## Preview
<img width="1477" height="913" alt="IMG_1465" src="https://github.com/user-attachments/assets/8382184a-461a-430b-a765-2e696071ad9a" />
<img width="1451" height="906" alt="IMG_1466" src="https://github.com/user-attachments/assets/ab4a008e-e730-44e5-a3b6-261fcf5da19a" />

# Other must-use applets
* [Type Sample](https://www.typewolf.com/type-sample), [Wayback](https://web.archive.org/web/20201203064635/https://www.typesample.com/): names and previews fonts
* [Validate This Page](https://validator.w3.org/nu/about.html), HTML test
