# Fintan Swagger Client

fintan-swagger-client
- API version: 1.0.0
  - Build date: 2022-02-03T01:18:13.970Z


Baseline client for integrating external [Swagger](https://swagger.io/)/OpenAPI-based services into Fintan. Based on an [experiment](https://github.com/acoli-repo/powla/tree/main/experimental/salt/swagger/java-client) for wrapping [Pepper](https://corpus-tools.org/pepper) in a dockerized service for converting resources to [POWLA](https://github.com/acoli-repo/powla) and [CoNLL-RDF](https://github.com/acoli-repo/conll-rdf) for use within [Fintan](https://github.com/Pret-a-LLOD/Fintan).

TODO: update to openapi: 3.0.0, also cf. https://swagger.io/docs/specification/2-0/file-upload/


*Most code has been automatically generated by the [Swagger Codegen](https://github.com/swagger-api/swagger-codegen)*


## Requirements

Building the API client library requires:
1. Java 1.8+
2. Maven

## Installation

To install the API client library to your local Maven repository, simply execute:

```shell
mvn clean install
```

### Use in Maven projects

Add this dependency to your project's POM:

```xml
<dependency>
	<groupId>org.acoli.fintan</groupId>
	<artifactId>fintan-swagger-client</artifactId>
	<version>1.0.0</version>
	<scope>compile</scope>
</dependency>
```

### Use as native Java lib

At first generate the JAR by executing:

```shell
mvn clean package
```

Then manually install the following JARs:

* `target/swagger-java-client-1.0.0.jar`
* `target/lib/*.jar`

### Multithreading Recommendation

It's recommended to create an instance of `ApiClient` per thread in a multithreaded environment to avoid any potential issues.



## Using OpenAPI/Swagger services in Fintan

This repository is referenced by the [fintan-backend](https://github.com/acoli-repo/fintan-backend) for general purpose service integration.

For a complete documentation, please refer to the [Fintan Documentation](https://github.com/acoli-repo/fintan-doc).



## Using the Pepper CorpusAPI as an example

Please follow the [installation](#installation) instruction and execute the following Java code:

```java

import io.swagger.client.*;
import io.swagger.client.auth.*;
import io.swagger.client.model.*;
import io.swagger.client.api.CorpusApi;

import java.io.File;
import java.util.*;

public class CorpusApiExample {

    public static void main(String[] args) {
        
        CorpusApi apiInstance = new CorpusApi();
        String id = "id_example"; // String | resource/data ID
        String importer = "importer_example"; // String | PepperImporter
        String format = "format_example"; // String | target format, one of CoNLL-RDF, CoNLL or POWLA
        String blob = "blob_example"; // String | Data to be processed
        try {
            Response result = apiInstance.addData(id, importer, format, blob);
            System.out.println(result);
        } catch (ApiException e) {
            System.err.println("Exception when calling CorpusApi#addData");
            e.printStackTrace();
        }
    }
}

```

### Documentation for Pepper CorpusAPI Endpoints

Pointer to [service](https://github.com/acoli-repo/powla/tree/main/experimental/salt/swagger/python-server):

All URIs are relative to the server's base URL, e.g. *https://to.be.determin.ed/data*

Class | Method | HTTP request | Description
------------ | ------------- | ------------- | -------------
*CorpusApi* | [**addData**](docs/CorpusApi.md#addData) | **POST** /blob/{id} | Send raw data
*CorpusApi* | [**addFile**](docs/CorpusApi.md#addFile) | **POST** /file/{id} | Upload a corpus file
*CorpusApi* | [**delete**](docs/CorpusApi.md#delete) | **DELETE** /resource/{id} | Deletes a resource
*CorpusApi* | [**getResponse**](docs/CorpusApi.md#getResponse) | **GET** /resource/{id} | Get processed data (full or partial)



## Authors and Maintainers
* **Christian Chiarcos** - chiarcos@informatik.uni-frankfurt.de - [original author](https://github.com/acoli-repo/powla/tree/main/experimental/salt/swagger/java-client)
* **Christian F??th** - faeth@em.uni-frankfurt.de
* **Maxim Ionov** 
* **Leo Gottfried** 

See also the list of [contributors](https://github.com/acoli-repo/fintan-swagger-client/graphs/contributors) who participated in this project.

## Software Documentation (Fintan)
[fintan-doc](https://github.com/acoli-repo/fintan-doc)

## Reference (Fintan)
* F??th C., Chiarcos C., Ebbrecht B., Ionov M. (2020), Fintan - Flexible, Integrated Transformation and Annotation eNgineering. In: Proceedings of the 12th Language Resources and Evaluation Conference. LREC 2020. pp 7212-7221.

## Acknowledgments
This repository has been created in context of
* Applied Computational Linguistics ([ACoLi](http://acoli.cs.uni-frankfurt.de))
* Pr??t-??-LLOD. Ready-to-use Multilingual Linked Language Data for Knowledge Services across Sectors ([Pret-a-LLOD](https://cordis.europa.eu/project/id/825182/results))
  * Research and Innovation Action of the H2020 programme (ERC, grant agreement 825182)
  * In this project, CoNLL-RDF has been applied/developed/restructured to serve as backend of the Flexible Integrated Transformation and Annotation Engineering ([FINTAN](https://github.com/Pret-a-LLOD/Fintan)) Platform.

## Licenses
This repository is being published under an Apache 2.0 license, see [LICENSE.main](LICENSE.main.txt).

