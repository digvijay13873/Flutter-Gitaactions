# FLutter Automation Deployment Using GitActions

![image](https://user-images.githubusercontent.com/71278693/148900145-01b4e632-d2d8-476c-9ef3-126ac9257903.png)


### Objective

Setup Workflow To Build And Release Apps

### What should happen?

1. Flutterflow Push Code To The GIthub Acoount

2. Git actions should get triggered

	a. build apk
	
	b. release apk

Note : Before using git actions compile flutter code on local environment for any errors.
### Note : Workflow is Working In only Main Branch.To Merge Flutterflow branch with main branch Create new Pull Request and merge with main branch.

### How To Merge To MAIN Branch ???

Go to Pull Requests--->New Pull Request

![Screenshot (135)](https://user-images.githubusercontent.com/71278693/149758958-032ac769-800a-4243-bf87-065621f7db92.png)

Set Base Branch as MAIN and Compare branch as FLUTTERFLOW------>Create New Pull Request

![Screenshot (143)](https://user-images.githubusercontent.com/71278693/149761205-b6ddb44b-4c12-475d-b156-425ed9b0c2f3.png)

Merging Changes/Pull Request

![Screenshot (146)](https://user-images.githubusercontent.com/71278693/149761597-2b3357eb-dd07-4b65-83bf-da5add1a7605.png)


# Setting Up New Workflow

### Step 1: 

Navigate to your repo on GitHub, and select the Actions tab.

![image](https://user-images.githubusercontent.com/71278693/148893070-ae70a79c-5ed9-4975-a5df-e1cf5057e89c.png)


### Step 2: 

In the actions tab we can see that there is the option to set up the workflow from scratch by selecting the ‘Set up a workflow yourself’ link, or by leveraging one of the multiple templates provided. It is these templates that make building these workflow simple.
 
![image](https://user-images.githubusercontent.com/71278693/148893125-c8e40f0c-876a-46dd-bac4-3064e6001831.png)


### Step 3: 

By clicking on one of the options, we are sent to the console editor where we can begin building our workflow.

![image](https://user-images.githubusercontent.com/71278693/148895271-8da21f91-e776-4422-af36-61a370edbc4e.png)

 
# Creating a Workflow File

The first thing you have to do is create a .yml file, which is a configuration file that Github Action can understand.
You must store workflow files in the .github/workflows/ directory in your repository. You can name the file whatever you want, for this tutorial name it flutter-ci.yml.
.github/workflows/flutter-ci.yml

### on
Github Actions will execute the workflow following the events under on key. In this example, we want to run it only when we push to master branch but you can add any of your preferred branches.

### job
A workflow run is made up of one or more jobs. For our example, we need only one job.

### runs-on
The type of virtual host machine to run the job on. For our case, we need ubuntu-latest.
Each ubuntu host machine contains different installed software. You can check a list of supported software, tools, and packages in each virtual environment here.

### steps
A job contains a sequence of tasks called steps.
You can have a granular step that runs only one command or a multi-line with a sequence of tasks pack together.
Let’s go through a series of steps in order to meet our requirements.
1. We have to set up the Flutter environment for the Github Actions and for that we will be using subosito/flutter-action .
2. Write the command to get the Flutter dependencies.
```- run: flutter pub get```
3. Check for any formatting issues in the code.
```- run: flutter format --set-exit-if-changed .```
4. Statically analyze the Dart code for any errors.
```- run: flutter analyze .```
5. Run widget tests for our flutter project.
```- run: flutter test```
6. Build an Android APK.
```- run: flutter build apk```
7. Finally, upload our generated app-release.apk for our workflow to the artifacts. For this, we will be using actions/upload-artifact .

![image](https://user-images.githubusercontent.com/71278693/148893564-3a877a9d-cc2d-4a20-88dc-efa389dfd704.png)

**You Can Find Sample Workflow File Here :

https://raw.githubusercontent.com/digvijay13873/Flutter-Automation-Deployment/main/.github/workflows/android.yml
 
  ## Where to find the apk?
  
1.	 Go to your Repository
	 
2.	 On right side of Screen Releases Section

3.	 You can find Your Releases here

![Screenshot (95)](https://user-images.githubusercontent.com/71278693/148894308-443fb82c-7af2-4164-bee8-3ab3ee4a0699.png)


**If You Encounter Any Errors Here Are Some Useful Resources :

https://medium.com/@digvijay13873/fixing-errors-for-flutter-gitactions-automation-6961b21536cc?source=friends_link&sk=f9bc385c2440118b0b74bc50e5294d7b
	
# Flutter Desktop Applications

## Flutter Desktop Release :

Desktop support allows you to compile Flutter source code to a native Windows, macOS, or Linux desktop app. Flutter’s desktop support also extends to plugins—you can install existing plugins that support the Windows, macOS, or Linux platforms, or you can create your own.

### commands : 

for windows platform (same commands can be used for Linux and MacOs plantforms)

### Step : 1

Enable Platform Support

```flutter config --enable-windows-desktop```

### Step : 2

Create Plantform Dependant Runners

```flutter create --platforms=windows,macos,linux .```

### Step : 3

Build Release

```flutter build windows``` 

![image](https://user-images.githubusercontent.com/71278693/149717997-37aa1e67-1041-40c5-8480-8a72eadf203d.png)

## Where To Find Builds ?

For Windows Builds , 

```<project root folder>/build/windows/runner/release```

For Linux Builds , 

```<project root folder>/flutter_navigate2.0/build/linux/x64/release/bundle```

Click Here To Know More :
https://docs.flutter.dev/desktop



