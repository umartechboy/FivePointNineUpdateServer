
#  Qosain Package Manager #
(Formerly known as FivePointNine UpdateServer)
Qosain Package Manger is a data installation and update management service that provides tools for both developers and users to easily get the latest updates using a GitHub cloud as well as offline packages.

# Downloads #
[Qosain Package Explorer](https://github.com/umartechboy/FivePointNineUpdateServer/raw/master/PackageExplorer/QosainPackageExplorer.exe"Download Qosain Package Manager now")
**Note: Your browser and windows may give a warning against the file being downloaded. This is pretty usual when downloading executable files from GitHub and you need to force it to use the the file anyways.**
# Features #
1. A single package doing multiple tasks for content creators and users
2. Create and distribute GitHub cloud based and offline installers
3. Doesn't use any proprietary services
4. Non-admin installations also supported
5. No coding required 

# How does it do it? (Online Mode) #
1. The developer uses Qosain Package Manger to create a release for their content project. 
2. The structured package is uploaded on a GitHub repository, (currently fixed to the current rep).
3. Whenever the developer makes an update, it is uploaded to the same repository along-with any previous updates.
4. The users may now download the universal "Qosain Package Explorer" or the developer's provided "Qosain Package Installer" to install the package along-with any new updates available on their system.
5. The users can check for updates using the universal "Qosain Package Explorer" or the same developer's provided "Qosain Package Installer" in the future.
6. If internet is not available on the target machine, the same GitHub packages can act as standalone, self extracting installers. Even updates can be distributed offline in this fashion.
7. The developer may optionally embed the updater in all their executable packages. This way, they can integrate software updates within their applications.

# Usage #
The same application is used to create, explore, install and update packages. Different functionality is achieved by changing the way the executable is called.

## 1. Installing a Package ##
### Option 1 -- Using Qosain Package Explorer ###
1. Download the Qosain Package Manager from [this GitHub link](https://github.com/umartechboy/FivePointNineUpdateServer/raw/master/PackageExplorer/QosainPackageExplorer.exe"Download Qosain Package Manager now").  (**Note:** don't rename the file after downloading)
**Note: Your browser and windows may give a warning against the file being downloaded. This is pretty usual when downloading executable files from GitHub and you need to force it to use the the file anyways.**
2. Run the program and use the search button to search for your desired package. For convenience, the search bar supports wildcards. This means that you can search for your package without entering the exact name. For example, To search for a package named Qosain PhysLogger Desktop, the search string **qos** * **phys** * **desk** or even **qosa** * **phy**  will make the results include our desired package.
3. Press the "Install" button to open up the installation wizard. 
4. To complete the installation, the wizard provides several installation options like changing the installation directory, letting other users use the same package installation etc.

### Option 2 -- Using the developer provided online installer ###
You may also get a custom installer for your specific package from the developer. Don't rename this file or it may not work as expected. Run the installer which works just like the standard Qosain Package Installer which works just like the standard Qosain Package explorer, except it automatically populates the installation screen only with your required package. The rest of the process is the same as the one used for the package explorer.

### Option 3 -- Using the developer provided offline installer ###
1. If the target computer doesn't have an internet connection, you can request the developer to provide you with an offline installer.
2. Alternatively, using some other internet powered machine, you can make an offline package on your own using Qosain Package Manager which can be downloaded from [this GitHub link](https://github.com/umartechboy/FivePointNineUpdateServer/raw/master/PackageExplorer/QosainPackageExplorer.exe"Download Qosain Package Manager now"). 
3. Just search for your package and instead of installing it, choose the "Re-distribute" option to download and make an offline installation package. 
4. The offline package contains a classic "Setup.exe" file which can install your desired package without using the internet.

## 2. Package Updates ##
### Option 1 -- Manually search for the updates online ###
Updating the application is similar to installing one. A package with newer version automatically detects any previously installed versions and updates it. So, all the methods used for the first instillation can be repeated to update your packages. 

### Option 2 -- Automatic updates ###
For automatic updates,
1. use the update option embedded in your executable packages (the developer may choose not to include embedded updates) or,
2. use the "Update.exe" file which can be found in the package installation directory.  The rest of the process is similar to installing a package.

### Option 3 -- Manually applied offline updates  ###
See [enter link description here](#option-3----using-the-developer-provided-offline-installer) which describes getting an offline installation package. The same process can be used for creating offline update packages.

## 3. Making a new package ##
### a. Basic package creation ###
**Please note that the update manger logically treats the first release just like an update.**
1. Rename the Qosain Package Explorer download from [this GitHub link](https://github.com/umartechboy/FivePointNineUpdateServer/raw/master/PackageExplorer/QosainPackageExplorer.exe"Download Qosain Package Manager now") as "UpdateCreator.exe" (case-insensitive) and copy to the root location of the package.
**Note: Your browser and windows may give a warning against the file being downloaded. This is pretty usual when downloading executable files from GitHub and you need to force it to use the the file anyways.**
2. Run the Exe.
3. Press "Scan" to scan the directory for changes and updates.
4. Optionally, you may add some pre-set post-build commands to the update script which will be executed at the time this update is installed.
5. Create the update package and upload to GitHub.

Creation of a package results in updating/creating these 4 files.
1. A project summary, (root\InstallationPackage\PackageUpdates\Sumamry.txt)
2. A multi-part ZIP update package ((root\InstallationPackage\PackageUpdates\[Update N]/[UpdatePackage.zXX])) which contains any additional files that must be added to the new script. This file cannot be ignored even if it doesn't contain any data (here [Update N] = Release, Update 1, Update 2, Update 3 ... and [UpdatePackage.zXX] = UpdatePackge.zip, UpdatePackge.z01, UpdatePackge.z02 ...
3. The ZIP update package (root\InstallationPackage\PackageUpdates\[Update N]/UpdateScript.txt) which contains necessary information about the update such as integral application version, what's new?, installation and post-installation scripts, etc.
4. A package thumbnail icon (root\InstallationPackage\PackageUpdates\Icon.png)
5. A first-time-only App ID (a Hash code which looks like FBC66FD44955AEE5836A9D161D528DA1)
6. A Setup.exe for offline installation.

### b. Uploading the package to the cloud ###
Uploading the update package files to GitHub is simple.
1. All the update files go to the root of your project directory in the same structure in which they appear within root\InstallationPackage. For example, the update script appears in GitHubRepRoot/PackageName/Update X/UpdateScript.txt. Over-write if a previous summary already exists.
2. Update Summary.txt (mandetory) and Icon.png (optional) under GitHubRepRoot/PackageName/Summary.txt and GitHubRepRoot/PackageName/Icon.png 
3. Also, after the first upload, (Release), append in a newline the complete URL of the Github package root (e.g. https://github.com/username/gitrep/tree/master/Test%20Project%201) to GitHubRepRoot/projects.txt.


### c. Making Offline installer/updater ###
The contents of the directory "root\InstallationPackage" can be distributed as offline installation and update packages. The directory contains a Setup.exe file which will be used by the users to install packages from the offline repository located along-with it in PackageUpdates directory.

### c. Enabling embedded package updates ###
The installer automatically creates an "Update.exe" file in the root folder of the installed package. This file is the same Qosain Package Explorer except it automatically populates the packages list only by the relavent package. In your executable package, call this file and exit the environment within 2-3 seconds, leaving all the files ready to be modified by the updater.

### d. Creating custom online package installers and updaters ###
Rename the latest Qosain Package Explorer as "Installer XX.exe" (XX is the App ID from the update creation step) and you are done! This exe works just like the standard package explorer except it automatically populates the packages list only by the package specified by the XX in the executable's name. Provide your users with this exe with restriction not to rename file which will serve as an all-in-one installer and updater for your custom application.
