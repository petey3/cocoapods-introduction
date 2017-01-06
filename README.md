# Cocoapods

> CocoaPods is a dependency manager for Swift and Objective-C Cocoa projects. Its used in just about every iOS project here at Intrepid.

> Here is how to set it up.

## Installing Cocoapods

- Open Terminal
- Enter command: `sudo gem install cocoapods`
- Enter your password

> Wait for this to finish, don't touch your terminal.  It might take a couple minutes

- Run command `pod setup`

## Setting Up Command Line Text Editor

##### Sublime

- Download Sublime <a href="http://www.sublimetext.com/">here</a>
- Install commandline tools following instructions <a href="http://www.sublimetext.com/docs/2/osx_command_line.html">here</a>


##### Atom (My Preference)

- Download Atom <a href="https://atom.io/">here</a>
- Install atom commandline tools by opening Atom and selecting `Atom > Install Shell Commands`

>Continuing forward, all commandline references will use the `atom` keyword.  Replace this with whatever you have designated as your text editor.

## Setting Up Cocoapods

### If New Project

- Create your Xcode Project
- Make sure that Create `git repository` is selected > If you forgot to select this, just continue to the **Existing Project** section

### If Existing Project

If your project is already setup with a git repository, skip this step.
- Open terminal
- Enter command `cd ~/path/to/your/project`
- Enter command `git init`

### Setup Gitignore

- Open terminal
- Enter command `cd ~/path/to/your/project` (if necessary)
- Enter command `atom .gitignore`
- Add `Pods/` to your gitignore
- If your `.gitignore` is empty, add the following:

```
# Xcode
#
build/
*.pbxuser
!default.pbxuser
*.mode1v3
!default.mode1v3
*.mode2v3
!default.mode2v3
*.perspectivev3
!default.perspectivev3
xcuserdata
*.xccheckout
*.moved-aside
DerivedData
*.hmap
*.ipa
*.xcuserstate

# CocoaPods
#
# We recommend against adding the Pods directory to your .gitignore. However
# you should judge for yourself, the pros and cons are mentioned at:
# http://guides.cocoapods.org/using/using-cocoapods.html#should-i-ignore-the-pods-directory-in-source-control
#
Pods/
```

- Save your `.gitignore` file <key>cmd</key> + <key>s</key>

## Add Podfile

### Old Way

- Open terminal
- Enter command `cd ~/path/to/your/project`
- Enter command `atom Podfile`
> This is case SENSITIVE

#### Source

Add a source to the top of your `Podfile`.  If you're unsure what this should be, it should be this:

`source 'https://github.com/CocoaPods/Specs.git'`

#### Platform

Specifying a platform is unncessary, but highly encouraged.  The syntax is:

`platform :<#platform#>, '<#version#>'`

Example:

`platform :ios, '7.0'`

### New Way

- Open terminal
- Enter command `pod init`
- Uncomment the platform line to specify a platform _(ex._ `platform :ios, '8.0'`_)_


### Add Pods

You add pods to your project using the following syntax:

`pod '<#pod name#>', '<#pod version#>'`

A simple example would look like this:

`pod 'AFNetworking', '1.0'`

Or, to get the latest version, you can omit the version from the declaration:

`pod 'AFNetworking'`

There are more complex arguments regarding version available <a href="http://guides.cocoapods.org/syntax/podfile.html#pod">here</a>

### Basic `Podfile` Example

```
source 'https://github.com/CocoaPods/Specs.git'

platform :ios, '9.0'

target 'ProjectName' do
  pod 'SVProgressHUD'
  pod 'AFNetworking'
end
```

> If you already have a workspace created, you'll need to specify this in your podfile by adding: `workspace 'MyWorkspace'`

## Installing Dependencies

Now we're going to integrate our libraries into the Xcode project.

- Close Xcode Project
- Open Terminal
- Enter command `cd ~/path/to/your/project`
- Enter command `pod install`

> Wait for this to finish, depending on the requirements of the `Podfile`, particularly with new projects, this may take a minute or two.  Just leave it.

When cocoapods is done installing libraries, you will get a terminal readout that says:

>[!] From now on use `<#Your Project#>.xcworkspace`.

Follow this instruction and henceforth, **use the workspace** instead of your project.

## Importing And Using Libraries

> In your project, if you want to use a library you can do so by adding

`import SomeCocoaPod`

## More Info on Podfiles

More on the Podfile: http://guides.cocoapods.org/using/the-podfile.html

### Pod Errors

Occasionally, imported libraries will have errors  or warnings generated in Xcode, these can be silenced if desired by adding the following to the `Podfile`

`inhibit_all_warnings!`

To prevent warnings on a library specific basis, you can use the following syntax:

`pod 'SomePodWithWarnings', :inhibit_warnings => true`

### Credit Where Credit Is Due

- These notes are just slightly modified from Logan's https://gist.github.com/LoganWright/5aa9b3deb71e9de628ba
- The dank grape gif is a masterpiece that belongs to FoxADHD

# Follow Up Excercise - Using Cocoapods

### Overview:
Make sure you know how to use cocoapods! To test this knowledge, add a pod to this project and leverage what it has to offer.

### Getting Started:
1. Clone repository (or continue working off your previously cloned repo).
2. Create a new branch off master and name the branch according to the form {name}/cocoapods-exercise  (e.g. epeterson/cocoapods-exercise).

### Your Task:
1. Add this pod to your project: https://github.com/cbpowell/MarqueeLabel
2. Add a marquee'd label to the primary View Controller such that the following is true
 * The marquee's label’s text should begin flush to the left side of the label
 * The marquee scroll should wrap around to its original position after scrolling through the text (traveling left)
 * The marquee's animation curve is EASE IN / EASE OUT
 * The marquee scrolls at 30 pixels per second
 * The marquee will only scroll after being tapped by the user
 * The marquee's text is as follows: "According to all known laws of aviation, there is no way a bee should be able to fly. Its wings are too small to get its fat little body off the ground. The bee, of course, flies anyway because bees don't care what humans think is impossible."
 * There is a 10 pixel buffer between the last character in the label and the first one
3. Open up a Pull Request to be reviewed by your instructor
