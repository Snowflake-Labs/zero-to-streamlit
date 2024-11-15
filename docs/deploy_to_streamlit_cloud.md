# Deploying Your Streamlit App to Streamlit Cloud

Congratulations on setting up your project using the Streamlit Starter Kit!  In this chapter, we'll take the next exciting step, deploying your bare-bones application to Streamlit Cloud. This will be the starting point of your application-building journey.

Streamlit Cloud is a platform that allows you to easily deploy, manage your Streamlit applications. By deploying your app to Streamlit Cloud, you'll be able to access it from anywhere, collaborate with others, and showcase your work to a wider audience.

In this chapter, we'll cover the following topics:

- [x] Creating a Streamlit Cloud account
- [x] Preparing your app for deployment
- [x] Connecting your GitHub repository to Streamlit Cloud
- [x] Configuring your app settings on Streamlit Cloud
- [x] Deploying your app and accessing it via a public URL
- [x] Making updates to your app and watch application refresh automatically in few seconds

By the end of this chapter, you'll have a live, publicly accessible Streamlit app that serves as a foundation for your application-building exercises. You'll be able to share the URL with others, gather feedback, and iterate on your app as you progress through the tutorial.

Let's dive in and get your app deployed to Streamlit Cloud!

## Navigate to app folder

If you are not on `$TUTORIAL_HOME`, naviaget to it and open the project in VS Code:

```shell
cd $TUTORIAL_HOME
code .
```

## Install and Update Python packages

!!!NOTE
    Defining the right package versions will allow us to deploy the same application to SiS without any trouble.

Update the `$TUTORIAL_HOME/requirements.txt` to be like:

```py title="requirements.txt"
snowflake-cli-labs>=3.1.0,<4.0.0
streamlit==1.35.0
pandas==2.0.3
numpy==1.24.3
scikit-learn==1.3.0
```

## Creating a Python Virtual Environment

We will use [`miniconda`](https://docs.anaconda.com/miniconda/){:target=_blank} to create a Python virtual environment and install all the packages.

Create an environment file `$TUTORIAL_HOME/environment.yml` to be like:

```yaml title="environment.yml"
name: st_ml_app
channels:
  - snowflake
  - conda-forge
dependencies:
  - python=3.11
  - pip
  - pip:
    - -r requirements.txt
```

Run the following command to create the Python virtual environment:

```shell
conda env create -f environment.yml 
```

And activate the environment:

```shell
conda activate st_ml_app
```

!!!TIP "Pro Tip"
    Use [direnv](https://direnv.net){:target=_blank} to de-clutter your local environment. You can create a Python virtual environment simply by creating a file named `.envrc` in your `$TUTORIAL_HOME` with the following content:

    ```shell title=".envrc"
    layout_python
    ```

    Then run `direnv allow .` to create a Python virtual environment in `$TUTORIAL_HOME/.direnv/python-3.11`


## Application Update

Let us start with a small change to the application code.

!!!WARNING
    For the entire tutorial, we will be making changes to the `$TUTORIAL_HOME/streamlit_app.py` file. The code listings will show the entire source with the ==changes== highlighted. This approach helps avoid any copy/paste errors while doing the exercises.

Edit and update the `$TUTORIAL_HOME/streamlit_app.py`:

```py linenums="1" title="streamlit_app.py"
import streamlit as st

st.title("🤖 Machine Learning App")

st.write("Welcome to world of Machine Learning with Streamlit.")
```
Commit the code: 

```shell
git commit -m "First deployment" streamlit_app.py
```

And push the code your remote(`st-ml-app`) Github repository.

!!!NOTE
    You can also do commit and push using VS Code. For the rest of the tutorial, commits and pushes are assumed implicit after each code update.

## Deploying to Streamlit Community Cloud

To deploy the application navigate to <https://streamlit.io>{:target=_blank}, Sign-In and click **Create app**.

You will need the following details for deploying the app,

- **GitHub Repo name** - `<your-gh-user>/st-ml-app`
- **Branch** - `main`
- **Main file path** - `streamlit_app.py`
- **App URL** - choose a public url for your application easiest one to avoid is to use something like `<your gh user>-ml-app`.

Any commit and push to your repository will trigger a new application update. **Give it a try!**

🎉 Great! You have successfully deployed your bare-bones Streamlit app to Streamlit Cloud. Now you're ready to dive into the exciting world of building machine learning applications and discover how Streamlit can enhance that experience.

In the next chapter, we'll start transforming your starter app into a fully-fledged ML application.

