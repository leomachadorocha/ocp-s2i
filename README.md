# Source 2 Image Example

Sample Java Web Application for use in OpenShift

#### 1 - create new project
```oc new-project demo-s2i \
--display-name="Demonstração Básica do S2I" \
--description="Demonstração básica do build strategy S2I, usando o EAP 7"```

#### 2 - create the new Java web application
```$ oc new-app --name=myapp jboss-eap64-openshift~https://github.com/leomachadorocha/os-sample-java-web.git```
```
--> Creating resources with label app=myapp ...
    imagestream "myapp" created
    buildconfig "myapp" created
    deploymentconfig "myapp" created
    service "myapp" created
--> Success
    Build scheduled, use 'oc logs -f bc/myapp' to track its progress.
    Run 'oc status' to view your app.
```

#### 3 - expose the service
```$ oc expose svc myapp```
```
route "myapp" exposed
```

#### 4 - get information about the deployment
```$ oc status```

#### 5 - make changes to the src/main/webapp/index.jsp file

#### 6 - start a new build
```$ oc start-build myapp```

#### 7 - see the changes applied

fonte: https://blog.openshift.com/getting-started-with-jboss-enterprise-application-platform/



# Adding Webhook

No Git Hub, em https://github.com/<your_user>/os-sample-java-web/settings/hooks, atualizar APENAS o campo "Payload URL" com o valor do campo "GitHub webhook URL:" obtido na página de configurações da Build do OpenShift.
