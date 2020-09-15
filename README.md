# helloapp-helm
This is a Helm Chart to deploy Helloapp for poc on build &amp; deploy to kubernetes.

## Version details :

- apiVersion: v2
- name: helloapp
- description: Helm chart to deploy helloapp in kubernetes
- type: application
- version: 0.1.0
- appVersion: 1.16.0

## Exposed parameters

replicaCount: 1
image:
  repository: txconsole/helloapp
  pullPolicy: IfNotPresent
  tag: "latest"

service:
  type: NodePort
  port: 8080

ingress:
  enabled: false
  annotations: {}
     kubernetes.io/ingress.class: nginx
     kubernetes.io/tls-acme: "true"
  hosts:
    - host: chart-example.local
      paths: []
  tls: []
  
resources: {}
   limits:
     cpu: 100m
     memory: 128Mi
   requests:
     cpu: 100m
     memory: 128Mi
  
autoscaling:
  enabled: false
  minReplicas: 1
  maxReplicas: 100
  targetCPUUtilizationPercentage: 80
  # targetMemoryUtilizationPercentage: 80
