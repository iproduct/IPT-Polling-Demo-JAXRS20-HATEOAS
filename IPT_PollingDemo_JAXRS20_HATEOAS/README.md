IPT_Polling_Demo_JAX-RS_2.0_HATEOAS
====================================

IPT_Polling_Demo_JAX-RS_2.0_HATEOAS is a Maven project demonstrating REST HATEOAS 
development using novelties in JAX-RS 2.0 API and GlassFish Jersey RI, such as:

 - Standardized REST Client API;

 - Client-side and server-side asynchronous HTTP request processing;

 - Integration of declarative validation of resources, response entities, 
   method parameters, and fields using JSR 349: Bean Validation 1.1;

 - Improved server-suggested content negotiation in addition to that suggested 
   by client;

 - Aspect-oriented extensibility of request/response processing using Filters 
   (non wrapping) and Interceptors (wrapping) client and server extension points;

 - Dynamic  extension registration using DynamicFeature interface;

 - Hypermedia As The Engine Of Application State (HATEOAS) REST architectural 
   constraint support using state transition links (support for new HTTP Link 
   header as well as JAXB serialization of resource links).

The demo can be deployed on Java EE 7 Server (e.g. Glassfish 4.1) and needs 
a data-source to be configured in /src/main/resources/META-INF/persistence.xml
and administratively created on Java EE Server.

Because this can somewhat "labor intensive" it can also be run on embedded 
GlassFish 4 Server using Maven goal: embedded-glassfish:run
The embedded server is run on 8080 by default (you can change it in maven config
for "maven-embedded-glassfish-plugin" in pom.xml file) and uses a JTA data-source 
GlassFish creates by default: jdbc/__TimerPool

You can also run integration tests - as a demo configuration there are two 
test classes:

 - PollsResourceJerseyTest - run by maven-surefire-plugin and extending JerseyTest
   (using Jersey Test Framework allowing running tests with a number of embedded
   or external containers (e.g. Grizzly2, Jetty,  GlassFish, etc.)

 - PollsResourceIT - integration tests run by maven-failsafe-plugin after starting 
   the embedded GlassFish server and deploying the app at /polling web context URI
   By default maven-failsafe-plugin recognizes the integration tests from unit tests 
   by naming conventions: **/IT*.java, **/*IT.java, and **/*ITCase.java.


 