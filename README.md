# Wikipedia apps (for testing purpose only)

These apps are meant to be consumed by Nightwatch.js, as Nightwatch provides some example tests in its initial setup that are based on the Wikipedia app.

These apps are meant for e2e testing purposes only and not for any production use.

## Updating wikipedia apps to latest version

To update wikipedia apps, we need to build them from the source.

### 1. wikipedia-ios

Here are the steps taken to update the Wikipedia iOS app to make it work with iOS 17.

- Go to wikipedia-ios github repo: https://github.com/wikimedia/wikipedia-ios
- Follow “Building and Running” section in README to create `Wikipedia.xcodeproj` file.
- Open the above created file in xcode.
- If required, update the xcode to latest version (to build Wikipedia iOS app for iOS17, I had to have “simulator runtime” for iOS 17 in xcode, for which updating xcode to latest version (v15) was required).
- Open the `Wikipedia.xcodeproj` file in xcode (it will by default open in xcode only).
- In xcode’s title bar (the macos bar at the top which shows all menus), go to Product > Destination and then click on “Any iOS Simulator Device” or select any iPhone from the list.
- Make sure the iOS version of the selected iPhone is the required one (click on “Manage Run Destinations” inside Destination menu to check the iOS version of each device). It should anyway be latest supported by xcode by default.
- Then in the “Product” menu only in macos title bar, click on Build For > Running. Or, just press cmd + r.
- It should build the wikipedia app for you.
- To get the wikipedia’s `.app` file, click on “Product” menu again, then click on “Show Build Folder in Finder”. Inside the opened Finder window, go to “Products” folder, and the whatever is the first folder there, inside that you’ll find a file with Wikipedia logo “crossed diagonally” (if you check the “Get Info” for that file, it should show it as a “Application” file).
- Now, compress this file to create a `wikipedia.zip` file.
- Pull the code from `https://github.com/priyansh3133/wikipedia`, replace the already existing file with the new file, and create a pull request (or directly push to main).
- All done now, just check if the tests work with the new version of app.

Additional notes:
- While running test, if the app doesn’t work properly on the new iOS version simulators, we may require to update appium as well as its `xcuitest` driver.
- If updating `xcuitest` driver to latest version gives error, we may require to uninstall the global installation of `appium` (if present) and then clear npm cache using `npm cache clean --force`.
  
