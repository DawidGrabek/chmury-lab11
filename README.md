# Zadanie

Repozytorium zawiera manifesty Kubernetes umożliwiające wdrożenie bazy danych MySQL za pomocą StatefulSet. Przykład obejmuje skalowanie w górę i w dół.

## Pliki

- `mysql-service.yaml`: Definicja usługi **mysql-headless** dla adresowania DNS-owego Podów.
- `mysql-statefulset.yaml`: Konfiguracja StatefulSet dla MySQL z trwałym przechowywaniem danych.
- `mysql-secret.yaml`: Zakodowane dane uwierzytelniające MySQL.

## Wymagania wstępne

1. Klaster Kubernetes (minikube lub klaster w chmurze).
2. Zainstalowane i skonfigurowane narzędzie kubectl.

## Kroki wdrożenia

1. **Zastosowanie manifestów:**

   ```bash
   kubectl apply -f <każdy plik z osobna>
   ```

2. **Weryfikacja StatefulSet i Podów:**

   ```bash
   kubectl get statefulset
   kubectl get pods
   ```

   ![alt text](image-2.png)

3. **Sprawdzenie trwałych wolumenów:**

   ```bash
   kubectl get pvc
   ```

   ![alt text](image-1.png)

## Skalowanie StatefulSet

### Skalowanie w górę

Zwiększenie liczby replik:

```bash
kubectl scale statefulset mysql --replicas=5
```

Weryfikacja nowych Podów:

```bash
kubectl get pods
```

![alt text](image-3.png)

Sprawdzenie replikacji danych i kolejności inicjalizacji Podów.

### Skalowanie w dół

Zmniejszenie liczby replik:

```bash
kubectl scale statefulset mysql --replicas=2
```

```bash
kubectl get pods
```

![alt text](image-4.png)
