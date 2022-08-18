# migration of application from docker-compose to kubernetes
1. Create applications
kubectl apply -f ecollect-deployment-artifacts/

Below objects are created:


2. Confirm all objects are created and pods and running

kubectl get pods -n ecol
kubectl get svc -n ecol
kubectl get hpa -n ecol

3. Stop docker-compose services
docker-compose down

4. Load Balancer
configure haproxy lB on 172.16.204.74