# SourceTree for Windows Beta Program
The following is s et of useful hints and tips for the SourceTree for Windows Beta program.
All details are subject to change.

## Installation
Currently the production version of SourceTree for Windows uses an installer built using AdvancedInstaller, http://www.advancedinstaller.com/, for the Beta program we are trialling an installer built using Squirrel, https://github.com/Squirrel/Squirrel.Windows.

### How To Install

* Download the _.exe_ installer
* Double click the installer
* This will display a splash screen while it installs
* SourceTree Beta will start automatically after installation completes.

The change in the installer results in a number of differences in the installation.

### Binaries location
* Production: 
    * c:\program files (x86)\Atlassian\SourceTree
* Beta: 
    * %localappdata%\SourceTree

### Data location
* Production: 
    * %localappdata%\Atlassian\SourceTree
        * embedded dvcs installs
        * account settings
        * bookmarks
        * history
        * logging
    * %localappdata%\Atlassian\SourceTree.exe_Url_{hash}\{version}
        * user.config
* Beta: 
    * %localappdata%\SourceTree\AppData\Local\Atlassian\SourceTree
        * embedded dvcs installs
        * account settings
        * bookmarks
        * history
        * logging
    * %localappdata%\Atlassian\SourceTree.exe_Url_{hash}\{version}
        * user.config
        
At this time the Beta intentionally does *NOT* share the same data as a production installation. This is to isolate the Beta and allow it flexibility to change data formats etc without affecting any production installation.
It is possible to override this isolation by changing the application's configuration. See _Useful Settings_ below

## Update

The change to Squirrel from AdvancedInstaller has changed the update process. At this time this is semi-manual, it requires the user to check for updates. More automation to this process is coming.

### How To Update

* In SourceTree Beta open the Tools/Options/Updates tab.
* Click the _Check for Updates_ button.
* The status message will indicate if there is a newer version.
* If there is, clicking the _Update_ button will download and install the update
* Restart SourceTree to use the new version.

## Configuration
Application level configuration is held in *SourceTree.exe.config* file held in the binaries folder.

### Useful Settings

To allow a Beta install to access production data, e.g. bookmarks etc, change the following seting to _True_

      <setting name="IsPortable" serializeAs="String">
        <value>False</value>
      </setting>   

This change effects
        * embedded dvcs installs
        * account settings
        * bookmarks
        * history
        * logging
        
It does not effect the user.config settings as these are held in a version specific folder to the application version.

## Error Handling

SourceTree for Windows Beta is trialling the use of BugSplat, http://www.bugsplatsoftware.com/, to improve the reporting of application crashes.

This has the advantage of simplifying the reporting process for users and provides developers with detail, categorised error reports.

After any application crash the user will be prompted to by a dialog to report the crash with and feedback. This is entirely optional, although we would encourage users to make use of the service.

No personal information is transfered.

Please raise any other issues at https://jira.atlassian.com/projects/SRCTREEWIN and set the "Affects Version" field to the relevant _#.#.#.#-beta_ version