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

## What's in the pipeline?
The gulpfile is preconfigured with a few common things that I find myself using regularly. Below is a list of the jobs that can be run as `gulp <command>`:
Command | What does it do?
------- | ----------------
`gulp`  | Runs the default task, which runs the `clean`, `uglify` and `copy-images` tasks
------- | -------------------------------------------------------------------------------
`clean` | Deletes the 'dist' directory (if it exists)
------- | -------------------------------------------------------------------------------



Basic template for beginning web dev. Run npm install -g gulp and npm install to set up.