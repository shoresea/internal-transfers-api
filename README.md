# internal-transfers-api

A REST API for money transfers between accounts.

## Built With

* [Kotlin](https://kotlinlang.org/)
* [Ktor](https://ktor.io/) - Web Framework
* [Gradle](https://gradle.org/) - Build Tool

### Other libraries used

* [JaCoCo](https://www.jacoco.org/) - code coverage
* [hibernate-validator](https://github.com/hibernate/hibernate-validator) - request validation
* [JUnit5](https://junit.org/junit5/) - testing
* [kotlinx-coroutines-core](https://kotlin.github.io/kotlinx.coroutines/kotlinx-coroutines-core/) - validating/testing concurrency
* [mockito](https://site.mockito.org/) - mocking in tests
* [assertJ](https://github.com/joel-costigliola/assertj-core) - assertions in tests
* [gson](https://github.com/google/gson) - json parser for tests


## Running on local

### Building

Run the below command on terminal to build the jar:

```console
./gradlew clean build
```
A fat-jar will be created in location `./build/libs/internal-transfers-api-1.0.0-all.jar`

### Running
Once you have built the jar using above step, you can start the application by below command:

```console
java -jar ./build/libs/internal-transfers-api-1.0.0-all.jar
```

### Testing and Reports

Run the below command on terminal to test the application and generate a test report and a JaCoCo code coverage report:

```console
./gradlew clean test
```
Test reports can be found at `./build/reports/tests/test/index.html`

Code Coverage reports can be found at `./build/reports/jacoco/test/html/index.html`


## Available Endpoints
This api doesn't have a Swagger/OpenAPI integration because of the lack of an official/cleaner OpenAPI support for Ktor Framework. 
Thus the available endpoints information has been added here.

### Account Endpoints
1) GET `localhost:8090/accounts` - Returns all the accounts available.
(For the ease of testability, I have created 10 random accounts already)
#### Sample Response
```json
[
    {
        "id": "833fb7f0-9549-4dbd-b570-2d9e4be2b0ef",
        "balance": 605.43
    },
    {
        "id": "89861c9e-5ca8-4814-a5c0-a284ea23d9e3",
        "balance": 86.84
    }
]
```
2) POST `localhost:8090/accounts` - Creates an account.
#### Sample Request
```json
{
    "balance": "123"
}
```
#### Sample Response
```json
{
    "id": "3c8754aa-6fbe-4b72-ad08-dcbf29501ea3",
    "balance": 123
}
```

### Internal Transfer Endpoints
1) POST `localhost:8090/internal/transfer/` - Transfers Money from one account to another
#### Sample Request
```json
{
    "senderAccountId": "833fb7f0-9549-4dbd-b570-2d9e4be2b0ef",
    "receiverAccountId": "3c8754aa-6fbe-4b72-ad08-dcbf29501ea3",
    "amount": 12
}
```
#### Sample Response
No json response for this endpoint, just HTTP status is returned.