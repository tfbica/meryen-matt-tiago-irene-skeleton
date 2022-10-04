[![Java CI with Maven](https://github.com/Academy-Sept-22/meryen-matt-tiago-irene-scheleton/actions/workflows/maven.yml/badge.svg?branch=main)](https://github.com/Academy-Sept-22/meryen-matt-tiago-irene-scheleton/actions/workflows/maven.yml)


# Application
- <code>HelloWorld</code>
  - Uses Spark framework
  - Gets Heroku PORT from environment to set Spark WebServer port
  - Serves a page at https://[server]/hello

# Test
- <code>EmptyTest</code>
  - Dummy test asserting 1=1 (always passes)

# Maven Build
- Builds a jar with all the dependencies
  - uses maven-assembly-plugin
  - on the <code>package</code> command

# CI/CD using GitHub Actions
- Created a repository secret <code>secrets.HEROKUAPIKEY</code> to use
- <code>.github/workflows/maven.yml</code>
  - Checkout the project using actions/checkout@v3
  - Setups JDK 17
  - Build and test running <code>mvn package</code>
  - Publish test report using scacap/action-surefire-report@v1
  - Deploy to Heroku (Irene's account) using akhileshns/heroku-deploy@v3.12.12
    - use <code>secrets.HEROKUAPIKEY</code>

# Run on Heroku
 - Heroku's configurations to run the application:
   - system.properties
     - define JDK 17
   - Procfile
     - tells Heroku how to run <br> 
        <code>web: java -cp ./target/walking-scheleton-1-jar-with-dependencies.jar HelloWorld</code>
   