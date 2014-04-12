Selenese Runner Java
====================

This is selenese script interpreter implemented by Java.

It supports test-case and test-suite which are Selenium IDE's native format.

[![Build Status](https://travis-ci.org/vmi/selenese-runner-java.svg?branch=master)](https://travis-ci.org/vmi/selenese-runner-java)

Features
--------

* Run test-case and test-suite generated by Selenium IDE from command line.
* Support commands of Selenium IDE: Flow Control.
  https://github.com/davehunt/selenium-ide-flowcontrol
* Log URL/title/Cookies at all commands.
* Take screenshots at all commands. (optional)
* Override base URL.
* Override directory of screenshot path.
* Generate JUnit XML result.
* Generate HTML result.

Usage
-----

    java -jar selenese-runner.jar <option> ... <test-case|test-suite> ...
    
     -d,--driver <driver>                    firefox (default) | chrome | ie | safari | htmlunit | phantomjs | remote | appium | FQCN-of-WebDriverFactory
     -p,--profile <name>                     profile name (Firefox only)
     -P,--profile-dir <dir>                  profile directory (Firefox only)
        --proxy <proxy>                      proxy host and port (HOST:PORT) (excepting IE)
        --proxy-user <user>                  proxy username (HtmlUnit only *)
        --proxy-password <password>          proxy password (HtmlUnit only *)
        --no-proxy <no-proxy>                no-proxy hosts
        --remote-url <url>                   Remote test runner URL (Remote only)
        --remote-platform <platform>         Desired remote platform (Remote only)
        --remote-browser <browser>           Desired remote browser (Remote only)
        --remote-version <browser-version>   Desired remote browser version (Remote only)
     -H,--highlight                          highlight locator always.
     -s,--screenshot-dir <dir>               override captureEntirePageScreenshot directory.
     -S,--screenshot-all <dir>               take screenshot at all commands to specified directory.
        --screenshot-on-fail <dir>           take screenshot on fail commands to specified directory.
        --ignore-screenshot-command          ignore captureEntirePageScreenshot command.
     -b,--baseurl <baseURL>                  override base URL set in selenese.
        --chromedriver <path>                path to 'chromedriver' binary. (implies '--driver chrome')
        --iedriver <path>                    path to 'IEDriverServer' binary. (implies '--driver ie')
        --phantomjs <path>                   path to 'phantomjs' binary. (implies '--driver phantomjs')
        --xml-result <dir>                   output XML JUnit results to specified directory.
        --html-result <dir>                  output HTML results to specified directory.
     -t,--timeout <timeout>                  set timeout (ms) for waiting. (default: 30000 ms)
        --set-speed <speed>                  same as executing setSpeed(ms) command first.
        --height <height>                    browser height (only phantomjs)
        --width <width>                      browser width (only phantomjs)
     -D,--define <key=value or key+=value>   define parameters for capabilities. (multiple)
        --rollup <file>                      define rollup rule by JavaScript. (multiple)
     -h,--help                               show this message.

Requirements
------------

* Java 6 or later.
* Apache Maven 2.x or later.

Release Note
------------

### 1.4.2

* Catch up Selenium 2.41.0.
* Fix issue #104.

### 1.4.1

* Fix failure on Java8.

### 1.4.0

* Add support "rollup" command and "user-extention-rollup.js". (issue #100)
* Catch up Selenium 2.40.0. (It changed too many internal API, and removed Android driver)
* Remove Andorid driver support because it is removed from Selenium 2.40.
* Re-implement command handling. TOO MANY internal API is changed.
* Update dependency versions.
* Fix issue #99.

### 1.3.6

* Remove default logging command line option for phantomjs from GhostDriver because it depends on user.dir system property.

### 1.3.5

* Fix issue #96.

### 1.3.4

* The option '-D/--define' accepts not only 'key=value' bu 'key+=value'.
* PrintStream object for logging is changed to the instance variable of Runner from static variable.
* Fix issues #92, #93, #94.

### 1.3.3

* Add ${KEY\_\*} variables. (see: http://blog.reallysimplethoughts.com/2013/09/25/using-special-keys-in-selenium-ide-part-2/ )
* Add new option '-D/--define' for setting capabilities of WebDriver.
* Fix issues #87, #90, #91.
* Update Selenium version to 2.39.0.
* Update dependency versions.

### 1.3.2

* Add --set-spped option. It is same as setSpeed(ms) command first.
* Add Appium support. (by yec)
* Fix issues #76, #77, #78, #82, #85.
* Update Selenium version to 2.38.0.

### 1.3.1

* Fix issue #75.

### 1.3.0

* Revive test-suites in test-suites.
* Update HTML result generator for the above feature.

### 1.2.0

* Add HTML result generator.
* Too many internal changes.

### 1.0.0 - 1.1.5

* Sorry, I was not recording changes...

Building the Application
------------------------

* Install Apache Maven.
* clone this repository
* run build script
	`mvn -P package`

That will create the *selenese-runner.jar* file within the 'target' directory.

Rollup
------

"--rollup" option and "rollup" command are used for a definition and execution of a user-defined command.

Refer to the following for how to write "rollup" script:

* Using the rollup feature of Selenium  
http://sanjitmohanty.wordpress.com/2012/07/06/using-the-rollup-feature-of-selenium/
* Selenium Tutorial : Testing Strategies
https://thenewcircle.com/static/bookshelf/selenium_tutorial/testing_strategies.html

However, this feature has the following limitations:

* supported properties of rollup rule:
** name
** args
** expandedCommands or getExpandedCommans
* cannot access any browser object.

License
-------

The Apache License, Version 2.0.

see "LICENSE" file.
