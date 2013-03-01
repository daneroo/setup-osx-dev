# Setup Dev environment under OSX
These note were taken on 2012-03-06. after OSX Lion clean Install

## Software

### Userland
* __Google Chrome__
    * Xmarks: [for Chrome](https://chrome.google.com/webstore/detail/ajpgkpeckebdhofmmjfgcjjiiejpodla)
    * Delicious: [for Chrome](https://chrome.google.com/webstore/detail/gclkcflnjahgejhappicbhcpllkpakej)
    * JSONView:[for Chrome](https://chrome.google.com/webstore/detail/chklaanhfefbnpoihckbnefhakgolnmc)
    * Window_Resizer: [for Chrome](https://chrome.google.com/webstore/detail/kkelicaakdanhinjdeammmilcgefonfh)
    * [Markdown Preview](https://chrome.google.com/webstore/detail/markdown-preview/jmchmkecamhbiokiopfpnfgbidieafmd)
    
* __Lastpass__: Basic authentication for Mac OS X requires that you enable access for assistive devices. In OS X  10.7 or less by going to Apple > System Preferences > Universal Access and checking "Enable access for assistive devices".
* __Dropbox__
* __Skype__
* __Growl__: ? 1.3 in app store 1.99$
* __MenuMeters__:
    copied settings from `dirac:/Library/Preferences/com.ragingmenace.MenuMeters.plist`

### Synching, Archiving and Cron
Should describe here the 
* Time machine setup
* Dropbox/gdocs
* Dropbox/Camera uploads
* photo, /archive synching
* im-w, im-csa, im-rj

Should have a global check on all these crons

#### GMail Vault Backup
This is setup on dirac, in `Downloads/gmvault-v1.7-beta`
the logs (cron trace) are in that same directory
If we move the bin to /usr/local


    # gmvault GMail backup - daily quick
    00 20,22 * * * cd /Users/daniel/Downloads/gmvault-v1.7-beta; /usr/bin/time ./bin/gmvault sync daniel.lauzon@gmail.com -t quick  > last-gmvault-sync-quick.log 2>&1

    # gmvault GMail backup - weekly full Sunday Midnight
    00 0 * * 0 cd /Users/daniel/Downloads/gmvault-v1.7-beta; /usr/bin/time ./bin/gmvault sync daniel.lauzon@gmail.com -t full  > last-gmvault-sync-full.log 2>&1

### Dotfiles
Well eventually...

But for now only note, that when we install rvm, creating a `.bash_profile`, causes .profile to be ignored, sou we source it (`.profile`) from `.bash_profile` 

### Developpment
* __Textmate__:  
    Zipped from dirac/Applications/Into Dropbox/peered  
    install mate command by selecting Help → Terminal Usage
   
* __Sublime Text 2__: see Package control packages below

* __Git__: from osx installer

        git config --global user.name "Daniel Lauzon"
        git config --global daniel.lauzon@gmail.com
        git config --global color.ui
        ssh-keygen -t rsa -C "daniel@newmachine"
        pbcopy < ~/.ssh/id_rsa.pub

* __homebrew__: [install](http://mxcl.github.com/homebrew/) wget, groovy, iftop, git, rsync  
You might put `/usr/local/bin` before `/usr/bin`
* __node/npm__ - use pkg installer, dirac still uses [n](https://github.com/visionmedia/n):  

    * convineiece global npm packages:  json, http-server, nodester-cli
    
* __Ruby Gems__: vmc, af, fog, (aws-s3 deprecated)  
  `sudo gem install vmc fog --no-ri --no-rdoc`  
  might need fog 0.7.(2|3) for mccloud  
  `vmc target api.cloudfoundry.com`
* __Xcode__ - from Appstore  
  w/ Command Line Tools for Xcode - Prefs/Downloads/Command Line Tools -> install
* __VirtualBox__
* __Vagrant__: from installer
* __Propane__ - license in gmail - 2011-05-16
* __SourceTree__ - no license required anymore - but in gmail 2011-11-25
* _iTerm2_: _not yet_


#### Editor / plugins - formatting/linting
* Sublime:
    * [Package Control](http://wbond.net/sublime_packages/package_control)
    * SidebarEnhancement : open in browser... with Markdown Preview chrome plugin
    * Emmet: e.g. ul>li*4  (superseeded ZenCoding)
    * Sublime Linter
        
    * [Sublime JSFormat](https://github.com/jdc0589/JsFormat)
    * here are my user defined keys

                [
                    {"keys": ["super+shift+["], "command": "js_format"},
                    {"keys": ["ctrl+alt+super+p"], "command": "side_bar_open_in_browser"}
                ]


    * _below are removed for now_
    * [Sublime JSHint](https://github.com/victorporof/Sublime-JSHint)
    * [Sublime HTMLPrettify](https://github.com/victorporof/Sublime-HTMLPrettify) as an alternative to JSFormat
    * [Closure-linter](git://github.com/fbzhong/sublime-closure-linter.git)
    * [sublime-text-jsbeautifier](git://github.com/kriswill/sublime-text-jsbeautifier.git)

* TextMate:
    * [JSLintmate](http://rondevera.github.com/jslintmate/); jslint/jshint
    * [Solarized](http://ethanschoonover.com/solarized) theme for textmate: [github repo](https://github.com/deplorableword/textmate-solarized)
    * [AckMate (Project Search Replacement)](https://github.com/protocool/AckMate)
    * TextMate: [ProjectPlus](http://ciaranwal.sh/2008/08/05/textmate-plug-in-projectplus)
    preferences:PRoject+:SCM (IconPack:Straight)
    * *TextMate*: Too Flaky: [Get Bundles](https://gist.github.com/2722805)
    * [JSTools adamhope](https://github.com/adamhope/js-tools.tmbundle) get from Github.

#### JSlint/JSHint/UglifyJS/JSBeautifier

Requirements: we need to pick jslint/jshint settings.

I have worked my way through my node-snippet and made appropriate changes, and settings
using command-line `npm` global installed `jslint`, and `jshint`.

Both of theese now pass:

        jslint  node-snippet-jslint.js
        jshint  node-snippet-jshint.js

Now using the JSLintMate plugin and pointing it to 
`/usr/local/lib/node_modules/jshint/lib/hint.js` and
`/usr/local/lib/node_modules/jslint/lib/jslint.js` as linters. problem with `unparam`.

The beautifier I was using is the one in JSTools, which is out of date, and caused a few minor irritants: like having to put `(-1)` in parens to avoid a space being inserted, and arrays are quirky. See `ioOpts` and `/incoming ... .join()` in the snippet.

Now I think I will use JSLintmate (straight npm install dependant), and get a similar thing working with jsbeautifier, which will take the editors indent into account. 

**Conslusions**: 

**JSTools** works well, but beautifier is out of date, only has JSLint, and jslint doesn't climb file tree for config.

**subtleGradient/javascript-tools.tmbundle**, don't remember why I stopped using it. Check again. But probably a good place to start to add to JSLintMate... It bundles `npm` https://github.com/dotmaster/js-beautify-node (fork). Also like their snippets, make one for node, browser, jshint, jslint.

* TextMate 3rd party bundles
    * Remove JSLintmate
    * Install [Javascript Tools by subGradient](https://github.com/subtleGradient/javascript-tools.tmbundle)


            cd ~/Library/Application\ Support/TextMate/Pristine\ Copy/Bundles
            git clone https://github.com/subtleGradient/javascript-tools.tmbundle.git
            osascript -e 'tell app "TextMate" to reload bundles'

/usr/bin:/bin:/usr/sbin:/sbin:/usr/local/bin:/usr/local/git/bin:/usr/X11/bin:/opt/local/bin: /usr/local/bin
* Node.js basis

Thes are global install node packages:

* [JSLint (node)](https://github.com/reid/node-jslint)
* [JSHint (node)](https://github.com/jshint/node-jshint)
* [JSBeautifier (.org)](https://github.com/einars/js-beautify)
* [UglifyJS (node)](https://github.com/mishoo/UglifyJS)

          # how many node beautify packages can there be ?
          npm i beautifier beautifyjs js-beautify-node jsbeautify node-beautify
          jsbeautify looks closest to source
          for i in `find node_modules/ -name beautify.js`; do echo $i "-+-+-+-+-+-+-+-+-+-+-+-"; diff -b js-beautify/beautify.js $i|wc -l; done
          # example run
          node  ./node_modules/jsbeautify/bin/jsbeautify   node-snippet.js node-snippet-b.js -s -i 2

* TextMate rolling My own ?

from http://stackoverflow.com/questions/5516010/textmate-reformat-with-2-spaces
To make it a bit more flexible, use the TextMate environment variable TM_TAB_SIZE, as in print js_beautify( $input, getenv('TM_TAB_SIZE' ) );, which should update how the command operates if you ever change your tab size.

To get all env, type env into a new file and execute it from textmate: ^R

* Sublime - rolling my own

in /Users/daniel/Library/Application Support/Sublime Text 2/Packages/Sublime-HTMLPrettify/HTMLPrettify.py

got the 'current tab size from:
print "DDD",json.dumps(self.view.settings().get('tab_size'))

from http://www.sublimetext.com/docs/2/settings.html
{
    "tab_size": 4,
    "translate_tabs_to_spaces": false
}
also: http://www.sublimetext.com/docs/2/indentation.html


## Settings
Would probably be best to setup a repo for dotfiles.
* Sharing - Remote Login
* Clock
* System Prefs/Network/Advanced/DNS/ search domains: imetrical.com
* .profile (from dirac) 