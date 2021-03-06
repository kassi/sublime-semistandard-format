# SemiStandard Format
[![Build Status](https://travis-ci.org/ppxu/sublime-semistandard-format.svg?branch=master)](https://travis-ci.org/ppxu/sublime-semistandard-format)

A Sublime Text 3 plug-in that runs [semistandard --fix](https://github.com/Flet/semistandard) against the javascript code in your ST3 window on save or manually.  Can be toggled on or off.  Includes a few settings that let you tweak your search path to favor local dependencies over global ones.

## Installation

Install SemiStandard Format using [Package Control](https://packagecontrol.io/).

```sh
# In the command palate
- package control install
- semistandard format
```

SemiStandard Format (the Sublime Text Plug-in) requires that you install [`semistandard`](https://github.com/Flet/semistandard) either locally to your project or globally.  It is recomended to save it to your local project.

```sh
$ npm install semistandard@latest --save-dev
```


## Configuration

You can find SemiStandard Format settings in the `SemiStandardFormat.sublime-settings` file.

SemiStandard Format is agressive about finding your developer dependencies.  The search path that it uses by default are in the following order:

- User added paths: you can add an array of paths in your settings file.  You shouldn't need to do this unless you are doing something weird.
- Any `node_modules/.bin` paths found above the current file.  Disable with `use_view_path`
- If your current view isn't saved to disk, any any folders in the project will be walked towards root searching for `node_modules/.bin` to add to the path here.  Disabled with `use_project_path_fallback`.
- The global user path is then used if nothing else is found.  This is calculated by starting a bash instance and calculating the real user path, including `.nvm` shims.

### Other settings:

- `format_on_save`: Boolean.  Runs SemiStandard Format on save when set to true.  Use the command pallet to quickly toggle this on or off.
- `extensions`: String Array.  An array of file extensions that you want to be able to run SemiStandard Format against.

- `command`: **Optional** String Array.  Customize the command and flags that **SemiStandard Format** runs against.

- `loud_error`: Boolean.  Specifies if you get a status bar message or error window if the subprocess encounters an error while formatting.

- `log_errors`: Boolean. Lets you log out errors encountered by the formatter.  Mainly used to suppress noisy formatting errors.

## Hints

Windows is now supported.  Please open any issues that you come across.

## Linter

SemiStandard Format pairs nicely with the Sublime Text `semistandard` linter:

- [Flet/SublimeLinter-contrib-semistandard](https://github.com/Flet/SublimeLinter-contrib-semistandard)

## References

- https://github.com/piuccio/sublime-esformatter
- https://github.com/ionutvmi/sublime-jsfmt
- https://github.com/enginespot/js-beautify-sublime
- https://github.com/jdc0589/JsFormat/commits/master
- https://github.com/akalongman/sublimetext-codeformatter
- https://github.com/DisposaBoy/GoSublime
- https://github.com/feross/standard
- https://github.com/Flet/semistandard
- https://github.com/Flet/SublimeLinter-contrib-standard
- https://github.com/Flet/SublimeLinter-contrib-semistandard
- https://github.com/bcomnes/sublime-standard-format

