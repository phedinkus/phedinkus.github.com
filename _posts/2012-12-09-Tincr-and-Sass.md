---
layout: post
title: Tincr + Sass
permalink: /2012/12/09/Tincr-and-Sass
published: true
tags:
- development
- Chrome
- tools
---

<p>In an <a href="/2012/11/24/Better-work-habits-Chrome-Dev-Tools-and-Tincr/" target="_blank">earlier post</a> I talked about using Tincr to help automate the frontend development workflow instead of flipping between the text editor and the browser. Tincr is great when you are working with straight CSS or JS but so often devs like the benefits of working with a compilation language, like Sass or Coffeescript. While we haven't gotten lucky enough for Coffeescript support in Chrome, Sass support is available.</p>

<!--post break-->

<h4>Sass Setup</h4>
<ol>
  <li>
  <p><strong>Install Tincr.</strong> The setup instructions vary depending on the type of project. (For the sake of brevity, the rest of this post will assume you are running with a simple http server or loading the files directly into the browser. There are instructions on how to setup Tincr for Rails projects but I haven't tried it yet so I can't speak to the difficulty.)</p></li>

  <li><p><strong>Turn on Developer Experiments in Chrome.</strong> Go to Chrome's experiment settings (chrome://flags/), enable the "Developer Tools Experiments" and restart your browser.</p></li>

  <li>
    <p><strong>Enable "Support for Sass".</strong> Open the developer tools settings and select "Support for SASS" under the new Experiments tab.</p>
    <img src="/assets/img/sass-experiment-settings.png" alt="sass experiment settings">
  </li>

  <li>
    <p><strong>Include File Info In Sass Compilation.</strong> Sass files will need to include file location information for parsing the source in Chrome. If you are using the Sass gem to generate your css files during development, include the flag <code>--debug-info</code> on the command line with the <code>--watch</code> command. You can also tell Compass to compile Sass files with debug info in a Rack applications config file:</p>
    <p>
      <code>config.sass_options = {:debug_info => true}</code>
    </p>

    <p>This will create a line before each rule in your css that starts with:</p>
    <p>
      <code>@media -sass-debug-info{...}</code>
    </p>
    <p>NOTE: You'll probably want to regenerate the files without the debug info for production environments...Don't forget to leave off the debug flag before compiling for the real world!!</p>
  </li>
  <li>
    <p><strong>Enable Source Maps.</strong> <a href="https://www.html5rocks.com/en/tutorials/developertools/sourcemaps/" target="_blank">Source Maps</a> are a breakdown of a compiled files initial location. Since we're including the Sass file info in compilation, we'll need to make sure the browser can read that info. To do this, enable source maps in the Chrome under the General Settings tab for the Developer Tools.</p>

    <img src="/assets/img/enable-source-maps.png" alt="enable source maps">

    <p>We can begin editing the file by either clicking the Sass file location shown in the inspector or finding it in the Sources tab in the Developer Tools.</p>
    <img src="/assets/img/sass-location.png" alt="sass location">
  </li>
</ol>
<p>Next up, tools for reloading HTML files.</p>
