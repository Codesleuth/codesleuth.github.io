---
layout: stackedit
title: Continuous Delivery as a Service
date: 2014-11-03
permalink: /talks/Continuous-Delivery-as-a-Service.html
redirect_from:
  - /talks/2014/11/Continuous-Delivery-as-a-Service.html
---

# Continuous Delivery as a Service
{:.no_toc}
*Presented at [Tech Nottingham, 3rd November 2014](http://www.technottingham.com/events/2014/11/03/tech-nottingham-november-2014-continuous-delivery-as-a-service "Continuous Delivery as a Service") and [DotNetSheff, 2nd June 2015](https://dotnetsheff.co.uk/)*

**Continuous Integration** helps teams deliver higher quality code and give them more confidence in features and changes, allowing them to deploy more often and with less surprises.
Using **Continuous Delivery**, your team can empower the delivery pipeline to automatically deploy a successful build, in order to gain valuable user feedback sooner.

## Table of Contents
{:.no_toc}
* Table of Contents
{:toc}

## The Task
Imagine you are an aspiring startup company with a great idea. You decide that using Continuous Integration and Continuous Delivery will help the company save time by building, maintaining and delivering the project more frequently. Great! Let's get started!

### 1. Create a project
Start a new project that does *anything* you like, such as a "Hello World" web app, a tool which prints out [lorem ipsum](http://slipsum.com "Samuel L. Ipsum"), a [Jekyll blog site](https://pages.github.com "GitHub pages with Jekyll"), or a service to send a reminder of your partner's upcoming Birthday [via SMS](http://developers.esendex.com/APIs/REST-API/messagedispatcher "Esendex Message Dispatcher") (super useful). It doesn't matter what it does, but it **must have tests** at this stage to demonstrate the use of Continuous Integration. You don't need to make it fancy - `Assert.Pass()` is fine for now!
See below for example test frameworks for different languages and platforms:

* .NET: [NUnit](http://www.nunit.org "NUnit")
* Java: [JUnit](http://junit.org "JUnit")
* Node.js: [Mocha](http://mochajs.org "Mocha")
* Ruby: [RSpec](https://github.com/rspec/rspec-core "RSpec Core @ GitHub")
* Python: [unittest](https://docs.python.org/2/library/unittest.html "unittest, The Python Standard Library")
* Go: [testing package](http://golang.org/pkg/testing/ "The Go testing standard package")
* Haskell: [HSpec](http://hspec.github.io/ "HSpec")
* PHP: [PHPUnit](https://phpunit.de/ "PHPUnit")

### 2. Push to a repository
Set up a place for the code to live. Some of the most popular choices are **[GitHub](https://github.com)**  or **[BitBucket](https://bitbucket.org)**. It's better to leave the code *public* for now, since most services will offer free builds if the repository is open source.
Push your source code so it's available, and get ready to begin continuously integrating!

```bash
$ git add -A
$ git commit -m 'First commit!'
$ git push origin master
```

### 3. Set up continuous integration
If you don't already have an account on a CI service, go create one! Set up your project to build using the service, and ideally set it up to build upon every code change. You may need to make sure your choice of service can support the language you have used for your project.
The following services offer free accounts and should help you get started right away:

* [AppVeryor](http://www.appveyor.com "AppVeyor") (allows .NET)
* [Microsoft Azure](http://azure.microsoft.com "Azure") (allows .NET)
* [Visual Studio Online](http://www.visualstudio.com/en-us/get-started/connect-to-vs.aspx "Visual Studio Online") (allows .NET)
* [Codeship](https://codeship.io "Codeship")
* [Travis-CI](https://travis-ci.org "Travis-CI")
* [Semaphore](https://semaphoreapp.com "Semaphore")
* [Buildbox](https://buildbox.io "Buildbox")
* [CircleCI](https://circleci.com "CircleCI")

### 4. Push a code change, watch it build
At this point you should have a public repository, code, tests, and a service to build it. Now all you need to do is start a build and watch it go! So, make a change to your code (perhaps add another test?) then push the changes. Does it build?

### 5. Choose a deployment location
Now that you have a clean build and all the tests pass, let's get it deployed so we can get user feedback as soon as possible. Deploy your application manually to get it set up to a hosting provider.
Choose a host for your project; here's a list of some you may like to try:

* [Azure Websites](http://azure.microsoft.com/en-us/services/websites/ "Azure Websites and Apps")
* [AWS Elastic Beanstalk](http://aws.amazon.com/elasticbeanstalk "AWS Elastic Beanstalk")
* [Heroku](https://www.heroku.com "Heroku")
* [OpenShift](https://www.openshift.com "OpenShift by Red Hat")
* [Google Cloud](https://cloud.google.com "Google Cloud")
* [nodejitsu](https://www.nodejitsu.com "nodejitsu Node.js hosting")

### 6. Automate the deployment
Return to your chosen CI or CD service and set up a deployment step to deploy to your chosen hosting service. Does the CD service support your chosen host? If not, don't worry, it's likely it can be scripted to deploy, you'll just have to figure out how. If your chosen host is already supported, great! Wire it up and push another build; watch it build, test ***and*** deploy!

## Next Steps
Now that you have everything set up, it's a good idea to have a think about what can cause your deployment to fail. Do you need more tests? How about running tests ***after*** deployment to verify the deploy succeeded? Do you need any manual test steps?

Continuous Integration and Delivery are the responsibility of everybody in your team. Anybody should be able to integrate their changes to **master** or **trunk**, push the change, and watch it build and deploy. How can you ensure you have the confidence to allow this? What coverage are you missing?

## In Practice
Not all code changes are ready for release. You may have to verify the change can withstand extreme load, or ensure it meets a visual comparison check; it's likely you'll need to insert an extra step somewhere to handle these situations. However, for those lucky enough to be able to gain confidence with automated tests, you can start to practice CI and CD immediately, so have a look where you can use it and take the first step!

## References and Further Reading

* Jez Humble: [Continuous Delivery](http://continuousdelivery.com/)
* Jez Humble and David Farley (2010) *[Continuous Delivery](http://www.amazon.co.uk/dp/0321601912), Addison Wesley*
* ThoughtWorks: [Continuous Integration](http://www.thoughtworks.com/continuous-integration) and [Continuous Delivery](http://www.thoughtworks.com/continuous-delivery)
* Wikipedia: [Continuous Integration](http://www.thoughtworks.com/continuous-delivery) and [Continuous Delivery](http://en.wikipedia.org/wiki/Continuous_delivery)
* Martin Fowler: [Continuous Integration](http://www.martinfowler.com/articles/continuousIntegration.html) and [Continuous Delivery](http://martinfowler.com/bliki/ContinuousDelivery.html)

> Written with [StackEdit](https://stackedit.io/).

*[CI]: Continuous Integration
*[CD]: Continuous Delivery