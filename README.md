# Run Selenium Tests With Jasmine for BDD — TestMu AI (Formerly LambdaTest)

![JavaScript](https://user-images.githubusercontent.com/95698164/172134732-2e9c780e-10ac-4956-b366-86ffc25bf070.png)

<p align="center">
  <a href="https://www.testmuai.com/blog/?utm_source=github&utm_medium=repo&utm_campaign=karma-jasmine-sample" target="_bank">Blog</a>
  &nbsp; &#8901; &nbsp;
  <a href="https://www.testmuai.com/support/docs/?utm_source=github&utm_medium=repo&utm_campaign=karma-jasmine-sample" target="_bank">Docs</a>
  &nbsp; &#8901; &nbsp;
  <a href="https://www.testmuai.com/learning-hub/?utm_source=github&utm_medium=repo&utm_campaign=karma-jasmine-sample" target="_bank">Learning Hub</a>
  &nbsp; &#8901; &nbsp;
  <a href="https://www.testmuai.com/newsletter/?utm_source=github&utm_medium=repo&utm_campaign=karma-jasmine-sample" target="_bank">Newsletter</a>
  &nbsp; &#8901; &nbsp;
  <a href="https://www.testmuai.com/certifications/?utm_source=github&utm_medium=repo&utm_campaign=karma-jasmine-sample" target="_bank">Certifications</a>
  &nbsp; &#8901; &nbsp;
  <a href="https://www.youtube.com/@TestMuAI" target="_bank">YouTube</a>
</p>
&emsp;
&emsp;
&emsp;

*Learn how to use Jasmine for BDD framework to configure and run your JavaScript automation testing scripts on the TestMu AI platform*

[<img height="58" width="200" src="https://user-images.githubusercontent.com/70570645/171866795-52c11b49-0728-4229-b073-4b704209ddde.png">](https://accounts.lambdatest.com/register)

## Table Of Contents

* [Pre-requisites](#pre-requisites)
* [Run Your First Test](#run-your-first-test)
* [Avoid Timeouts With psuedoActivityInternal](#avoid-timeouts-with-psuedoactivityinternal)
* [Testing Locally Hosted or Privately Hosted Projects](#testing-locally-hosted-or-privately-hosted-projects)

## Pre-requisites 

In order to perform your karma tests with TestMu AI, you would need the below things to be already set up:

#### 1. Global Dependencies

* Make sure to use the latest version of JavaScript.
* A [Git or GitHub repository](https://github.com/)
* Download and [install node.js](https://nodejs.org/en/) and node package manager or npm.
* To install node.js with homebrew use the below command.

`$ brew install node`

* If you have npm already installed, you may want to upgrade it to latest version. Here the code you can run in your terminal to upgrade npm.

`npm install npm@latest -g`

#### 2. TestMu AI Authentication Credentials

Be aware of your TestMu AI authentication credentials i.e. your TestMu AI username, access key and HubURL. You need to set them up as your environment variables. You can retrieve them from your [TestMu AI automation dashboard](https://automation.lambdatest.com/?utm_source=github&utm_medium=repo&utm_campaign=karma-jasmine-sample) by clicking on the key icon near the help button.

* **For Linux/Mac:**
```bash
$ export LT_USERNAME=<YOUR_LAMBDATEST_USERNAME> 
$ export LT_ACCESS_KEY=<YOUR_LAMBDATEST_ACCESS_KEY>
```

* **For Windows:**
```bash
$ set LT_ACCESS_KEY=<YOUR_LAMBDATEST_ACCESS_KEY>
$ set LT_ACCESS_KEY=<YOUR_LAMBDATEST_ACCESS_KEY>
```

### Setting Up The Environment For Jasmine Testing Using Selenium

You need to clone our [GitHub repository](https://github.com/LambdaTest/protractor-selenium-sample) which demonstrates a [sample of Karma-Jasmine](https://github.com/LambdaTest/karma-jasmine-sample).

After cloning, you need to navigate to the cloned directory and install project dependencies using the below command:

`$ npm install`

The example mentioned below would help you to perform Jasmine testing in Google Chrome.

``` js
describe('add', function () {
    it('should add two numbers and return the result', function () {
        expect(window.add(1, 2)).toBe(3);
    });
});
 
describe('subtract', function () {
    it('should subtract two numbers', function () {
        expect(window.subtract(2, 1)).toBe(1);
    });
});
 
describe('updateAppState', function () {
    it('should push a new state into the browser history', function () {
        window.updateAppState({
            message: 'Getting Started with LambdaTest'
        });
        expect(window.history.state).toEqual({
            message: 'Getting Started with LambdaTest'
        })
    });
});
```

## Testing Locally Hosted or Privately Hosted Projects

To help you perform cross browser testing of your locally stored web pages, TestMu AI provides an SSH(Secure Shell) tunnel connection with the name TestMu AI tunnel. With TestMu AI tunnel, you can run your Jasmine tests using Karma to perform automated cross browser testing on browsers offered by online Selenium Grid at LambdaTest. So you make sure how well your changes look, even before your customers. Curious to know more about TestMu AI tunnel?

> Follow our documentation on TestMu AI tunnel to know it all. OS specific instructions to download and setup tunnel binary can be found at the following links.
 * [Documentation For Windows User](/docs/local-testing-for-windows/)
 * [Documentation For Mac User](/docs/local-testing-for-macos/)
 * [Documentation For Linux User](/docs/local-testing-for-linux/)

> Download the binary file of:
 * [TestMu AI tunnel for Windows](https://downloads.lambdatest.com/tunnel/v3/windows/64bit/LT_Windows.zip)
 * [TestMu AI tunnel for Mac](https://downloads.lambdatest.com/tunnel/v3/mac/64bit/LT_Mac.zip)
 * [TestMu AI tunnel for Linux](https://downloads.lambdatest.com/tunnel/v3/linux/64bit/LT_Linux.zip)

Once, the tunnel is successfully set up. You can add the below code to your capabilities for testing internal servers on your network.

``` js
//Test Websites Using Localhost
customLaunchers: { chrome: {
        tunnel: true, // In case karma is running on local machine
    }   }
```
> **Important Note**: Some Safari & IE browsers don’t support automatic resolution of the URL string “localhost”. Therefore if you test on URLs like "`http://localhost/`" or "`http://localhost:8080`" etc, you would get an error in these browsers. A possible solution is to use "`localhost.lambdatest.com`" or replace the string “localhost” with machine IP address. For example, if you wanted to test "`http://localhost/dashboard`" or, and your machine IP is 192.168.2.6 you can instead test on "`http://192.168.2.6/dashboard`" or "`http://localhost.lambdatest.com/dashboard`".

## Run Your First Test

Navigate to the directory where you cloned the [sample of Karma-Jasmine](https://github.com/LambdaTest/karma-jasmine-sample) and run the following command.

`$ karma start karma.conf.js`

or you could also run the test using:

`$ npm test`

### Browser Launcher Configuration

If you look at ***karma.conf.js*** file you will find that we are passing browser, browser version, and operating system information, along with TestMu AI [Selenium grid](https://www.testmuai.com/blog/why-selenium-grid-is-ideal-for-automated-browser-testing/) capabilities via capabilities object. The capabilities object in the above code is defined as:

``` js
customLaunchers: {
        chrome: {
             base: 'WebDriver',
             config: webdriverConfig,
             browserName: 'chrome',
             platform: 'windows 10',
             version: '71.0',
             name: 'Karma With Heartbeat',
             user: process.env.LT_USERNAME,
             accessKey: process.env.LT_ACCESS_KEY,
             pseudoActivityInterval: 15000 // 15000 ms heartbeat to avoid timeouts
        }
    }
```

The most important capabilities to understand here are ‘browserName’, ‘version’, and ‘platform’. They define which browser environment you wish to run the test on. Rest of the capabilities are important in test management and debugging. We have an inbuilt [Capabilities Generator](https://www.testmuai.com/capabilities-generator/?utm_source=github&utm_medium=repo&utm_campaign=karma-jasmine-sample) tool as well that you use to generate capabilities code for your test suite.

## Avoid Timeouts With psuedoActivityInternal

To make sure our machines are not hold for long due to some incorrect test, we have come up with a restriction on the number of seconds that our machine is kept reserved for you. In cases, where our servers fail to retrieve a request from your local machine for more than 90 seconds, then your tests are aborted from the queue with the error message related to Timeouts.

If you wish to avoid such timeouts, you need to make use of the below parameter:
``` js
customLaunchers: { chrome: {
 pseudoActivityInterval: 5000 // 5000 ms heartbeat to avoid timeouts
 } }
```

> **Note**: psuedoActivityInternal is presented as a default parameter with a value set to 0. Make sure to provide a value more than 0 in order to avoid the timeouts.


## Documentation & Resources :books:
 
Visit the following links to learn more about TestMu AI's features, setup and tutorials around test automation, mobile app testing, responsive testing, and manual testing.

* [TestMu AI Documentation](https://www.testmuai.com/support/docs/?utm_source=github&utm_medium=repo&utm_campaign=karma-jasmine-sample)
* [TestMu AI Blog](https://www.testmuai.com/blog/?utm_source=github&utm_medium=repo&utm_campaign=karma-jasmine-sample)
* [TestMu AI Learning Hub](https://www.testmuai.com/learning-hub/?utm_source=github&utm_medium=repo&utm_campaign=karma-jasmine-sample)    

## TestMu AI Community :busts_in_silhouette:

The [TestMu AI Community](https://community.testmuai.com/?utm_source=github&utm_medium=repo&utm_campaign=karma-jasmine-sample) allows people to interact with tech enthusiasts. Connect, ask questions, and learn from tech-savvy people. Discuss best practises in web development, testing, and DevOps with professionals from across the globe 🌎

## What's New At TestMu AI ❓

To stay updated with the latest features and product add-ons, visit [Changelog](https://changelog.lambdatest.com/)

## 🚀 LambdaTest is Now TestMu AI

👋 Welcome to TestMu AI, the next evolution of LambdaTest. As of January 2026, [LambdaTest is Now TestMu AI](https://www.testmuai.com/lambdatest-is-now-testmuai/) - we have evolved from a cross-browser testing cloud into a unified, AI-native quality engineering platform designed for the modern DevOps era.

Whether you have been part of the LambdaTest community for years or are just discovering TestMu AI, our mission remains the same: to help you ship faster with high-scale test execution, autonomous testing, and deep quality analytics.

### 🔄 Our Rebrand Journey

In 2017, we introduced LambdaTest with a clear mission: to become the world's most trusted cloud testing platform. We built a scalable, high-performance test cloud that eliminated flakiness, improved developer feedback cycles, and accelerated release velocity for teams worldwide.

As LambdaTest grew, we expanded the platform into Test Intelligence, Visual Regression Testing, Accessibility Testing, API Testing, and Performance Testing, covering the entire testing lifecycle. These capabilities enabled teams to test any stack, on any technology, at enterprise scale.

Over time, we rebuilt the architecture to be AI-native from the ground up. What began as LambdaTest's high-performance testing cloud has now evolved into TestMu AI, an AI-native, multi-agent platform redefining modern quality engineering.

We chose the name TestMu AI to reflect our shift towards intelligent, autonomous testing. While our identity has changed, our core technology and commitment to the testing community stay the same.

👉 Find [LambdaTest's New Home](https://www.testmuai.com/).

### 🔭 Explore TestMu AI

The same infrastructure LambdaTest customers relied on, now delivered through autonomous AI agents.

- [KaneAI](https://www.testmuai.com/kane-ai/)
- [Agent-to-Agent Testing](https://www.testmuai.com/agent-to-agent-testing/)
- [HyperExecute](https://www.testmuai.com/hyperexecute/)
- [Real Device Cloud](https://www.testmuai.com/real-device-cloud/)
- [Pricing](https://www.testmuai.com/pricing/)
- [Documentation](https://www.testmuai.com/support/docs/)