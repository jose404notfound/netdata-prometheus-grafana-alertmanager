# NETDATA - PROMETHEUS - GRAFANA - ALERTMANAGER
Este proyecto integra **Netdata**, **Prometheus**, **Grafana** y **Alertmanager** para proporcionar una solución completa de monitoreo y alertas.

## Contenido del Repositorio
- `docker-compose.yml`: Configuración para desplegar los servicios utilizando Docker Compose.
- `prometheus.yml`: Configuración de Prometheus para la recolección de métricas.
- `alertmanager.yml`: Configuración de Alertmanager para la gestión de alertas.
- `alert_rules.yml`: Reglas de alertas definidas para Prometheus.

## Requisitos Previos
- Docker y Docker Compose instalados en tu sistema.

## Instalación y Puesta en Marcha

1. **Clonar el repositorio:**

    ```bash
    git clone https://github.com/jose404notfound/netdata-prometheus-grafana-alertmanager.git
    cd netdata-prometheus-grafana-alertmanager
    ```

2. **Iniciar los servicios:**

    ```bash
    docker-compose up -d
    ```

    Esto desplegará los contenedores de **Netdata**, **Prometheus**, **Grafana** y **Alertmanager** en segundo plano.

## Acceso a las Interfaces Web

- **Netdata**: [http://localhost:19999](http://localhost:19999)
- **Prometheus**: [http://localhost:9090](http://localhost:9090)
- **Grafana**: [http://localhost:3000](http://localhost:3000)
- **Alertmanager**: [http://localhost:9093](http://localhost:9093)

> Nota: Asegúrate de que estos puertos estén disponibles y no en uso por otros servicios. Cambia `localhost` por la IP en caso de que sea necesario.

## Configuración de Grafana

1. **Acceder a Grafana**: Navega a [http://localhost:3000](http://localhost:3000) y utiliza las credenciales predeterminadas (**admin/admin**) para iniciar sesión.

2. **Agregar Prometheus como fuente de datos**:
    - Ve a `Configuration > Data Sources`.
    - Haz clic en `Add data source`.
    - Selecciona **Prometheus**.
    - En el campo **URL**, ingresa `http://<IP>:9090`.
    - Guarda la configuración.

3. **Importar dashboards**:
    - Ve a `Create > Import`.
    - Ingresa el ID del dashboard deseado desde [Grafana Dashboards](https://grafana.com/grafana/dashboards).
    - Asocia la fuente de datos de Prometheus y completa la importación.

## Gestión de Alertas

Las reglas de alerta se definen en el archivo `alert_rules.yml`. Estas reglas son cargadas por Prometheus y las alertas resultantes son gestionadas por **Alertmanager** según la configuración en `alertmanager.yml`.

Para más información sobre la configuración de alertas, consulta la [documentación oficial de Prometheus](https://prometheus.io/docs/prometheus/latest/configuration/alerting_rules/) y [Alertmanager](https://prometheus.io/docs/alerting/latest/alertmanager/).

## Personalización

- **Netdata**: La configuración predeterminada de Netdata está incluida en el contenedor. Para personalizarla, puedes crear un volumen que monte tu configuración personalizada en `/etc/netdata/`.
- **Prometheus**: Ajusta las reglas de scrapeo y alertas en `prometheus.yml` y `alert_rules.yml` según tus necesidades.
- **Grafana**: Agrega paneles y fuentes de datos adicionales según los requisitos de tu monitoreo.

## Contribuciones

Las contribuciones son bienvenidas. Por favor, abre un issue o envía un pull request para sugerencias o mejoras.

## Licencia

Este proyecto está bajo la Licencia **MIT**. Consulta el archivo `LICENSE` para más detalles.

