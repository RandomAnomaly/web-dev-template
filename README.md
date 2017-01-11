# web-dev-template

## Description
A basic template setup for web development.
I found I kept having to do the same things over and over again when beginning a new development project, so decided to keep a template of my most common setup.

This includes a (very basic) folder structure, some placeholder html, css and javascript, a package.json file and a gulp pipeline.
When using this you should change the package.json to match your project, though it is not recommended you remove anything from the dev dependencies.

## Setup
1. Clone the repository so you have a local copy.
2. Ensure you have npm / node.js installed, then run the command `npm install gulp -g` to ensure you have a global version of gulp set up on your machine.
3. Now run the command `npm install` in the same directory as the package.json file to install the gulp dependencies. Run the command with the `--verbose` option to see a bunch of text fly by super fast and feel like a 90s movie hacker.
4. Now you're free to go! Check out the next section to see what stuff you can do with the basic pipeline.

## Basic use flow
Simply use the `gulp watch` command and begin working within the dev directory. A browser window will open and refresh as you save changes to your files. As always, use `Ctrl + C` to halt the current job.

## What's in the pipeline?
The gulpfile is preconfigured with a few common things that I find myself using regularly. Below is a list of the jobs that can be run as `gulp <command>`:

Command | What does it do?
--- | ---
`gulp` | Runs the default task, which runs the `clean`, `uglify` and `copy-images` tasks.
`gulp clean` | Deletes the 'dist' directory (if it exists).
`gulp copy-images` | Copies all jpg images from the dev/bin/ directory to dist/bin/
`gulp jshint` | Runs jshint on the javascript files in dev/scripts/ and displays them using the stylish reporter.
`gulp uglify` | Minifies the css and javascript files referenced in between the build tags in the html files. Combines these files together, gives them a versioning number and put them in the dist folder.
`gulp watch` | Runs the `browser-sync` task, then watches for changes in the html, javascript and css files in your dev folder. When they change, triggers another running of the `uglify` task. Watches for changes of image files and kicks off the `copy-images` task.
`gulp browser-sync` | Runs browser-sync, which serves up your HTML files on localhost, and automatically refreshes the page when the files change. The browser-sync job is serving up the version of your files as they exist in dist/, so they will be uglified. For this reason I'd recommend changing the gulpfile to point to the dev version of the files if you use in-browser debugging a lot, or do not use the build tags for these files.

### Build Tags
In your html files, if you put your css link tags in between `build:css` comment tags like this:
```html
<!-- build:css styles/main.css -->
<link rel="stylesheet" href="styles/styles.css">
<link rel="stylesheet" href="styles/styles2.css">
<!-- endbuild -->
```
The pipeline will uglify, combine and attach a pseudorandom version number to the files when outputting them to the dist directory. You can specify what file name you would like by changing the `styles/main.css` part of the opening build tag, and specify multiple build tags. The same may be done with javascript files, in a similar form:
```html
<!-- build:js scripts/main.js -->
<script type="text/javascript" src="scripts/index.js"></script>
<script type="text/javascript" src="scripts/morejavascript.js"></script>
<!-- endbuild -->
```

### Version Number
The version number is a pseudorandom string, and is not used for actual versioning, it simply makes getting around browser caching a bit easier.
