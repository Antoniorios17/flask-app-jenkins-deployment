Stage 1: Build
--------------

This stage performs the following actions:

1.  Installs the `python3.10-venv` package using `apt`.
2.  Creates a Python virtual environment named `test3`.
3.  Activates the virtual environment.
4.  Upgrades `pip` to the latest version.
5.  Installs project dependencies from the `requirements.txt` file.
6.  Sets the `FLASK_APP` environment variable.

bashCopy code

`sudo apt install python3.10-venv -y
python3 -m venv test3
source test3/bin/activate
pip install pip --upgrade
pip install -r requirements.txt
export FLASK_APP=application`

Stage 2: Test
-------------

This stage executes the following steps:

1.  Activates the virtual environment created in the previous stage.
2.  Runs tests using `py.test`.
3.  Generates a detailed JUnit XML report.
4.  Utilizes the `always` post condition to ensure collection of the JUnit report regardless of test outcomes.

bashCopy code

`source test3/bin/activate
py.test --verbose --junit-xml test-reports/results.xml`

Stage 3: Packaging the Output Files
-----------------------------------

This stage waits for user input before proceeding. Once input is received, the pipeline takes the following actions:

1.  Zips the specified directory.
2.  Excludes certain files from the zip.
3.  Creates a packaged output file.

User input is required to proceed with this stage.
