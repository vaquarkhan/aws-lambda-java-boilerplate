# AWS Lambda Boilerplate for JAVA and Spring IoC

- https://github.com/vaquarkhan/aws-log-level
- https://github.com/aws/aws-lambda-java-libs/tree/master/aws-lambda-java-log4j2
- https://github.com/aws/aws-lambda-java-libs

Do you miss JAVA, its great features and all Spring framework sugar in AWS Lambda? Use this boilerplate code to author JAVA functions in Lambda and enjoy all features of Spring IoC. It also supports local debugging of JAVA functions.

## Usage

The code is already documented. **MainHandler** is the main entrance point of your lambda function. **services** package includes Spring Beans. For default, MainHandler fetches **Service** Bean from IoC container but once you have Service instance you can use Autowiring features.
 
### Local running

In root folder fire
 
```
mvn compile exec:java
```

You can configure your IDE to run com.example.lambda.local.LocalRunner as Main Class and com.cagataygurturk.lambda.MainHandler as program argument to debug locally your function.

### Deployment

In root folder fire

```
mvn package -Denv=production
```

This creates a JAR package in target folder. 

As you can see in `pom.xml`, "-Denv=production" activates production profile and it excludes `aws-lambda-local-runner` dependency from deployment package in order to get rid of a unnecessary dependency which is not needed in production environment. Forgetting this does not affect the project but it increases JAR package size.

You can upload the created JAR folder to AWS Lambda console. Handler function should be configured to `com.cagataygurturk.example.lambda.MainHandler`.
 
## More about the topic

- Check out [Lambada Framework](https://github.com/lambadaframework/lambadaframework) for seamless AWS Lambda and JAVA integration.


- https://stackoverflow.com/questions/51651507/is-it-possible-to-change-the-log-level-of-an-aws-lambda-at-runtime
- https://frank-afriat.medium.com/solving-the-java-aws-lambda-logging-problem-305b06df457f
- https://kathirmunai.com/logging-in-aws-lambda-with-slf4j?__cf_chl_jschl_tk__=pmd_189c3b9c98b86495a7339ed202e8d56645c66127-1627313760-0-gqNtZGzNAfijcnBszQdO
