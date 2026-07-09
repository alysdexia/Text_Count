### Text Count
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
 
### Installation
Make a bookmark/favorite with this code as the address:  
```javascript:(function(S,b,d,l,n,p,r,s,t,w,_,$){S=window.getSelection(),s=S.rangeCount?S.getRangeAt(0):null,t=S.toString(),w=(t.match(/\b[^\s]+\b/gs)||[]).length,n=(t.match(/(?<!\d)[-.,'·]?\d+(?:[-.,'·]\d+)*[-.,'·]?(?!\d)/g)||[]).length,d=(t.match(/\d/g)||[]).length,p=(!s||S.isCollapsed)?0:s.getBoundingClientRect().height/window.innerHeight;for(r of s?[...s.getClientRects()].sort((A,a)=>A.top-a.top):[])r.width>0&&(!l||r.top>=b)&&(l=-~l,b=r.bottom);_=document.createElement("div");_.style.cssText="position:fixed;top:0;left:0;width:100%;height:100%;background:rgba(128,128,128,.6);display:flex;align-items:center;justify-content:center;z-index:9";_.onclick=()=>_.remove();$=document.createElement("div");$.style.cssText="background:rgba(255,255,255,.7);color:#000;padding:4px;border-radius:8px;box-shadow:0 4px 15px rgba(0,0,0,.5)";$.onclick=(e)=>e.stopPropagation();document.body.appendChild(_).appendChild($);$.innerHTML=`${p.toFixed(2)} page${p>0&&p<=1?"":"s"}<br>${l||0} line${l==1?"":"s"}<br>${w} word${w==1?"":"s"}<br>${n} number${n==1?"":"s"}<br>${d} digit${d==1?"":"s"}<br>${t.length} figure${t.length==1?"":"s"}`})()```  
I came up with this on stupid iPadOS Safari so even a shackled platform can surprise a regular user.  This has not been stress tested.  I disclaim any liability for data loss.
#### Preview
<img width="1458" height="855" alt="IMG_1468" src="https://github.com/user-attachments/assets/c2bc39ea-9afe-49b1-85c4-e6238785beb7" />
<img width="1462" height="859" alt="IMG_1469" src="https://github.com/user-attachments/assets/97717dfb-d95b-4b08-a789-072b01fd2c89" />

### Development
* https://www.google.com/search?q=bookmarklet+word+character+count
* https://www.google.com/search?q=bookmarket+page+line+word+character+count
* https://www.google.com/search?q=Javascript+match
* https://www.google.com/search?q=any+way+for+regex+or+Javascript+to+count+the+number+of+lines+a+word+wrapped+line+takes+up%3F
* [does Javascript know the height of a text selection?, AI Mode](https://share.google/aimode/5QEorfroWTo8wjj2s)
* https://www.google.com/search?q=in+Javascript+when+I+used+typewriter+quote+marks+instead+of+grave+accents+in+map%28rect+%3D%3E+%24%7Brect.height%7Dpx%29%2C+the+function+didn%27t+work
* https://www.google.com/search?q=does+Javascript+require+grave+accents+as+quote+marks%3F
* [does Javascript know the height of a text selection?, AI Mode](https://share.google/aimode/t3SdhFyKkEbEOvLcL)
* r1: I was occupied with numerical conventions that I forgot my own preferred decimal separator.  I also needed to fix two bugs with mixed numbers whose solution still doesn't make sense when I look at the regex.
  * Now I understand what went and what I did wrong.  When I first added the − I was aware of Mozilla’s warning to put that at the beginning or end of brackets.  But I added · after forgetting to and didn’t tell Google AI that I did after the −.  I didn’t expect anything bad to happen as that was also punctuation, but that middot happens to be in Latin-1 Supplement which means most of Basic Latin broke the match.

### Other must-use applets
* [Type Sample](https://www.typewolf.com/type-sample), [Wayback](https://web.archive.org/web/20201203064635/https://www.typesample.com/): names and previews fonts
* [Validate This Page](https://validator.w3.org/nu/about.html), HTML test

alysdexia
