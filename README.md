# Installation de Prometheus sur Kubernetes

Prometheus est un système de surveillance open-source conçu pour la collecte et l'alerte basée sur les métriques. Dans cet exemple, nous allons installer Prometheus dans un cluster Kubernetes.

## Prérequis

-   Un cluster Kubernetes en cours d'exécution
-   kubectl installé et configuré pour accéder à votre cluster
-   Helm installé sur votre machine locale et configuré pour accéder à votre cluster

## Étapes d'installation

### 1. Configuration de Helm

`helm repo add prometheus-community https://prometheus-community.github.io/helm-charts helm repo update`

### 2. Installation de Prometheus

`kubectl create namespace monitoring helm install prometheus prometheus-community/prometheus --namespace monitoring`

### 3. Accès à l'interface utilisateur de Prometheus

`kubectl port-forward -n monitoring svc/prometheus-server 9090:80`

Ouvrez votre navigateur et accédez à http://localhost:9090 pour accéder à l'interface utilisateur de Prometheus.

### 4. Configuration des cibles de surveillance

Pour configurer les cibles à surveiller, vous pouvez modifier le fichier `values.yaml` lors de l'installation ou utiliser la console web de Prometheus.

### 5. Suppression

`helm uninstall prometheus -n monitoring kubectl delete namespace monitoring`

Cela désinstallera Prometheus et supprimera le namespace associé.

## Conclusion

Félicitations, Prometheus est bien installé dans votre cluster Kubernetes. 
Pour plus d'infos (lien de la doc officiel) : https://prometheus.io/docs/introduction/overview/
