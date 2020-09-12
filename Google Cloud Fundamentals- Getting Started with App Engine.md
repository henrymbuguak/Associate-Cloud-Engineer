# Google Cloud Fundamentals: Getting Started with App Engine

## Objectives

- Initialize App Engine.

- Preview an App Engine application running locally in Cloud Shell.

- Deploy an App Engine application, so that others can reach it.

- Disable an App Engine application, when you no longer want it to be visible.


## Step 1

a) Connect to GCP Shell

Click the Activate Cloud Shell button Activate Shell Button at the top of the Console window:

This launches Cloud Shell session in a frame at the bottom of the Console.

b) To list the active account name run this command:

gcloud auth list

## Step 2

a) Initialize App Engine

To initialize the an app engine run the following command:

gcloud app create --project=$DEVSHELL_PROJECT_ID

When prompted, select the region where you want your App Engine application located

b) Clone the Sample project by running the following command

git clone https://github.com/GoogleCloudPlatform/python-docs-samples

c) Navigate to the source directory by running the following command

cd python-docs-samples/appengine/standard_python3/hello_world

## Preview an App Engine application running locally in Cloud Shell

a) In your cloud shell prompt - run the following command to update packages

sudo apt-get update

b) Since it's python project - set up the virtual environment by running the following command

sudo apt-get install virtualenv

If prompted [Y/n], press Y and then Enter.

finally run this command:

virtualenv -p python3 venv

Which creates a virtual environment called venv

c) Activate virtual environment by running the following command:

source venv/bin/activate

d) Navigate to the project root directory and run the following command to install dependecies

pip install  -r requirements.txt

e) Run the application using the following command

python main.py

In Cloud Shell, click Web preview (Web Preview) > Preview on port 8080 to preview the application.

Result: You should see Hello world


## Deploy an App Engine application, so that others can reach it

- To deploy your application navigate to your project using the following command:

cd ~/python-docs-samples/appengine/standard_python3/hello_world

- To deploy run the following command:

gcloud app deploy

- If prompted "Do you want to continue (Y/n)?", press Y and then Enter.

- To launch your browser to view the app at http://YOUR_PROJECT_ID.appspot.com use the following command:

gcloud app browse

## Disable an App Engine application, when you no longer want it to be visible run the following command

gcloud beta app versions stop

