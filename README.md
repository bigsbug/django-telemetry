# Django Telemetry Example

This repository demonstrates integrating **OpenTelemetry** with **Jaeger** and **Zipkin** for tracing in a Django application.

---

## Prerequisites

- [Docker](https://www.docker.com/)
- [Docker Compose](https://docs.docker.com/compose/)
- [Python 3.8+](https://www.python.org/)

---

## Setup

1. **Clone the Repository**

   ```bash
   git clone https://github.com/bigsbug/django-telemetry.git
   cd django-telemetry
   ```

2. **Install Python Dependencies**

   Create a virtual environment (optional) and install the required Python packages:

   ```bash
   python -m venv venv
   source venv/bin/activate   # On Windows: venv\Scripts\activate
   pip install -r requirements.txt
   ```

3. **Start the Services**

   Use Docker Compose to start the required services:

   ```bash
   docker-compose up
   ```

   This command starts the following services:
   - **OpenTelemetry Collector**
   - **Jaeger**
   - **Zipkin**

---

## Django Application

The Django application is preconfigured to use SQLite as its database. You can run the application with OpenTelemetry instrumentation by executing:

```bash
opentelemetry-instrument --service_name django python manage.py runserver --noreload
```

---

## OpenTelemetry Configuration

The OpenTelemetry Collector is configured using `otel-collector-config.yaml`:
- **Receivers:** Accept traces via OTLP (gRPC & HTTP).
- **Exporters:** Send traces to **Jaeger** and **Zipkin**.

---

## Accessing Tracing UIs

1. **Jaeger**  
   Access Jaeger's UI at [http://localhost:16686](http://localhost:16686).  
   - In the UI, select `django` from the list of services.

2. **Zipkin**  
   Access Zipkin's UI at [http://localhost:9411](http://localhost:9411).  
   - In the UI, choose `django` as the service name.

---

Feel free to fork this repository and use it as a base for experimenting with telemetry in Django applications!