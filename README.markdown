StartExplorer
=============

[![Build Status](https://secure.travis-ci.org/basti1302/startexplorer.png)](http://travis-ci.org/basti1302/startexplorer)

Just drag-and-drop the button to the Eclipse menu bar to install the plug-in:<br/>

<a href="http://marketplace.eclipse.org/marketplace-client-intro?mpc_install=641101" title="Drag and drop into a running Eclipse workspace to install StartExplorer">
  <img src="https://marketplace.eclipse.org/sites/all/modules/custom/marketplace/images/installbutton.png"/>
</a>

Eclipse-Update-URL: http://basti1302.github.com/startexplorer/update/

About
-----

The StartExplorer Eclipse plug-in offers tight integration of the system file manager (Windows Explorer, Gnome Nautilus, KDE Konqueror, Mac Finder, ...) and the shell (cmd.exe, Linux/Mac terminal) in Eclipse.

Every now and then when working with Eclipse you'd like to examine a file or a folder inside the Eclipse workspace with your file manager or open a shell/cmd.exe in this location. Or you edit a file in Eclipse and would like to open the parent folder of this file in the file manager or shell. Or the file you are editing contains a string which references another file in the filesystem and you would like to do some of the things mentioned above with that referenced file. This plug-in gives you a convenient way to do all this by adding a few entries to Eclipse's context menus. Furthermore, it offers a different, more convenient way to issue any shell/dos command you like through customizable menu commands. Last but not the least this plug-in offers a tighter integration of the clip board, so copying a file's/folder's path to the clip board is only two mouse clicks (instead of opening the Properties dialog and selecting the path manually).

Supported Platforms
-------------------

This plug-in is inherently not platform-independent. Currently, the following operating systems/desktop environments are supported out of the box:

* Windows
* Mac OS
* Linux with Gnome
* Linux with KDE
* Linux with Xfce
* Linux with LXDE

However, even if your system is not listed there, you can still easily configure
StartExplorer to work correctly on your system.

Features
--------

* Start file manager in selected folder from Eclipse Package Explorer/Project Explorer/Navigator
* Start shell in selected folder from Eclipse Package Explorer/Project Explorer/Navigator
* Start the default system app for any file from Eclipse Package Explorer/Project Explorer/Navigator
* From Eclipse Package Explorer/Project Explorer/Navigator, copy any resource's path directly to the clipboard, without having to select it manually in the Properties dialog
* Define custom commands and execute them on any resource in the Eclipse Package Explorer/Project Explorer/Navigator
* Do all of the above for multiple selected files/folders
* Select a text region in any Eclipse editor; if the selected text is a file system path, you can start a file manager in this location
* Select a text region in any Eclipse editor; if the selected text is a file system path, you can start a shell in this location
* Select a text region in any Eclipse editor; if the selected text is a file system path, you can start the default system application for this file
* Define custom commands and execute them on the file/folder represented by the current selection in any Eclipse editor
* Select a text region in any Eclipse editor and pass the selected text to any application in your system

But...
------

Eclipse can do some things that are quite similar what this plug-in offers out of the box. This section explains the subtle differences.

### But I can copy the file system path of a resource (file or folder) to the clipboard without the plug-in! Why should I use StartExplorer for that?
Yes, by right clicking the resource, selecting properties and then selecting the complete content of the location field with the mouse. In my humble opinion, that's quite clumsy.

### But I can open files with the default system application by using "Open With - System Editor" without the plug-in! Why should I use StartExplorer for that?
Yes, that's indeed quite redundant. It might be removed in future versions of the plug-in. One minor difference, though: Eclipse remembers that you opened the file with the system editor and the next time you open it, it will be opened with the system editor again. StartExplorer does not have this kind of memory. Most often, the Eclipse behaviour is probably what you want, sometimes it's not.


Alternatives
------------

There is always more than one way to skin a cat. Or to open a file manager window. It seems many people miss this functionality in Eclipse and some of them (like me) wrote plug-ins to ease their pain. I'll list all I know of here. If you know another open-file-manager-plug-in, let me know. I also list some pros and cons, which, of course, are completely subjective.

* EasyShell (http://marketplace.eclipse.org/content/easyshell)
  * (+) Cross platform
  * (+) Still maintained
  * (+) Configurable to adapt to any operating system/desktop environment
  * (+) Supports PowerShell and Cygwin on Windows out of the box
  * (-) No custom commands
  * (-) Does not support standard Eclipse variables
  * (-) No integrated help in Eclipse
* OpenExplorer (http://blog.samsonis.me/2009/02/open-explorer-plugin-for-eclipse/)
  * (+) Cross platform
  * (+) Still maintained
  * (-) No shell integration (only file manager)
  * (-) No custom commands
  * (-) No integrated help in Eclipse
* ExploreFS (http://junginger.biz/eclipse/)
  * (+) cross platform
  * (-) No shell integration (only file manager)
  * (-) No custom commands
  * (-) No integrated help in Eclipse
* easyexplore - outdated, not maintained anymore (http://market.eclipsesource.com/yoxos/node/org.sf.easyexplore.feature.group)
* Eclipse Explorer - seemed to exist once, can't find it anymore
* Launch Explorer via external tools (http://www.eclipsezone.com/eclipse/forums/t77655.html)
  * (-) Cumbersome approach (for my taste)

To the best of my knowledge, at the time of writing (March 2012), StartExplorer has some unique features that none of its competitors offer (and it has most, if not all, features that its competitors have):

* Custom commands
* Comprehensive help in Eclipse
* Best configurability
* Supports all Eclipse variables (and some variables that StartExplorer adds) in custom commands as well as custom desktop environments.

Hacking
----------

If you want to hack on StartExplorer, you need Eclipse with PDE (Plugin Development Environment) with a few pre-requisites. Most JUnit tests use Mockito and some use PowerMock in addition to Mockito. To avoid compile errors you need to download these libraries and their dependencies. The people from PowerMock provide a nice all-in-one package: [powermock-mockito-junit-1.5.zip](https://powermock.googlecode.com/files/powermock-mockito-junit-1.5.zip).

After unpacking this you need to set a bunch of classpath variables. In Eclipse, go to Window -> Preferences -> Java -> Build Path -> Classpath Variables. Add the following variables (by clicking "New...", obviously):
* JUnit-Library (junit-4.8.2.jar in the zip file mentioned above)
* Mockito-Library (mockito-all-1.9.5.jar in the zip file mentioned above)
* PowerMock-Library (powermock-mockito-1.5-full.jar in the zip file mentioned above)
* CGLib-Library (cglib-nodep-2.2.jar in the zip file mentioned above)
* Javassist-Library (javassist-3.17.1-GA.jar in the zip file mentioned above)
* Objenesis-Library (objenesis-1.2.jar in the zip file mentioned above)

Also in Eclipse, you should have at least two projects, the plug-in project and the feature project:
* The plug-in project should point to the plugin subfolder of this git repository,
* The feature project should point to the feature subfolder of this git repository.
* You can create both projects by using File - Import - General - Existing Projects into Workspace and selecting the folder as given above
* You can also import the complete git-repository (that is, the parent folder of plugin and feature) into Eclipse, for example, if you need to change this file (README.markdown).
* In addition, you might want to check out the branch gh-pages to a separate location (required for building and publishing new versions to the update site).

### Optional maven build

[Maven](http://maven.apache.org/) build (using [Tycho plugin](http://eclipse.org/tycho/)) is headless build, that doesn't require Eclipse.

From base folder just run `mvn package`. Run offline when to re-build `mvn clean package -o`. 

#### Install site.zip (quick and simple way)

1. Locate zip file under `site\target` in Project Explorer, StartExplore-> Copy Resource Path to Clipboard
2. Help -> Install New Software ...
3. <kbd>Add...</kbd>
4. <kbd>Archive...</kbd>
5. Insert copied string into name and path.  
 E.g. `C:\Users\pverest\git\startexplorer\site\target\de.bastiankrol.startexplorer.site-1.4.1.zip`
 
For the next time just select the zip entry from Work With drop-down list. 

Release Notes
-------------

### Version 1.4.1 (2013-03-25)

* Bugfix for paths with whitespaces on Windows, which had been broken due to the fix for issue #23.
* Added built-in configuration for msys Git Bash/Git for Windows.

### Version 1.4.0 (2013-03-24)

* Bugfix for paths with whitespaces on Gnome (GitHub issue #23).

### Version 1.3.0 (2013-03-04)

* Switched to more permissive license to allow redistribution of StartExplorer in Eclipse distributions (GitHub issue #22).

### Version 1.2.1 (2012-08-17)

* Fix GitHub issue #19: Custom commands now work in Eclipse 4.2/Juno

### Version 1.2.0 (2012-03-14)

* Custom Commands can be stored as files in one of your projects in the workspace instead of the preference store. They will be imported automatically on Eclipse startup. This makes it possible to share custom commands in a version control system, for example to share them with your team.
* Copy Resource Path to Clipboard from editor window now always uses the file opened in editor and never the selected text region.

### Version 1.1.3 (2012-03-02)

* Bugfix for problem with StartExplorer's own variables.

### Version 1.1.2 (2012-03-02)

* Support for all Eclipse variables: Custom commands and custom desktop environments are now integrated with the standard Eclipse mechanism and thus support all variables that are defined in your Eclipse installation/workspace. This includes well known variables like `workspace_loc` and `project_loc`, but generally every variable that is defined, either by Eclipse or by any installed plug-in or that has been added manually (for example via Preferences -> Run/Debug -> String Substitution) can be used in custom command definitions and the command definitions for and custom desktop environments. Variables that take arguments are also supported. The content assist functionality in the preference pages will show all available variables.
* Custom commands can be exported to and imported from JSON files. Thus, command definitions can be shared with other users.
* Added predefined configurations for
  * Windows + PowerShell (uses powershell.exe instead of cmd.exe as shell)
  * Windows + Cygwin (uses bash.exe instead of cmd.exe as shell)
* Bugfix: Pressing Cancel in the dialog for adding a new custom command added an empty custom command to the list.

### Version 1.0.4 (2012-02-28)

* Help files updated because of move to GitHub
* Help files table of contents fixed

### Version 1.0.0 (2012-02-23)

* Finally, this plug-in supports Linux and Mac OS and not only Windows!
* Bugfix: Select File in File Manager option was neither stored nor used.

### Version 0.9.0 (2012-02-16)

* Context Assist for variables in configuration dialog for custom commands.
* You can now configure the resource type a custom command is intended for, either "Files", "Folders" or "Files & Folders". If a custom command that is intended for files is execute on a directory, a dialog box with an error message is shown and no action is taken. If, on the other hand, a custom command intended for a folder is executed on a file, the command automatically uses the parent directory. Finally, for a custom command that is intended for files & folders, no such check is executed before invoking the command.
* "Copy resource path to clipboard" is now also available from the editor view. This didn't make sense before (because it more or less would only copy the selected text to the clipboard) but in connection with the feature to use the file opened in editor when the text selection is empty this is quite useful. By executing this on an empty text selection, you can now copy the path of the edited file directly to your clipboard.

### Version 0.8.0 (2012-02-14)

* Changed behaviour for "Show resource(s) in Windows Explorer" and "Start a Windows Explorer in this path": if you select a file (not a directory), the corresponding file will be selected in the Windows Explorer instance that is to be opened. This new behaviour can be disabled by unchecking "Select File In Explorer" in the preference page.

### Version 0.7.0 (2012-02-12)

* Now it is possible to invoke the StartExplorer commands (predefined and custom ones) from the editor window for the file currently opened in the editor. If the current text selection is empty, the file being edited will be used for "Start Windows Explorer", "Start file with system editor", "Start cmd.exe", ...
* New defaults for custom commands. The default custom command "Edit with UltraEdit" has been discarded, instead, there are two custom commands using Notepad and one that echos all variables just to showcase which variables can be used.

### Version 0.6.2 (2012-02-09)

* Comprehensive Eclipse Help documenation. Go to Help -> Help Contents -> StartExplorer Help to read it.
* Two new variables: In addition to `${resource_path}`, `${resource_name}` and `${resource_parent}`, there are now two new variables:
  - `${resource_name_without_extension}`: File name or directory name of the resource, without path and without extension
  - `${resource_extension}`: Only the file's extension (aka suffix)

### Version 0.5.0 (2009-05-04)
