# SonarQubeDemo
## Execute sonar from local

Running a SonarQube analysis with Maven is straighforward. You just need to run the following command in your project's folder.

```
mvn sonar:sonar \
  -Dsonar.host.url=http://localhost:9000 \
  -Dsonar.login=Key
```
## Execute using jenkins pipeline
```
stage('Sonar scan') {
            steps {
                sh 'mvn sonar:sonar' 
            }
        }
```
## Jacoco integration with Sonar
JaCoCo is a free code coverage library for Java , we need to include Jacoco plug-in in pom.xml
after that we need to run jacoco and sonar.
```
stage('JaCoCo') {
            steps {
                echo 'Code Coverage'
                sh 'mvn jacoco:report'
            }
        }
```
## What Is a Quality Gate?

A Quality Gate is a set of conditions the project must meet before it can qualify for production release. 

<img width="1346" alt="Screen Shot 2021-09-15 at 10 03 36 PM" src="https://user-images.githubusercontent.com/87215340/133552629-4c3f4135-6b98-457d-a34c-73bd7a85588d.png">

## Sonar report
<img width="939" alt="Screen Shot 2021-09-15 at 10 05 08 PM" src="https://user-images.githubusercontent.com/87215340/133552747-dd55d106-c959-45d0-8bc9-64287615aba6.png">

