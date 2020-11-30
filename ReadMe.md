# max-auto-build

This is a sample Max package project created with the [Min-DevKit for Max](https://github.com/Cycling74/min-devkit). This project demonstrates how you can use github actions to automate building, testing and creating releases for your Max packages and externals, for both Mac and Windows platforms. This project is for demonstration purposes only - the instructions below describe how you can set up your own project. Big thanks to the creators of the Min-DevKit for making this possible!

# Prerequisites

Follow the Min-DevKit for Max prerequisites instructions: https://github.com/Cycling74/min-devkit#prerequisites  
Clone the Min-DevKit as described here: https://github.com/Cycling74/min-devkit#building

# Creating a new project

Follow the instructions for creating a new Max package: https://github.com/Cycling74/min-devkit/blob/master/HowTo-NewPackage.md  
  
Once you run `create_package.rb` script, it will also init a git repository for your new project. Add it to github:
  
- create a new repository on github
- navigate to your project folder
- add a remote for the github repository: `git remote add origin YOUR_REPOSITORY_URL`
- rename master branch to main: `git branch -m master main`
- commit what you have so far
- push the initial tag (it was created by the script): `git push origin v0.0.1`  
**^ this step is important! without it the build will fail!**  
- copy `.github` folder from this project - it contains the github actions template file
- commit it - once you do, you should see the build starting under `Actions` tab on github
  
If everything was properly set up, you should see all the jobs turning green, and 2 artifacts will be posted. This should take approximately 5-10 minutes. If the build fails, you should receive an email notification.

# Creating a new release

The actions template is configured so that a new build gets triggered whenever there is a new commit or a pull request. The Release job will only execute when a new tag is committed. Adding a new tag is how you trigger a Release:
  
- create a new tag (replace `0.0.1` with your version number but keep the format!): `git tag -a v0.0.1 -m "put description here"`
- push the tag to the remote (again, replace `0.0.1` with your version number): `git push origin v0.0.1`
  
Once the job executes, it will add a zip file with the complete Max package to the release - you should see it in the list of assets.
