PRODUCTION ENVIRONMENT

**Q:  Help!  Something broke in production!**  
Did you check it with ``--debug``?  There is a minification library that will parse your CSS and Javascript.  Check that it hasn't mangled your application by running your app with --debug.

**Q:  How do I deploy to Heroku?**  
Sadly, just don't.  Prior to 0.6.0, lots of people were using the Oortcloud Heroku Buildpack with much success.  As of 0.6.0, it seems to have broken, however.  And it's a moot point, because Heroku doesn't support Sticky Sessions, and won't scale up or support fail-over configurations.  Instead, use Meteor.com, CloudBees, or Modulus.io.  
https://github.com/oortcloud/heroku-buildpack-meteorite

**Q:  Are there any cloud hosting providers that provide unit testing?**  
CloudBees provides a Meteor clickstart, software-as-a-service, unit testing, and continuous integration.  It's a bit klunky, but if you're worried about continuous integration, it's the one to choose:  
https://github.com/CloudBees-community/meteor-clickstart  

**Q:  How do I monitor CPU utilization, memory utilization, etc?**  
See this discussion.  
https://groups.google.com/forum/#!topic/meteor-talk/91hcC87ch5k  




------------------------------------------------------------------
**Q:  Is there any documentation on the Meteor.settings?**    
So far, the following setting parameters have been seen in the wild:  

````
Meteor.settings.privateKey == "MY_KEY"  
Meteor.settings.public.publicKey == "MY_PUBLIC_KEY"   
Meteor.settings.public.anotherPublicKey == "MORE_KEY"  
````


**Q:  What's the best practice for using content distribution networks (CDN)?**  
Currently, there's not anything specific, other than putting static content on your CDN, and creating links to it from your app.  You may want to run the meteor bundle command, and take a peek in the resulting tar.gz file.
````
meteor bundle
````

Also, follow the feature card on the Meteor roadmap:  
https://trello.com/card/speed-up-improve-app-loading/508721606e02bb9d570016ae/47


**Q: How do I run the node.js app that Meteor produces as a service?**  
http://kvz.io/blog/2009/12/15/run-nodejs-as-a-service-on-ubuntu-karmic/  
