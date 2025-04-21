# Currency Converter API - Configuración

Este repositorio contiene la configuración de infraestructura para desplegar la API de conversión de moneda en un clúster de Kubernetes. Utiliza Helm para la gestión de plantillas y ArgoCD para el despliegue continuo.

## Estructura del Repositorio

```
currency-converter-config/
├── helm/                     # Configuraciones de Helm
│   └── currency-converter-api/
│       ├── Chart.yaml        # Metadatos del chart
│       ├── values.yaml       # Valores predeterminados
│       └── templates/        # Plantillas YAML 
│           ├── deployment.yaml
│           ├── service.yaml
│           ├── ingress.yaml
│           └── hpa.yaml
└── argocd/                   # Configuraciones de ArgoCD
    └── applications/
        └── currency-converter.yaml
```

## Despliegue con ArgoCD

1. Asegúrate de tener ArgoCD instalado en tu clúster de Kubernetes.
2. Aplica el archivo de configuración de ArgoCD:

```bash
kubectl apply -f argocd/applications/currency-converter.yaml
```

3. ArgoCD detectará automáticamente los cambios en este repositorio y aplicará la configuración de Helm al clúster.

## Configuración con Helm

Si deseas desplegar manualmente usando Helm:

```bash
# Instalar el chart
helm install currency-converter ./helm/currency-converter-api

# Actualizar el chart
helm upgrade currency-converter ./helm/currency-converter-api

# Desinstalar el chart
helm uninstall currency-converter
```

## Personalización

Puedes personalizar la configuración modificando el archivo `values.yaml` o proporcionando un archivo de valores personalizado:

```bash
helm install currency-converter ./helm/currency-converter-api -f my-values.yaml
```