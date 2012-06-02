# Setup Dev environment under OSX
These note were taken on 2012-03-06. after OSX Lion clean Install

## Software

### Userland
* __Google Chrome__
    * Xmarks: [for Chrome](https://chrome.google.com/webstore/detail/ajpgkpeckebdhofmmjfgcjjiiejpodla)
    * Delicious: [for Chrome](https://chrome.google.com/webstore/detail/gclkcflnjahgejhappicbhcpllkpakej)
    * JSONView:[for Chrome](https://chrome.google.com/webstore/detail/chklaanhfefbnpoihckbnefhakgolnmc)
    * Window_Resizer: [for Chrome](https://chrome.google.com/webstore/detail/kkelicaakdanhinjdeammmilcgefonfh)
    
* __Lastpass__: Basic authentication for Mac OS X requires that you enable access for assistive devices. In OS X  10.7 or less by going to Apple > System Preferences > Universal Access and checking "Enable access for assistive devices".
* __Dropbox__
* __Skype__
* __Growl__: ? 1.3 in app store 1.99$
* __MenuMeters__:
    copied settings from `dirac:/Library/Preferences/com.ragingmenace.MenuMeters.plist`

### Developpment
* __Textmate__
   Zipped from dirac/Applications/Into Dropbox/peered
* __Git__: from osx installer  

        git config --global user.name "Daniel Lauzon"
        git config --global daniel.lauzon@gmail.com
        ssh-keygen -t rsa -C "daniel@newmachine"
        pbcopy < ~/.ssh/id_rsa.pub

* __node/npm__ - use pkg installer, dirac still uses [n](https://github.com/visionmedia/n); :

    * convineiece global npm packages:  json, http-server, nodester-cli
    
* __Ruby Gems__: vmc, aws-s3   
* __Xcode__ - from Appstore  
  w/ Command Line Tools for Xcode - Prefs/Downloads/Command Line Tolls -> install
* __VirtualBox__
* __Vagrant__: from installer
* __Propane__ - license in gmail - 2011-05-16
* __SourceTree__ - no license required anymore - but in gmail 2011-11-25
* _iTerm2_: _not yet_

#### JSlint/JSHint/UglifyJS/JSBeautifier
* [JSLint (node)](https://github.com/reid/node-jslint)
* [JSHint (node)](https://github.com/jshint/node-jshint)
* [JSBeautifier (.org)](https://github.com/einars/js-beautify)
* [UglifyJS (node)](https://github.com/mishoo/UglifyJS)

          # how many of these can there be ?
          npm i beautifier beautifyjs js-beautify-node jsbeautify node-beautify
          jsbeautify looks closest to source
          for i in `find node_modules/ -name beautify.js`; do echo $i "-+-+-+-+-+-+-+-+-+-+-+-"; diff -b js-beautify/beautify.js $i|wc -l; done
          # example run
          node  ./node_modules/jsbeautify/bin/jsbeautify   node-snippet.js node-snippet-b.js -s -i 2

from http://stackoverflow.com/questions/5516010/textmate-reformat-with-2-spaces
To make it a bit more flexible, use the TextMate environment variable TM_TAB_SIZE, as in print js_beautify( $input, getenv('TM_TAB_SIZE' ) );, which should update how the command operates if you ever change your tab size.

To get all env, type env into a new file and execute it from textmate: ^R

To install Get Budles: 
https://gist.github.com/2722805
http://al3x.net/2008/12/03/how-i-use-textmate.html
-- but there is also a git repo at: https://github.com/adamsalter/GetBundles.tmbundle

#### Editor / plugins - formatting/linting
* _TextMate_: [JSLintmate](http://rondevera.github.com/jslintmate/); jslint/jshint
* _TextMate_: [Solarized](http://ethanschoonover.com/solarized) theme for textmate: [github repo](https://github.com/deplorableword/textmate-solarized)
* _Sublime_: [Package Control](http://wbond.net/sublime_packages/package_control)
* _Sublime_: [Sublime JSHint](https://github.com/victorporof/Sublime-JSHint)
* _Sublime_: [Sublime HTMLPrettify](https://github.com/victorporof/Sublime-HTMLPrettify)
* _Sublime_: [Sublime JSFormat](https://github.com/jdc0589/JsFormat)

## Settings
Would probably be best to setup a repo for dotfiles.
* Sharing - Remote Login
* Clock
* System Prefs/Network/Advanced/DNS/ search domains: imetrical.com
* .profile (from dirac) 