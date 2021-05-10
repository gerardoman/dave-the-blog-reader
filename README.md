# Dave, the blog reader
Dave is a Blog Reader and a while ago he read an interesting post with the title “rem alias distinctio quo quis“ and he wants to know who wrote it so he can read more posts from the writer.
In this [URL], Dave found all posts of the platform.

### User story: Filter Posts
As a user, I want to help Dave finding the person who wrote the blog post “rem alias distincto quo quis“ and then list all posts from that writer so Dave can read them. The best approach would be to do some REST API requests to filter the information Dave wants. In order to validate your code will work correctly, which test cases would you add to your solution to make it more robust? In this [URL], you can find the json with all platform posts of the platform. You can also find the relevant API documentation you will need [here].

### Features

- Up Docker image containing Jenkins
- Configure Jenkins with a [jenkinsfile]
- Import Postman [collections] and [environment] to the pipeline
- Run tests with Newman
- Publish [HTML reports] with test results
- Import [.JMX file] to the pipeline
- Run tests with JMeter
- Publish [CSV report] with test results

## Installation

"Dave, the blog reader" requires [Node.js](https://nodejs.org/) and [Docker](https://www.docker.com/) to run.

1) Go to the directory where [docker-compose file] is located and then run the following commands:
```sh
docker-compose build
docker-compose up -d
```

2) Get generated admin password to login in Jenkins:
```sh
docker exec jenkins cat /var/jenkins_home/secrets/initialAdminPassword
```

3) Create a Pipeline (new item) with following configs:
![alt text](https://raw.githubusercontent.com/gerardoman/dave-the-blog-reader/main/readme/Jenkins1.png)
![alt text](https://raw.githubusercontent.com/gerardoman/dave-the-blog-reader/main/readme/Jenkins2.png)
![alt text](https://raw.githubusercontent.com/gerardoman/dave-the-blog-reader/main/readme/Jenkins3.png)

4) Install the following plugins:
- GitHub Integration Plugin;
- HTML Publisher plugin;
- NodeJS Plugin;
- Performance Plugin.

5) Run the following command in Jenkins script console:
```sh
System.setProperty( "hudson.model.DirectoryBrowserSupport.CSP" , "" )
```

6) You can now build your pipeline!

## Expected Results

1) Jenkins Interface Results (example)
![alt text](https://raw.githubusercontent.com/gerardoman/dave-the-blog-reader/main/readme/Interface1.png)
![alt text](https://raw.githubusercontent.com/gerardoman/dave-the-blog-reader/main/readme/Interface2.png)

2) Newman Results (example)
![alt text](https://raw.githubusercontent.com/gerardoman/dave-the-blog-reader/main/readme/Newman1.png)
![alt text](https://raw.githubusercontent.com/gerardoman/dave-the-blog-reader/main/readme/Newman2.png)

3) JMeter Results (example)
![alt text](https://raw.githubusercontent.com/gerardoman/dave-the-blog-reader/main/readme/Jmeter1.png)
![alt text](https://raw.githubusercontent.com/gerardoman/dave-the-blog-reader/main/readme/Jmeter2.png)

[//]: # (These are reference links used in the body of this note and get stripped out when the markdown processor does its job. There is no need to format nicely because it shouldn't be seen. Thanks SO - http://stackoverflow.com/questions/4823468/store-comments-in-markdown-syntax)

   [URL]: <https://jsonplaceholder.typicode.com/posts>
   [here]: <https://jsonplaceholder.typicode.com/>
   [jenkinsfile]: <https://github.com/gerardoman/dave-the-blog-reader/blob/main/Jenkinsfile>
   [collections]: <https://github.com/gerardoman/dave-the-blog-reader/tree/main/collections>
   [environment]: <https://github.com/gerardoman/dave-the-blog-reader/tree/main/environment>
   [HTML reports]: <https://github.com/gerardoman/dave-the-blog-reader/tree/main/htmlreports>
   [.JMX file]: <https://github.com/gerardoman/dave-the-blog-reader/blob/main/jmeter/extras/jenkins.jmx>
   [CSV report]: <https://github.com/gerardoman/dave-the-blog-reader/blob/main/csvreport/results.csv>
   [docker-compose file]: <https://github.com/gerardoman/dave-the-blog-reader/blob/main/docker-compose.yml>
