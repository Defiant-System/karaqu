## Karaqu CLI

If you are a developer or interested in programming, you can clone repositories from
<a href="//github.com/Defiant-System" target="_new">Karaqu Github</a> and run any application on your computer.

...or even start coding your own application for Karaqu. There are however some requirements.


### Requirements

First requirement for karaqu-cli is to have <a href="//nodejs.org/" target="_new">NodeJS</a> installed on your 
computer. If you are not already familiar with <a href="//nodejs.org/" target="_new">NodeJS</a>, there is excellent
in-depth information at <a href="//en.wikipedia.org/wiki/Node.js" target="_new">WikiPedia</a>. In brief, it is a 
very popular cross-platform environment used by a wide range of companies in even wider range of areas.

The installation of **NodeJS** is pretty straight forward. Download the appropriate installer for your OS and it 
will install basic setup in a few short minutes - you are good to go.


### NPM

With **NodeJS** comes **npm** (_Node Package Manager_) automatically. In the linked
<a href="//en.wikipedia.org/wiki/Npm" target="_new">Wikipedia page</a>, there is a section explaining npm and the 
benefits of it. Once **npm** is available on your computer, enter the following command in Terminal / Shell / Command Prompt
(_depending on your OS_):

```
npm install karaqu-cli -g
```

This will install **karaqu-cli**. The `-g` means that it should be installed globally. _Globally_ means in turn that the
installed command will be available regardless of what directory you are in when using Terminal.


### Congratulations

You have now installed `karaqu-cli`. If you now enter the command **karaqu** in the terminal without any options or
flags, it will print the help section, similar to this:

```
Usage: karaqu <options>

help       --help, -h       Displays this help.
version    --version, -v    Displays version of this tool.
config     --config, -c     Displays last saved login information.
init       --init, -i       When starting a new application use this option to
                            create a empty scaffold file structure. Useful for
                            quick start.
run        --run, -r        Using this option, you can develop individual
                            applications detached from the online Karaqu
                            service. Specify path and port when using this
                            option. Example; karaqu run . 8080
login      --login, -l      In order to publish your application, you need to
                            login to Karaqu and obtain a token that will be
                            used to identify you and your application.
publish    --publish, -p    Once logged in, you can publish your application
                            and it will be available to run in Karaqu online
                            service. Notice that file size limit 5MB and total
                            package size limit is 10MB.
```


### Example

As an example, let's clone a <a href="//github.com/Defiant-System/2048" target="_new">repository</a> or download the 
<a href="//github.com/Defiant-System/2048/archive/refs/heads/master.zip" target="_new">zip</a> of the application **2048**.
It is an application that plays midi files with a synchronised keyboard and visualised notes falling down.
Once downloaded and unpacked - go to the directory of **2048** and run the following command:

```
karaqu run . 8080
```

This is the short explanation of the parts of this command. The `run` option is self-explantory. The `.` is the path to the 
root of the code for the application...and the `8080` is the port we want the application to be launched on.
