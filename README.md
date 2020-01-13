# FivePointNineUpdateServer (now Qosain Package Manager) #
This is a private repository used to store software update packages compatible with FivePointNine Update Server (now Qosain Package Installer).

# What does it do? #
The application provides a system to create cloud based application installation and updates management for projects that receive frequent updates. 

# How does it do it? #
1. The developer uses Qosain Package Manger to create a release for their project. 
2. The release and the project summary is uploaded on a GitHub repository, (currently fixed to the current rep).
3. Whenever the developer makes an update, it is uploaded to the same repository.
4. The clients may now download the universal "Qosain Package Explorer" or the developer's provided "Qosain Package Installer" to install the package alongwith any new updates on their system.
5. The clients can check for updates using the universal "Qosain Package Explorer" or the same developer's provided "Qosain Package Installer".
6. The developer may optionally embed the updater in all their .Net based projects. This way, they can integrate software updates within their appliactions.

# Usage #
The same application is used to create, explore, install and update packages. Different functionality is achieved by changing the way the executable is called.

## 1. Update Creator ##
**Please note that the update manger logically treates the first release just like an update.**
1. Rename the Package Manger as "UpdateCreator.exe" (case-insensetive) and copy to the root location of the package.
2. Run the Exe.
3. Press "Scan" to scan the directory for changes and updates.
4. Optionally, you may add some pre-set post-build commands to the update script which will be executed at the time this update is installed.
5. Create the update package and upload to GitHub.

Creation of a package results in updateion/creation of three files.
1. A project sumamry, (root/ApplicationUpdates/Sumamry.txt)
2. The ZIP update package ((root/ApplicationUpdates/[Update N]/UpdatePackage.zip)) which contains any additional files that must be added to the new script. This file cannot be ignored even if it doesn't contain any data
   where [Update N] = Release, Update 1, Update 2, Update 3 ...
3. The ZIP update package ((root/ApplicationUpdates/[Update N]/UpdateScript.txt)) which contains neccessary information about the update such as integral application version, what's new?, installation and post-installation scripts, etc.

Uploading these files to github is simple.
1. Sumamry goes to GitHubRepRoot/PackageName/Summary.txt (over-write if a previous summary already exists)
2. UpdatePackage.zip goes to GitHubRepRoot/PackageName/[Update N]/UpdatePackage.zip
3. UpdateScript goes to GitHubRepRoot/PackageName/[Update N]/UpdateScript.txt
4. In the first upload (Release), add an Icon.png file to GitHubRepRoot/PackageName/Icon.png.
5. After the first upload (Release), append in a newline the complete URL of the Github package root (e.g. https://github.com/username/gitrep/tree/master/Test%20Project%201) to GitHubRepRoot/projects.txt.
