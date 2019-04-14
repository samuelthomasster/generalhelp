<h1>API reference documentation</h1>
<h2>
  Objective
</h2>
<p>The reference documentation that Grab provides must be self-explanatory, comprehensive and should include live code examples wherever possible. The objective of the documentation should be that external customers can:</p>
<ul>
<ol>understand and use our APIs without talking to our support or development team.</ol>
<ol>run and test the APIs with minimal help from Grab in the form of providing authorization tokens.</ol>
<ol>Troubleshoot any issues they might face while integrating their development environment with our APIs.</ol>
</ul>
<h2>Swagger output</h2>
<p>We can follow the same method to generate API documentation for external customers also. <p/>

|                               | Advantages                                                   | Disadvantages                                                |
| ----------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Write once in a proto file    | Annotations are in the code. Zero gap between the code and documentation. Minimal rework. | Code layout looks messy and bulky with inline annotations occupying most of the proto file. |
| Capture API running sequence  | Uses existing Swagger output.                                | Swagger output does not capture detailed API explanation. We can't introduce images or the order in which to run a set of APIs. |
| Provide a testing environment | One of the advantages of Swagger output is its ability to let users test the endpoints. If the API endpoints can be hosted behind a user session, then we can enable the customers to run the APIs. | Most often this is not the case. Without the ability to run the APIs, Swagger API reference output is not very user friendly especially for external customers. |

<h2>Slate output</h2>

Another popular trend in API documentation is using a 3-column format that contains the navigation elements on the left, with API description and contextual information in the middle and code examples on the right. This format is supported by an open source tool called Slate which uses middleman server (OOB) to publish the static website.

Slate output requires generation of a markdown file and hosting it on a static website. You can use a Slate plugin to convert the Swagger json/yaml/html file to a markdown file. The html file can also be generated using the protoc-gen-doc plugin (that we have already evaluated).

|                                |                                                              |                                                              |
| ------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Annotations are away from code | Code is clean and easy to read.                              | If the API behaviour changes frequently then we have to track the changes and change the documentation accordingly. |
| Provide user-friendly content  | You can add images, contextual information, API sequence custom written for each API endpoint to help customers leverage your APIs easily. | Someone has to manually add them and this information is away from code. |
| Provide a testing environment  | You can provide example cURL requests and responses and with developer's help, create a portal that can help run the APIs. | Needs developer's effort to customize the portal.            |

<h2>Common things to address</h2>
<p>Things to keep in mind while creating external-facing API reference documentation:</p>

- How do customers access our API endpoints? Explain the authentication token/session creating APIs in detail with multiple working examples.
- Run each API endpoint either using cURL or postman collections as how a customer would run it. Make sure you do are not a priviledged network and do not use an existing development environment.
- Explain all error codes and provide recommendations on how to fix the errors. 
  