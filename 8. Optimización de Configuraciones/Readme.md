# Optimización de Configuraciones

Este entorno permite monitorizar contenedores Docker usando Prometheus para recopilar métricas, cAdvisor para exponer estadísticas de contenedores, y Grafana para visualizarlas mediante dashboards.
Servicios utilizados

    Prometheus: recopila métricas y las almacena.

    cAdvisor: proporciona información sobre el uso de recursos de contenedores Docker.

    Grafana: plataforma de visualización para explorar las métricas recolectadas.

Pasos realizados

    Se definieron los servicios en un docker-compose.yml.

    Se creó un archivo .env con las siguientes variables:

    PROMETHEUS_PORT=9090
    CADVISOR_PORT=8081
    GRAFANA_PORT=3000

    Se levantaron los servicios con el comando:
    docker-compose up -d

    Se accedió a Grafana en el puerto 3000. Al entrar con usuario y contraseña por defecto (admin / admin), se forzó el cambio de contraseña.

    Se añadió Prometheus como fuente de datos en Grafana usando la URL http://prometheus:9090.

    Se importó el dashboard 193 desde Grafana.com para visualizar métricas de los contenedores (uso de CPU, memoria, red, etc.).

Mejoras aplicadas

    Se limitaron los recursos de los contenedores: 0.5 CPU y 512 MB de RAM.

    Se usaron imágenes con versión específica para evitar problemas futuros por cambios.

    Se reorganizó el archivo usando variables de entorno para definir los puertos.

    Se definió una red propia llamada "monitoring" para aislar los servicios.

    Se expusieron solo los puertos necesarios para cada servicio.

    Se añadieron volúmenes persistentes para mantener los datos de Prometheus y Grafana.
