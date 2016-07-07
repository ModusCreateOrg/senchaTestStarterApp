# E2E && Integration tests

## Install requirements using the following commands:
change dir to _'/test/e2e/'_
change dir to _'/test/integration/'_

- Follow the installation steps for Sencha Studio and STC:
 - http://docs.sencha.com/sencha_test/guides/sencha_test_installation.html
- Make sure you have node > 4.2.1. You can use nvm: https://www.npmjs.com/package/nvm
- E2E tests Configuration:
 - Install Selenium Standalone Server: 
  - `cd tests/e2e`
  - `./install.sh`
   - If no permissions to run then `chmod +x install.sh` and run again.
 - Start Selenium Standalone Server: 
  - `./start.sh`
- Integration tests Configuration:
 - Install Selenium Standalone Server: 
  - `cd tests/integration`
  - `./install.sh`
   - If no permissions to run then `chmod +x install.sh` and run again.
 - Start Selenium Standalone Server: 
  - `./start.sh`

## Run the tests with STC
change dir to _'/test/e2e/'_
change dir to _'/test/integration/'_

- To run all tests in `/tests`, run in terminal:
 - `./run-tests-chrome.sh`
 - `./run-tests.sh`
- To run tests from different scopes and other browsers:
 - `stc run -o output -p pool -s scenario`
  - o <output> - Output format. Supported values are text, teamcity and junit
  - p <pool> - Name of the pool from whence tests will be executed. This must be a pool associated with a browser farm 
  - s <scenario> - Path to the scenario to be executed. If unspecified, defaults to the current directory.
  - More info at http://docs.sencha.com/sencha_test/guides/command_line_archive_server.html
 - eg: `stc run -p "firefox" -s tests/ui-tests`


# Performance tests
Tests are using a version of jMeter 3.0 with custom plugins

## Install requirements

- install java JDK and add to path
- unzip _test/performance/apache_jmeter_3.0.zip_
- open _bin/jmeter.exec_ and edit the following (if not already edited):
```
line 91 to: HEAP="-Xms2048m -Xmx2048m"
line 96 to: NEW="-XX:NewSize=512m -XX:MaxNewSize=512m"
```

## Run the tests

- File > Open > [choose _PerformanceTests.jmx_]
- under _jMeter Users_ Thread Group change:
```
Number of Threads to desired value: Default = 10
Loop Count to desired value: Default = 10
```
 - this means 10 concurrent users for 10 times
- Run > Start
 
## Inspect the results
There are 4 listeners at the end of the Thread Group that provide useful info.



