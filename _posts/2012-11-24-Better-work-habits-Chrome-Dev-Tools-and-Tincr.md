---
layout: post
title: Better workflow habits, Chrome Dev Tools & Tincr
permalink: /2012/11/24/Better-work-habits-Chrome-Dev-Tools-and-Tincr
tags:
- development
- Chrome
- tools
---

<p>Alongside <a href="https://www.sublimetext.com/" target="_blank">Sublime Text</a>, Chrome's Dev Tools are essential to my workflow when debugging and fine-tuning JS and CSS. As my work has moved more and more to the frontend of projects, I have noticed how much I flip between the text editor and manually refreshing the page in my browser.</p>

<p>I thought, <em>there has to be a better way...</em></p>

<!--post break-->

<p>Thankfully, there are number of options for automating the frontend development process.</p>

<h4>First up, Chrome Dev Tools' native features.</h4>

<img class="img-fluid" src="/assets/img/save-css-in-chrome.png" alt="save css in chrome" >

<p>My antiquated workflow for css involved copying the new styling and switching back to my text editor to paste it into the CSS file. Besides being too manual, this technique leaves the risk of eagerly refreshing the page and losing changes. With some poking around and experimentation I soon discovered Chrome provides a way to edit the CSS or JS and save directly to the source file (even though Chrome's Dev Tools are feature rich, I find their documentation lacking -- this feature wasn't obvious to me). When inspecting a file in the source tab, the secondary menu provides a way to save the file. Changes are seen immediately while you're building your page and they can easily be saved without leaving the browser.</p>

<p>Since there are a number of reasons for continuing to write the bulk of your code in your text editor (syntax highlighting, snippets, etc), Chrome's native CSS/JS source file saving only covers the debugging/fine-tuning phase of development.</p>

<h4>Enter Tincr.</h4>

<p><a href="https://tin.cr" target="_blank">Tincr</a>, a free Chrome extension, couples the cability of saving changes made in the dev tools to the source file along with refreshing those same files in the browser after saving from a text editor.</p>

<p>Tincr is relatively easy to set up. Once you've installed it through the Chrome Web Store, its instructions cover a variety project configurations. Overall, it works great for a static HTML site. While I haven't given it a spin on a Ruby on Rails project yet, the setup doesn't look too complicated.</p>

<p>My biggest hang up is that I often use <a href="https://sass-lang.com/" target="_blank">Sass</a> or <a href="https://coffeescript.org" target="_blank">Coffeescript</a> during frontend developement. Having Tincr alter the CSS or JS source files won't work since they are rewritten by the compilers. Luckily, Chrome's Dev Tools experiments recently provided a way to edit Sass source files directly while using Tincr to watch the CSS files and reload the page.</p>

<p>In my next post I'll show you how to hook up Chrome's Dev Tools and Tincr so they play nicely with Saas.</p>

