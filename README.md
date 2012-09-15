# Servus: Theme Boilerplate

[Servus][servus] is a Mac app to make quick-fire sharing via your 
[Dropbox account][dropbox] easier and more comfortable.  Its preferences allow
you to specify a custom theme for rendering your shared files' preview pages.

This repository contains a bare-bones theme starter kit: a `index.html` with 
all the available placeholders.  Feel free to use it as boilerplate for your 
custom themes.


## How to get started

  1. Either [download starter kit as ZIP file][boilerplate-zip] **or** 
    [fork the starter kit repo on Github][boilerplate-github].
  2. tell Servus to use the folder with the `index.html` in it as custom
    theme folder (Servus ➔ Preferences ➔ Theme ➔ Use custom theme…)
  3. Edit the `index.html` as you see fit, drop files onto the Servus icon
    to see your changes.


## Templating Engine

Servus is making use of [Mustache][mustache], a well-known logic-less 
templating engine.  You can find all you need to know about its syntax on the 
[Mustache website][mustache].


## Theme Workflow

The templating process works like this:

  1. All template files will be copied verbatim to a temporary folder.
  2. All asset files —excluding CSS files and `index.html`— are uploaded
  3. Shareable links for those files are requested from the Dropbox API.
  4. In the CSS files and `index.html` the original references to the local 
     asset files are replaced with their respective shareable counterparts 
     gathered in step 3.  
     As an example, let's assume in your CSS file you reference local theme
     file `background-image.jpg`.  Since each file shared via Dropbox gets its
     own unpredictable path name by the Dropbox API, your local reference to
     that file won't work anymore, so Servus is replacing it with the file's
     shareable URL 
     `https://dl.dropbox.com/s/1234567890abcde/background-image.jpg`.
  5. The CSS files are uploaded, their references are replaced in the
     `index.html`.
  6. The HTML file is uploaded.
  

## Important!

  - Your theme **must** contain an `index.html`.
  - Your theme can contain more than one CSS file and many JS files but only
    *one* `index.html`.  The templating engine won't replace placeholders in 
    JS files, tho, so if you want to set JS variables, do so in a `<script>`
    block in the HTML file prior to loading your external JS file.
  - Servus will ignore subfolders.  Only files in the root folder of your 
    theme are recognized and processed.
  - The templating engine expects UTF-8 encoded files.
  - All your external assets should be served via HTTPS.
    

## Template Placeholders

Here's a list of available template keys/variables with their meaning.

  - `file_link`: the relative path to the shared file as seen from
    `index.html`.
  - `file_ext`: the normalized file extension (trimmed & lowercase).
  - `file_size`: the file size in readable format, eg. "2.70 KB", 
    "5.12 GB".
  - `original_filename`: The name of the file as it was when the file was
    shared.
  - `is_archive`: the file is an archive (zip, tgz, rar etc.)
  - `is_audio`: the file is an audio file (mp3, m4a, wav etc.)
  - `is_contact`: the file is a vcard file
  - `is_image`: the file is an image (png, jpg, tiff, gif etc.)
  - `is_message`: the file is a recognized message (email, IM, and so on)
  - `is_pdf`: the file is a mixed content file, i.e. a PDF.
  - `is_text`: the file is text document (html, rtf, mdown etc.)
  - `is_video`: the file is a video (mov, mpg etc.)
  - `is_unknown_type`: the file wasn't recognized as one of the files 
    listed above
  - `is_ext_*`: a "dynamic" placeholder — for example, if the shared file
    is a GIF then the placeholder `is_ext_gif` would be set.


## Changelog

### September 15, 2012 — Servus 0.9.12

- You can't use many HTML files anymore, only placeholders in `index.html`
  will be processed.
- Rewrote the "Theme Workflow" section as that whole part of Servus was
  rewritten from scratch.
- URL shortening in Servus was removed, so the `short_url` placeholder isn't
  supported anymore.


## Legal

The Servus Default Theme are copyright © 2012 Carlo Zottmann, 
[municode.de](http://municode.de/), carlo@municode.de.

The Servus Theme Boilerplate (this here repository) is licensed under the
WTFPL v2.

               DO WHAT THE FUCK YOU WANT TO PUBLIC LICENSE
                       Version 2, December 2004
    
    Copyright (C) 2004 Sam Hocevar
     14 rue de Plaisance, 75014 Paris, France
    Everyone is permitted to copy and distribute verbatim or modified
    copies of this license document, and changing it is allowed as long
    as the name is changed.
    
               DO WHAT THE FUCK YOU WANT TO PUBLIC LICENSE
      TERMS AND CONDITIONS FOR COPYING, DISTRIBUTION AND MODIFICATION
    
     0. You just DO WHAT THE FUCK YOU WANT TO.



[dropbox]: http://db.tt/T84kkEv
[servus]: http://servus.io
[mustache]: http://mustache.github.com/
[boilerplate-github]: https://github.com/carlo/servus-theme-boilerplate
[boilerplate-zip]: https://github.com/carlo/servus-theme-boilerplate/zipball/master
