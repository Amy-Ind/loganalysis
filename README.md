The programming task - A Spring Boot API Project
To parse the specific log file, and give the answer to: • The number of unique IP addresses • The top 3 most visited URLs • The top 3 most active IP addresses

I set up the REST APIs and expose 3 endpoints:

api/v1/logs/ip-number
api/v1/logs/top-ips
api/v1/logs/top-urls
The URL is http://localhost:8082/

How to test the 3 APIs
I saved a Bruno collection named programing-task-test-api-bruno-collection under docs/
Download free Bruno from https://www.usebruno.com/downloads
Click "Open Collection" from Bruno, choose docs/programing-task-test-api-bruno-collection and you will see these 3 APIs. Just click the arrow and run the API you will see the response.
In case, the username and password is admin/admin.

Running "java -jar target/loganalysis-0.0.1-SNAPSHOT.jar" in the Terminal to starts this Java application
Run each API on Bruno to test the result Alt text Alt text Alt text Alt text
Thoughts and Technical details
when analyzed the log file, I found the java regex can be used to parse each line.
Consider some unexpected text appear at the end of some lines e.g. "junk extra" "456 789", I skipped these lines which don't match the pattern. You may see some "java.lang.IllegalArgumentException: The line doesn't match the pattern " on the console, this is not issue, just the exception thrown when invalid line in the log file detected.
Restful API
JUnit and Mockito
Getting Started
1. Build and Run
# Using Maven
./mvnw spring-boot:run

# Or build JAR first
./mvnw clean package
java -jar target/loganalysis-0.0.1-SNAPSHOT.jar
The API will be available at http://localhost:8082

Deployment
Docker
docker build -t your-project .
docker run -p 8082:8080 your-project
