
  

# Django Telemetry Example

  

This repository is an example of using OpenTelemetry with Jaeger and Zipkin for tracing in a Django application.

  

## Prerequisites

  

- Docker

- Docker Compose

  

## Setup

  

1. Clone the repository:

  

```sh

git  clone <repository-url>

cd <repository-directory>

```

  

2. Start the services using Docker Compose:

  

```sh

docker-compose  up

```

  

This will start the following services:

- OpenTelemetry Collector

- Jaeger

- Zipkin

  

## Django Application

  

The Django application is configured to use SQLite as the database. You can run the application using the following command:

  

```sh

opentelemetry-instrument  --service_name  django  python  manage.py  runserver  --noreload

```

  

## OpenTelemetry Configuration

  

The OpenTelemetry Collector is configured using the

  

otel-collector-config.yaml:

- It receives traces via OTLP and exports them to Jaeger and Zipkin.

  

## Accessing the Tracing UI

  

- Jaeger: [http://localhost:16686](http://localhost:16686)
	- - select django form services

- Zipkin: [http://localhost:9411](http://localhost:9411)
	- select django for service name on UI