# GCP Fundamentals: Getting Started with App Engine

## Objectives
#### At the end of this lab, I would be able to

- Initialize App Engine.
- Preview an App Engine application running locally in Cloud Shell.
- Deploy an App Engine application, so that others can reach it.
- Disable an App Engine application, when you no longer want it to be visible.


### Steps

#### 1. Initialize App Engine.
I activated the Google Cloud Shell 
###### I initialised the App Engine app via Cloud Shell and selected [14] uscentral1 when I was prompted.
            gcloud app create --project=qwiklabs-gcp-04-9733c5ef3d3f

###### I cloned the source code repository for a sample application in the hello_world directory.
            git clone https://github.com/GoogleCloudPlatform/python-docs-samples

###### I navigated to the source directory.
            cd python-docs-samples/appengine/standard_python3/hello_world

#### 2. Preview an App Engine application running locally in the Cloud Shell.
###### I downloaded and updated the packages list, with the command below:
            sudo apt-get update

###### I set up a virtual environment to run the application. I have used a Python virtual environments to enable me isolate the installations from the system. When prompted, I entered [Y].
            sudo apt-get install virtualenv
            virtualenv -p python3 venv

###### I activated the environment and navigated to the project directory to install the dependencies for running the application.
            source venv/bin/activate
            pip install  -r requirements.txt

###### I ran the Application. I previewed the application on port 8080 via the Web Preview button on the Cloud Shell. I was redirected to a web page with the url *https://8080-dot-14084812-dot-devshell.appspot.com/?authuser=1*. 
###### *Hello World!* was displayed on the web page.
            python main.py

#### 3. Deploy and run *Hello World!* on an App Engine.
###### I navigated to the source directory, to deploy the application the App Engine standard environment.
            cd ~/python-docs-samples/appengine/standard_python3/hello_world

###### I used the following command to deploy the *Hello World!* application. I entered [Y] when prompted. The app deploy command uses the app.yaml file to identify the project configuration.
            gcloud app deploy

###### To  view the application, I launched a browser at *http://qwiklabs-gcp-04-9733c5ef3d3f.appspot.com*. I copied the url in a new browser window to view the *Hello World!* application.
            
#### 4. Disable the App Engine application.
###### There is no command to undeploy an application that has been deployed. However, the application can be disabled to stop the application from running instances and serving requests. To disable an application, you click on the *Disable Application* on the application on the App Engine settings page. When prompted, the App ID is entered. Click Disable.
###### For this project, I elected to shut down the project instead. Shutting down a project is a more permanent way to  free up resources used on the project and disable billing for associated resources utilised by the project.
            gcloud projects delete