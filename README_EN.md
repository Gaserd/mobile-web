#mobile-web

Hello, my young friend! Yes, you're the fellow that came here, because today I will tell you a story about the mobile web.

Yes, on the very web on which you can't find the time. And meanwhile, mobile traffic works, and strengthened rule of mobile first is only strengthening its position.

Most likely you sit and think, how cool that I have a mobile version, which I have all of the adaptive and everything is so cool.

##I'm sorry, but this is not true
From what you wrote adaptive layout, some of the problems are gone.

##Let's see

And so, before us a whole zoo of devices. What do we do? All right, we could have our CA! And know what guys you are sitting, which we use, in my case it is all possible in the world of devices. Yeah.

##Problem with iOS

###Problem 1 — the scale on the page
In iOS 10 guys off you a little scale on the page.

<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">

I think it's a problem, but there are those who will say that it is not. The choice is yours.

###Problem 2 — Scroll and overflow
Everyone's favorite scrolling and overflou. Sorry friends, but in iOS it is not working as you would like.


###Problem 3 — Smooth scrolling
Again scrolling, it is not a problem, just a reminder, don't forget to do that. Allows smooth scrolling with your finger in the block.

-webkit-overflow-scrolling: touch;

###Problem 4 — new Date()
Between Safari and Chrome, there's a little inconsistency. It is associated with `new Date()` - in the case of Chrome you can safely feed the line 2016-8-2, while Safari will complain and force you to deliver the missing zeros.

###Problem 5 — Flexbox Wrap
The property `flex-wrap: wrap;` is not working as in other browsers. Even if you specify the minimum width of an element using `min-width`, migrate items to other lines will not be: Safari ignores the `min-width`. Must be set to `flex-basis` (or `flex-basis: 10em;` or`, flex: 1 0 10em;`).

###Problem 6 — Round input
Safari on iOS by default, rounds all text input and does not respond to `border-radius: 0;`. To prevent the fillet it is necessary to use `-webkit-appearance: none;`.

##Problem with Android

###Problem 1 — Keyboard in WebView
WebView and Android. Unfortunately, there is little trouble. If iOS makes the scale features a keypad, as it is necessary, then Android just opens it up and all.
I solved this problem very simply, I added padding from the bottom of my block. You can do more logical to scroll to the desired input. The average size of the keyboard is 150px.

###Problem 2 — Huawei U8860
I for some reason was not able to solve, is also connected with layout inside the app.
There is such a device, Huawei U8860 / Android OS 4.0.3 and now it is not working `border-radius` and it's sad.

In addition, this device does not work linear-gradient, which also might please you.


#Problem with PWA

###Problem 1
There is such a meta tag which allows You to paint the status bar on your iOS, a very important thing if you save a website to your desktop. 
But it does not work in versions 9.0 and 9.1, 9.2 have all work.

<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">

###Problem 2
Sorry, but in iOS there are no such chips from the PWA. One of the very important things is not a service worker, you will outlive them. But saving the application state (state) in which you minimize it, won't work, it only works in Anroid.

Plus, I did not understand how in the end traverse of get-parameters at the start of the website from desktop to iOS. Thus, I can't even treknet, sits a man with a working table or from the browser.

###Problem 3
Service worker, it's not Serrana bullet. Sorry, but will have to work hard to make it work as you want.

And so, we all know that mobile brazeal and so is the caching system? And that he is all cache level caches?
So, your service-worker-he is also cache level caches. And file that installs your service worker. And the whole thing is rotten through at least 24 hours (this infa about 24 hours are not accurate, but while surfing on the Internet found it). And your new version of the cache, just not coming to man.

I solved this problem, so that adds a version to the cache file, as hasik that the browser always downloads the latest version of the cache and re-installed at the right time I service worker.

 gulp.task('generate-version-sw', () => {
let text = file.readFileSync('dist/service-worker.js', 'utf8');
let version = Math.random().toString(36).slice(2, 2 + Math.max(1, Math.min(10000, 10)))
text = text.replace('v1::', version )
file.writeFileSync('dist/service-worker-' + version + '.js',text)

let text_upload_file = file.readFileSync('app/scripts/upload-service-worker.js', 'utf8');
text_upload_file = text_upload_file.replace('service-worker-file','service-worker-' + version)
 file.writeFileSync('dist/scripts/upload-service-worker-' + version + '.js',text_upload_file)

let text_index = file.readFileSync('dist/index.html', 'utf8');
text_index += '<script src=scripts/upload-service-worker-' + version + '.js></script>'
file.writeFileSync('dist/index.html',text_index)
}
);

The idea is this: we select separate file which sets our service worker and the service worker and let every time they are loaded again, they are not as big and a lot of traffic will not catch up to the user.


That's that, then. Follow us on Twitter https://twitter.com/gaserd123 follow this turnip and if You have any improvements, please send your issue and pr.

Good luck and make the mobile web better.
