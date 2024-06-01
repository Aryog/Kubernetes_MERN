# Kubernetes Setup with Minikube

This guide will walk you through setting up a Kubernetes environment using Minikube, and deploying your application using secrets, config maps, and services.

## Prerequisites

- [Install Kubernetes](https://kubernetes.io/docs/tasks/tools/install-kubectl/)
- [Install Minikube](https://minikube.sigs.k8s.io/docs/start/)

## Steps to Setup and Deploy

1. **Start Minikube**

   ```sh
   minikube start
   ```

   This command starts Minikube, which runs a single-node Kubernetes cluster in a VM on your local machine.

2. **Check for Pods**

   ```sh
   kubectl get pod
   ```

   At this point, no pods should be running.

3. **Apply Configuration Files**

   ```sh
   kubectl apply -f secrets.yaml
   kubectl apply -f mongo-config.yaml
   kubectl apply -f mongo-app.yaml
   kubectl apply -f web-app.yaml
   ```

   These commands apply the configuration files for secrets, MongoDB configuration, MongoDB application, and web application.

4. **Check Pods Status**

   ```sh
   kubectl get pod
   ```

   Now, you should see the pods running.

5. **Get Detailed Pod Information**

   ```sh
   kubectl get pod -o wide
   ```

   This provides a detailed view of the running pods.

6. **Retrieve Secrets and ConfigMaps**

   ```sh
   kubectl get secret
   kubectl get configmap
   ```

7. **Get Services**

   ```sh
   kubectl get svc
   ```

   This lists all the services running in your cluster.

8. **Get Minikube IP**

   ```sh
   minikube ip
   ```

9. **Access the Web Application**

   ```sh
   minikube service webapp-service
   ```

   This command will open the web application in your default browser. Alternatively, you can use the Minikube IP and the port of the service to access it.

## Additional Notes

- Ensure all your YAML configuration files (`secrets.yaml`, `mongo-config.yaml`, `mongo-app.yaml`, `web-app.yaml`) are correctly set up with the necessary configurations for your application.
- If any service is not running as expected, use `kubectl describe pod <pod-name>` and `kubectl logs <pod-name>` to debug.
- For more detailed information on each command and Kubernetes concepts, refer to the [Kubernetes Documentation](https://kubernetes.io/docs/home/).

## Troubleshooting

- If you encounter issues starting Minikube, ensure your virtualization is enabled in your BIOS settings.
- Check for any conflicts on the ports being used by Minikube and other local applications.

## Conclusion

By following these steps, you should have a local Kubernetes environment running your application with Minikube. Feel free to expand on this setup by adding more services, scaling your deployments, and experimenting with Kubernetes features.
