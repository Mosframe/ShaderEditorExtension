# WebGL GLSL Shader Editor Extension for Google Chrome

A Chrome DevTools extension to help you edit shaders live in the browser. Very much based on Firefox DevTools Shader Editor. [Here's a video showing it in action](http://www.youtube.com/watch?v=nPcUH3b3pFY)

[Install the extension from the Chrome Store](https://chrome.google.com/webstore/detail/shader-editor/ggeaidddejpbakgafapihjbgdlbbbpob)
[![npm](/about/ChromeWebStore_Badge_v2_496x150.png)](https://chrome.google.com/webstore/detail/shader-editor/ggeaidddejpbakgafapihjbgdlbbbpob)

Twin project of [Web Audio API Editor Extension for Google Chrome](https://github.com/spite/WebAudioExtension)

![Shader Editor](/about/snapshot.jpg)

Some more info about this project: [Creating a Plug'n Play Live WebGL Shader Editor](http://www.clicktorelease.com/blog/live-webgl-shader-editor)

### How to install ###

While in beta, you can load the extension from disk directly:
- Checkout the repo
- Open Chrome's Extensions page (``Settings / More tools / Extensions``)
- Enable ``Developer Mode``
- Click on ``Load unpacked extension`...
- Select the folder /src in the checked out project

Alternatively, you can pack the extension yourself and load by dropping the .crx file in the Extensions page.

### How to use ###

- Browse to a page with WebGL content (you can find many here http://threejs.org/, here https://www.chromeexperiments.com/webgl or here http://www.webgl.com/)
- Open DevTools
- Select the ``Shader Editor`` tab
- The extension needs to instrument ``WebGLRenderingContext``: if you open DevTools after the page has loaded, hit the ``Reload`` button. If the extension was already running, it automatically instruments the page.
- If there are calls to ``.createProgram``, the UI will show a list
- Select a program to see its vertex shader and fragment shader
- Use the Pretty Print icon to make the code more readable; Use the fullscreen button to make the code editor bigger; Use the Eye icon to disable shader highlighting.

### Stuff that works ###

You can expand the editor area by clicking the Fullscreen button on the bottom right corner.

If the shader code is obfuscated, you can click on the Autoformat button.

Enabling extensions is mirrored in the environment to test shaders.

### Stuff that doesn't work ####

Changing stuff in several places probably isn't tracked correctly, so if you edit a shader and the JavaScript in the page also edits it, there'll be weird side-effects.

~~**More importantly: the shader compiling and testing is done with a separate ``WebGLRenderingContext``, so is the page is using extensions, the shader won't compile.** The solution is either track the ``.getExtension`` method and reproduce it in the extension GL context, or pass the testing to the injected library.~~

### TO-DO ###

As always: forks, pull requests and code critiques are welcome!

- ~~Detect when the page is reloaded or changed [Issue #1](https://github.com/spite/ShaderEditorExtension/issues/1)~~
- ~~Highlight shaders when hovering over list item [Issue #3](https://github.com/spite/ShaderEditorExtension/issues/3)~~
- Check why some pages don't load (like http://david.li/flow/) [Issue #4](https://github.com/spite/ShaderEditorExtension/issues/4)
- Figure out why it doesn't .postMessage the first time it's injected [Issue #5](https://github.com/spite/ShaderEditorExtension/issues/5)
- Figure out why it doesn't work on Android over remote debugging [Issue #6](https://github.com/spite/ShaderEditorExtension/issues/6)

Nice to have:

- Save to disk (?) - Not possible for now with the DevTools API
- Add uniform tracking to display values fed to the shader
- ~~Integrating @aras-p + @zz85 [GLSL Optimizer](https://github.com/zz85/glsl-optimizer)~~ [Added](https://github.com/spite/ShaderEditorExtension/commit/cd6c59aef586b1a7d8dfbdbb01e9538fb374a270)
 
#### Changelog ####

[See detailed change log](CHANGELOG.md)

#### License ####

MIT licensed

Copyright (C) 2015 Jaume Sanchez Elias, http://www.clicktorelease.com