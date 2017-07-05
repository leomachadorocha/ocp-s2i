Source 2 Image Example

# os-sample-java-web
Sample Java Web Application for use in OpenShift


1 - create the new Java web application
$ oc new-app --name=myapp jboss-eap64-openshift~https://github.com/leomachadorocha/os-sample-java-web.git
--> Creating resources with label app=myapp ...
    imagestream "myapp" created
    buildconfig "myapp" created
    deploymentconfig "myapp" created
    service "myapp" created
--> Success
    Build scheduled, use 'oc logs -f bc/myapp' to track its progress.
    Run 'oc status' to view your app.

2 - expose the service
$ oc expose svc myapp
route "myapp" exposed

3 - get information about the deployment
$ oc status


fonte: https://blog.openshift.com/getting-started-with-jboss-enterprise-application-platform/
