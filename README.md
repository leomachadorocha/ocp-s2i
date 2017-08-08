# Source 2 Image Example

Sample Java Web Application for use in OpenShift

#### 1. create new project
```
oc new-project demo-s2i \
--display-name="Demonstração Básica do S2I" \
--description="Demonstração básica do build strategy S2I, usando o EAP 7"
```

#### 2. create the new Java web application
```
$ oc new-app --name=myapp jboss-eap70-openshift~https://github.com/leomachadorocha/ocp-s2i-lab.git
```
```
--> Found image 6257411 (2 months old) in image stream "openshift/jboss-eap70-openshift" under tag "latest" for "jboss-eap70-openshift"

    JBoss EAP 7.0 
    ------------- 
    Platform for building and running JavaEE applications on JBoss EAP 7.0

    Tags: builder, javaee, eap, eap7

    * A source build using source code from https://github.com/leomachadorocha/ocp-s2i-lab.git will be created
      * The resulting image will be pushed to image stream "myapp:latest"
      * Use 'start-build' to trigger a new build
    * This image will be deployed in deployment config "myapp"
    * Ports 8080/tcp, 8443/tcp, 8778/tcp will be load balanced by service "myapp"
      * Other containers can access this service through the hostname "myapp"

--> Creating resources with label app=myapp ...
    imagestream "myapp" created
    buildconfig "myapp" created
    deploymentconfig "myapp" created
    service "myapp" created
--> Success
    Build scheduled, use 'oc logs -f bc/myapp' to track its progress.
    Run 'oc status' to view your app.
```

#### 3. expose the service
```
$ oc expose svc myapp
```
```
route "myapp" exposed
```

#### 4. get information about the deployment
```
$ oc status
```

#### 5. make changes to the src/main/webapp/index.jsp file


#### 6. start a new build
```
$ oc start-build myapp
```

#### 7. see the logs
```
$ oc logs -f bc/myapp
```

#### 8. see the changes applied

fonte: https://blog.openshift.com/getting-started-with-jboss-enterprise-application-platform/

# Adding Webhook

No Git Hub, em https://github.com/leomachadorocha/ocp-s2i-lab/settings/hooks:
- informar o campo "Payload URL" com o valor do campo "GitHub Webhook URL:" obtido na página de configurações da Build.
- alterar o campo "Content type" para "application/json".
- desabilitar a SSL verification.

