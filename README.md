# JBoss EAP running in a container

Trying out JBoss EAP in a container.

## Usage

1. Build the image.

  ```shell
  docker build . -t jboss
  ```

1. Run the image

  ```shell
  docker run --publish-all --name jboss jboss
  ```

1. Get the port mapping

  ```shell
  docker container ps
  ```

  This will show the jboss container under the `PORTS` column.

1. Open a browser to `http://localhost:<port-mapped-to-8080>`.

## Notes

- Jboss EAP OpenShift container image: `jboss-eap-7/eap72-openshift`
- OpenShift docs seem to lean towards using Source-to-Image (S2I) [S@I GitHub repo](https://github.com/openshift/source-to-image)
- Deployments should be done using `/wardeploy`
  - The JBoss EAP management console is not included in JBoss EAP **for OpenShift**. So it is likely best to not use it in the container. [Source](https://access.redhat.com/documentation/en-us/red_hat_jboss_enterprise_application_platform/7.2/html-single/getting_started_with_jboss_eap_for_openshift_container_platform/index)
- "The JBoss EAP management CLI is not recommended for use with JBoss EAP running in a containerized environment. Any configuration changes made using the management CLI in a running container will be lost when the container restarts." [Source](https://access.redhat.com/documentation/en-us/red_hat_jboss_enterprise_application_platform/7.2/html-single/getting_started_with_jboss_eap_for_openshift_container_platform/index)

## Open questions

- How would a user deploy their customer patches onto this?

## Links

- [JBoss EAP 7.2 for OpenShift Container Image](https://access.redhat.com/containers/?extIdCarryOver=true&sc_cid=701f2000001Css5AAC&tab=images&get-method=unauthenticated#/registry.access.redhat.com/jboss-eap-7/eap72-openshift)

- User-made container images:
  - https://hub.docker.com/r/daggerok/jboss-eap-7.1/dockerfile
  - https://www.redhat.com/en/about/videos/deploy-applications-linux-container-red-hat-jboss-eap
  - https://medium.com/@gloriapalmagonzalez/example-dockerfile-jboss-eap-7-for-deploying-an-application-using-the-deployment-scanner-e6841bc180
