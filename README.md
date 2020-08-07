## Web Annotation Rest API

WebAnnotationAPI application is annotation builder module for any web application. It is designed as a separate application server. It consist of two different parts. One of them is a rest service api which is a Spring Boot Application that uses Mongo DB as data storage solution. This module provides opportunity to save annotations based on W3C standards on db and search. 

Second part is the javascript and html side of the module which integrates the annotation sidebar, save and update annotation, search annotation operations to any page. Custom sidebar is designed to show all the annotations in the current page. In javascript side, annotation-model.js library is used. This library helps to create proper json-ld for various types of annotations in annotating text data. While annotating image data we have changed this library and add some new features to manage image annotations properly, as well. Additionally, Bootstrap, Jcrop, Jquery js libraries is used in the front end side of annotation operations.
Application Specification

- {github_repository}/WebAnnotationAPI
- Back-end application is Spring Boot Rest API service.
- Rest Service endpoints are located under package com.mystream.controller
- Rest Service request and response types are located under package com.mystream.param - Domain objects for MongoDb are located under package com.mystream.dom
- Repositories are located under package com.mystream.repo
- Services are located under package com.mystream.service
- Unit tests are located under package com.mystream.test - Dependencies for used repositories is stored in pom.xml

#### Database

MongoDb is used in project. Atlas cloud system is used to store database.

Atlas account username : ************************ Atlas account password : **************************
 
Atlas cloud : https://cloud.mongodb.com/user#/atlas/login

#### Implementation Details 

***Technology Scope***
 
*Frameworks and Libraries used in project :*

*Frameworks :*
 
Spring Boot Framework : https://spring.io/projects/spring-boot

*Javascript Libraries*

Annotation Modal Jquery

Jcrop
: https://www.postgresql.org : https://www.mongodb.com/
: https://github.com/goodmansasha/annotation-model : https://code.jquery.com
: https://jcrop.com/
  
*Css:*

Bootstrap : https://getbootstrap.com/

*Repository*

*DeployedServerInformation*

Annotation Server Production Environment
https://mystream-anno.herokuapp.com/helloAnnotation

#### User Manual

In order to create community, the following information will be entered to the modal.
Github Repository : https://github.com/mateskarayol/WebAnnotationAPI

***Running Up WebAnnotationAPI***

In order to run front-end on local environment follow the steps below :

1. Open terminal
2. Run “git clone  https://github.com/mateskarayol/WebAnnotationAPI”
3. Open IntelliJ or any preferred IDE
4. Open project .../WebAnnotationAPI
5. Build project
6. Run “mvn clean install”
7. Start
8. Open “https://mystream-anno.herokuapp.com/searchAnnotation?source=*” on browser.
 
***Deployment of WebAnnotationAPI***

1. First download Heroku command line interface from internet
2. Open terminal
3. Go to folder .../WebAnnotationAPI
4. Run “heroku login”
5. Run “heroku git:remote -a mystream-anno”
6. Run “mvn clean package”
7. Run “heroku buildpacks:set heroku/jvm”
8. Run “heroku deploy:jar target/anno-0.0.1-SNAPSHOT.jar --app mystream-annoj”
9. Run “heroku open”
10. Run “heroku logs”


### Annotation Server Unit Tests

The tests below asserts that repository save various types of annotations properly. For each case, relevant json file is used and relevant annotation type is saved then required assertions are done. Then saved annotation is deleted to make the test cases sustainable and not to increase data size. All tests are
runned via mvn clean package commands before deployment. So, the functionality of the repository and service is checked before production.

Repository Tests :

test_save_imageTarget test_save_textTarget test_save_bodyWithVideo test_save_bodyWithImage test_save_bodyWithText 

test_findByTarget_SourceLike

Service Tests : 

test_saveAnnotation_imageTarget

test_saveAnnotation_textTarget test_saveAnnotation_bodyWithVideo test_saveAnnotation_bodyWithImage

test_saveAnnotation_bodyWithText test_searchAnnotationWithSource

Relevant test json-ld structures are located as mystream/MyAnnotation/src/test/resources/*.json inroject.
