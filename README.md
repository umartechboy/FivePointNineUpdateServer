#  Qosain Package Manager #
(Formerly known as FivePointNine UpdateServer)
Qosain Package Manger is an installation and update management service that provides tool for both developers and users to easily get the latest updates using GitHub cloud as well as offline packages.

# What does it do? #
The application provides a system to create cloud based application installation and updates management for projects that receive frequent updates. 

# How does it do it? #
1. The developer uses Qosain Package Manger to create a release for their project. 
2. The release and the project summary is uploaded on a GitHub repository, (currently fixed to the current rep).
3. Whenever the developer makes an update, it is uploaded to the same repository.
4. The users may now download the universal "Qosain Package Explorer" or the developer's provided "Qosain Package Installer" to install the package alongwith any new updates available on their system.
5. The users can check for updates using the universal "Qosain Package Explorer" or the same developer's provided "Qosain Package Installer" in the future.
6. The developer may optionally embed the updater in all their executable packages. This way, they can integrate software updates within their appliactions.

# Usage #
The same application is used to create, explore, install and update packages. Different functionality is achieved by changing the way the executable is called.

## 1. Installing a Package ##
### Option 1 -- Using Qosain Package Explorer ###
1. Download the Qosain Package Manager from [this GitHub link](https://raw.githubusercontent.com/umartechboy/FivePointNineUpdateServer/master/QosainPackageManager.exe "Download the Qosain Package Manager now").  (**Note:** don't rename the file)
2. Run the program and use the search button to search for your desired package. For convenience, the search bar supports wildcards. This means that you can search for your package without entering the exact name. For example, To search for a package named Qosain PhysLogger Desktop, the search string **qos** * **phys** * **desk** or even **qosa** * **phy**  will make the results include our desired package.
3. Press the "Install" button to open up the installation wizard. 
4. To complete the installation, the wizard provides several installation options like changing the installation directory, letting other users use the same package installation etc.

### Option 2 -- Using the developer provided installer ###
You may also get a custom installer for your specific package from the developer. Don't rename this file or it may not work as expected. Run the installer which works just like the standard Qosain Package Explorer, except it automatically populates the installation screen only with your required package. The rest of the process is the same as the one used for the package explorer.

## 2. Package Updates ##

### Option 1 -- Automatic Updates ###
For automatic updates,
1. use the update option embedded in your executable packages (the developer may choose not to include embedded updates) or,
2. use the "updater XX.exe" file (XX refers to a hash code similar to D70911430AB15B6E1CAFA68FFED79C6F) which can be found in the package update installation directory. 

The installer works just like the standard Qosain Package Explorer, except it automatically populates the installation screen only with your required package. The rest of the process is the same as the one used for the package explorer.

### Option 2 -- Using Qosain Package Explorer or Qosain Package Installer ###
Packages can be updated right where they were installed from. The process is similar to installing a new package.
1. Use the developer provided installer or search using Qosain Package Explorer to check if your package has any updates available. If there are any updates, they may be applied using the "Update from vM to vN" button next to your package (N and M are integers).
2. This will open up Qosain Package Updater similar to the one used to install the package; except that it may not offer an option to select the installtion location.

### Offline updates ###
No matter which way the update process is triggered, 

## 3. Making a new cloud based package ##
### a. Basic package creation ###
**Please note that the update manger logically treates the first release just like an update.**
1. Rename the Package Manger as "UpdateCreator.exe" (case-insensetive) and copy to the root location of the package.
2. Run the Exe.
3. Press "Scan" to scan the directory for changes and updates.
4. Optionally, you may add some pre-set post-build commands to the update script which will be executed at the time this update is installed.
5. Create the update package and upload to GitHub.

Creation of a package results in updateion/creation of a first-time-only App ID and three package update files.
1. A project sumamry, (root\InstallationPackage\PackageUpdates\Sumamry.txt)
2. The ZIP update package ((root\InstallationPackage\PackageUpdates\[Update N]/UpdatePackage.zip)) which contains any additional files that must be added to the new script. This file cannot be ignored even if it doesn't contain any data
   where [Update N] = Release, Update 1, Update 2, Update 3 ...
3. The ZIP update package ((root\InstallationPackage\PackageUpdates/[Update N]/UpdateScript.txt)) which contains neccessary information about the update such as integral application version, what's new?, installation and post-installation scripts, etc.

### b. Uploading the package to the cloud ###
Uploading the update package files to github is simple.
1. Sumamry goes to GitHubRepRoot/PackageName/Summary.txt (over-write if a previous summary already exists)
2. UpdatePackage.zip goes to GitHubRepRoot/PackageName/[Update N]/UpdatePackage.zip
3. UpdateScript goes to GitHubRepRoot/PackageName/[Update N]/UpdateScript.txt
4. In the first upload (Release), add an Icon.png file to GitHubRepRoot/PackageName/Icon.png.
5. After the first upload (Release), append in a newline the complete URL of the Github package root (e.g. https://github.com/username/gitrep/tree/master/Test%20Project%201) to GitHubRepRoot/projects.txt.

### c. Enabling embedded package updates ###
The installer automatically creates a "updater XX.exe" (XX is the App ID from the update creation step) file in the root folder of the installed package. This file is the same Qosain Package Explorer except it automatically populates the packages list only by the package specified by the XX in the executable's name. In your executable package, call this file and exit the environment, leaving all the files ready to be modified by the updater.

### d. Creating custom online package installers and updaters ###
Rename the latest Qosain Package Explorer as "Installer XX.exe" (XX is the App ID from the update creation step) and you are done! This exe works just like the standard package explorer except it automatically populates the packages list only by the package specified by the XX in the executable's name. Provide your users with this exe with restriction not to rename file which will serve as an all-in-one installer and updater for your custom application.

## 4. Making a new offline package installer ##
Every now and then, we need to create offline, CD/USB installation packages for our products. For this a similar procedure is used as the one used for online packages.
1. Create the upload package just like the online package except, confirm that "Create an offline Pacakge" is checked in the package creator before pressing the "Create" button.
2. Optionally, you may choose "Create Autorun" to automatically create an autorun compatible with disk/USB drives.
3. The setup may ask for an icon image file which will be used as a thumbnail of the package tile in the installation wizard.
4. Copy the setup.exe (which is essentially the same exe as the standard Qosain package explorer) alongwith the directory "PackageUpdates" and Autorun.inf (if required) to the USB/CD's root.
