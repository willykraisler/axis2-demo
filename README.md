Apache Axis2 demo
==========
This is Apache Axis2 Demo Project.

If you want to build this project, please follow the next step.
1, checkout out parent and run: 
    git clone git@github.com:bulain/parent.git
    mvn install
2, checkout out axis2-demo:
    git clone git@github.com:bulain/axis2-demo.git
    mvn eclipse:eclipse
    
Server side Task:
1. Deploying POJOs
2. Building the service using AXIOM
3. Generating the service using ADB
4. Generating the service using XMLBeans
5. Generating the service using JiBX

Client side Task:
1. Creating a client using AXIOM
2. Generating a client using ADB
3. Generating a client using XML Beans
4. Generating a client using JiBX

DemoService
http://localhost:8082/axis2-demo/services/DemoService?wsdl
http://localhost:8082/axis2-demo/services/DemoService/emerge
http://localhost:8082/axis2-demo/services/DemoService?emerge

Axis
mvn axis2-wsdl2code:java2wsdl -Pjava2wsdl
mvn axis2-wsdl2code:wsdl2code -Pwsdl2code-adb
mvn axis2-wsdl2code:wsdl2code -Pwsdl2code-jibx
mvn axis2-wsdl2code:wsdl2code -Pwsdl2code-axiom  <can't work>
mvn axis2-wsdl2code:wsdl2code -Pwsdl2code-xmlbeans  <can't work>
mvn process-classes -P

Jibx
mvn jibx:schema-codegen -Pschema-codegen
mvn jibx:jibx2wsdl -Pjibx2wsdl
mvn jibx:bind -Pbind
mvn process-classes -P

Jetty
mvn jetty:run
mvn jetty:run -Pit

Build
mvn eclipse:eclipse -Pwsdl2code-jibx
mvn clean package -Pbind -Dmaven.test.skip=true
mvn clean package -Pbind -Pwsdl2code-jibx -Dmaven.test.skip=true
mvn test-compile