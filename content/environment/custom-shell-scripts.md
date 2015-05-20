/*
Title: Executing Custom Shell Scripts
Sort: 2
*/

Ship.io has support for a number of build and test frameworks, but there may be certain tools that your build process depends on. For that reason, we provide a Run Shell Script build step to allow you to extend the functionality of Ship.io
 
First, create a new Run Shell Script build step.

Next, write your script in the text area, and click OK. You are also able to select the shell that you would like your script to run in. Ship.io supports `bash`, `ksh`, `tcsh`, `zsh`, `tclsh`, `ruby`, `python`, and `perl`.

Your custom script build step will execute in order, so any changes you make to the builder will persist until your build has completed. Keep in mind that environment variables that you set will *not* persist.

If your script returns a non-zero exit code, your build step will be marked as "failed".
