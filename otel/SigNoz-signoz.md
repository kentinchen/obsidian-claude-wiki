---
title: "SigNoz/signoz: SigNoz is an open-source observability platform native to OpenTelemetry with logs, traces and metrics in a single application. An open-source alternative to DataDog, NewRelic, etc. 🔥 🖥.   👉  Open source Application Performance Monitoring (APM) & Observability tool"
source: "https://github.com/SigNoz/signoz"
author:
published:
created: 2026-04-17
description: "SigNoz is an open-source observability platform native to OpenTelemetry with logs, traces and metrics in a single application. An open-source alternative to DataDog, NewRelic, etc. 🔥 🖥.   👉  Open source Application Performance Monitoring (APM) & Observability tool - SigNoz/signoz"
tags:
  - "clippings"
---
## SigNoz

All your logs, metrics, and traces in one place. Monitor your application, spot issues before they occur and troubleshoot downtime quickly with rich context. SigNoz is a cost-effective open-source alternative to Datadog and New Relic. Visit [signoz.io](https://signoz.io/) for the full documentation, tutorials, and guide.

## Features

### Application Performance Monitoring

Use SigNoz APM to monitor your applications and services. It comes with out-of-box charts for key application metrics like p99 latency, error rate, Apdex and operations per second. You can also monitor the database and external calls made from your application. Read [more](https://signoz.io/application-performance-monitoring/).

You can [instrument](https://signoz.io/docs/instrumentation/) your application with OpenTelemetry to get started.

[![apm-cover](https://private-user-images.githubusercontent.com/83692067/375960671-fa5c0396-0854-4c8b-b972-9b62fd2a70d2.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNTY4NDksIm5iZiI6MTc3NjM1NjU0OSwicGF0aCI6Ii84MzY5MjA2Ny8zNzU5NjA2NzEtZmE1YzAzOTYtMDg1NC00YzhiLWI5NzItOWI2MmZkMmE3MGQyLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDE2MjIyOVomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTc4YzBlNDgyYjc4MDZhY2JmZGRmNjdlZGRlZjI1NTI5YjRhZjM5NmM3NjZiOTEyN2RkZTBmNDI0MzhmNWNmMWImWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.-rnynyyK2MAZHbZTQeA3KFXYHAo659CP-_cTvHOn4pg)](https://private-user-images.githubusercontent.com/83692067/375960671-fa5c0396-0854-4c8b-b972-9b62fd2a70d2.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNTY4NDksIm5iZiI6MTc3NjM1NjU0OSwicGF0aCI6Ii84MzY5MjA2Ny8zNzU5NjA2NzEtZmE1YzAzOTYtMDg1NC00YzhiLWI5NzItOWI2MmZkMmE3MGQyLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDE2MjIyOVomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTc4YzBlNDgyYjc4MDZhY2JmZGRmNjdlZGRlZjI1NTI5YjRhZjM5NmM3NjZiOTEyN2RkZTBmNDI0MzhmNWNmMWImWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.-rnynyyK2MAZHbZTQeA3KFXYHAo659CP-_cTvHOn4pg)

### Logs Management

SigNoz can be used as a centralized log management solution. We use ClickHouse (used by likes of Uber & Cloudflare) as a datastore, ⎯ an extremely fast and highly optimized storage for logs data. Instantly search through all your logs using quick filters and a powerful query builder.

You can also create charts on your logs and monitor them with customized dashboards. Read [more](https://signoz.io/log-management/).

[![logs-management-cover](https://private-user-images.githubusercontent.com/83692067/375960682-343588ee-98fb-4310-b3d2-c5bacf9c7384.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNTY4NDksIm5iZiI6MTc3NjM1NjU0OSwicGF0aCI6Ii84MzY5MjA2Ny8zNzU5NjA2ODItMzQzNTg4ZWUtOThmYi00MzEwLWIzZDItYzViYWNmOWM3Mzg0LnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDE2MjIyOVomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPWRjZDUwYjFiY2FhMzZiY2NkOTdjYmM0MzgyYmNmZGQyMjA2ZmU3ODVjOWIzMzdmNWVmNzY5ZGFmOTU3NTMzMTYmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.6T4N3ahU0hbP0ouQVpKYnpHIGD4u-cMeRiBnzhf9BGE)](https://private-user-images.githubusercontent.com/83692067/375960682-343588ee-98fb-4310-b3d2-c5bacf9c7384.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNTY4NDksIm5iZiI6MTc3NjM1NjU0OSwicGF0aCI6Ii84MzY5MjA2Ny8zNzU5NjA2ODItMzQzNTg4ZWUtOThmYi00MzEwLWIzZDItYzViYWNmOWM3Mzg0LnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDE2MjIyOVomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPWRjZDUwYjFiY2FhMzZiY2NkOTdjYmM0MzgyYmNmZGQyMjA2ZmU3ODVjOWIzMzdmNWVmNzY5ZGFmOTU3NTMzMTYmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.6T4N3ahU0hbP0ouQVpKYnpHIGD4u-cMeRiBnzhf9BGE)

### Distributed Tracing

Distributed Tracing is essential to troubleshoot issues in microservices applications. Powered by OpenTelemetry, distributed tracing in SigNoz can help you track user requests across services to help you identify performance bottlenecks.

See user requests in a detailed breakdown with the help of Flamegraphs and Gantt Charts. Click on any span to see the entire trace represented beautifully, which will help you make sense of where issues actually occurred in the flow of requests.

Read [more](https://signoz.io/distributed-tracing/).

[![distributed-tracing-cover](https://private-user-images.githubusercontent.com/83692067/375960675-9bfe060a-0c40-4922-9b55-8a97e1a4076c.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNTY4NDksIm5iZiI6MTc3NjM1NjU0OSwicGF0aCI6Ii84MzY5MjA2Ny8zNzU5NjA2NzUtOWJmZTA2MGEtMGM0MC00OTIyLTliNTUtOGE5N2UxYTQwNzZjLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDE2MjIyOVomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPWVlMWZkNzlkNWRlYTFiM2E5ZTBmNDIyNmNhMWQ4OGJkNGFlZTA0NGZjY2Q1ZTM1YjM2MjIwNTViZTRiZmNiZDUmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.eLGUmBMfE3jiPJDgjsHgp0A8KW4QFRJIsYIWKa8nr4o)](https://private-user-images.githubusercontent.com/83692067/375960675-9bfe060a-0c40-4922-9b55-8a97e1a4076c.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNTY4NDksIm5iZiI6MTc3NjM1NjU0OSwicGF0aCI6Ii84MzY5MjA2Ny8zNzU5NjA2NzUtOWJmZTA2MGEtMGM0MC00OTIyLTliNTUtOGE5N2UxYTQwNzZjLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDE2MjIyOVomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPWVlMWZkNzlkNWRlYTFiM2E5ZTBmNDIyNmNhMWQ4OGJkNGFlZTA0NGZjY2Q1ZTM1YjM2MjIwNTViZTRiZmNiZDUmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.eLGUmBMfE3jiPJDgjsHgp0A8KW4QFRJIsYIWKa8nr4o)

### Metrics and Dashboards

Ingest metrics from your infrastructure or applications and create customized dashboards to monitor them. Create visualization that suits your needs with a variety of panel types like pie chart, time-series, bar chart, etc.

Create queries on your metrics data quickly with an easy-to-use metrics query builder. Add multiple queries and combine those queries with formulae to create really complex queries quickly.

Read [more](https://signoz.io/metrics-and-dashboards/).

[![metrics-n-dashboards-cover](https://private-user-images.githubusercontent.com/83692067/375960690-a536fd71-1d2c-4681-aa7e-516d754c47a5.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNTY4NDksIm5iZiI6MTc3NjM1NjU0OSwicGF0aCI6Ii84MzY5MjA2Ny8zNzU5NjA2OTAtYTUzNmZkNzEtMWQyYy00NjgxLWFhN2UtNTE2ZDc1NGM0N2E1LnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDE2MjIyOVomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTJhM2M5MjkyZWU2NGRlMWFlMGM2YWI0ZWJkMzAwODcxM2Y2MzMyZDE1M2RkZTg5ODQ2YjZmM2JhOTU2ZjZkOGUmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.9zmxHPPl8ZMQapb923C-29QWbpWQstfzY9VpJcDlRBA)](https://private-user-images.githubusercontent.com/83692067/375960690-a536fd71-1d2c-4681-aa7e-516d754c47a5.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNTY4NDksIm5iZiI6MTc3NjM1NjU0OSwicGF0aCI6Ii84MzY5MjA2Ny8zNzU5NjA2OTAtYTUzNmZkNzEtMWQyYy00NjgxLWFhN2UtNTE2ZDc1NGM0N2E1LnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDE2MjIyOVomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTJhM2M5MjkyZWU2NGRlMWFlMGM2YWI0ZWJkMzAwODcxM2Y2MzMyZDE1M2RkZTg5ODQ2YjZmM2JhOTU2ZjZkOGUmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.9zmxHPPl8ZMQapb923C-29QWbpWQstfzY9VpJcDlRBA)

### LLM Observability

Monitor and debug your LLM applications with comprehensive observability. Track LLM calls, analyze token usage, monitor performance, and gain insights into your AI application's behavior in production.

SigNoz LLM observability helps you understand how your language models are performing, identify issues with prompts and responses, track token usage and costs, and optimize your AI applications for better performance and reliability.

[Get started with LLM Observability →](https://signoz.io/docs/llm-observability/)

[![llm-observability-cover](https://private-user-images.githubusercontent.com/220771096/541808562-a6cc0ca3-59df-48f9-9c16-7c843fccff96.webp?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNTY4NDksIm5iZiI6MTc3NjM1NjU0OSwicGF0aCI6Ii8yMjA3NzEwOTYvNTQxODA4NTYyLWE2Y2MwY2EzLTU5ZGYtNDhmOS05YzE2LTdjODQzZmNjZmY5Ni53ZWJwP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI2MDQxNiUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNjA0MTZUMTYyMjI5WiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9NDgzMTk4ZjJiNmJjY2U2NmExNTQ4YTAxYTlkOGUxODQxNGRmMjA0ZmQ3MzFkYjI5OGU5MTBjNTBlMzk5MWFiYyZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QmcmVzcG9uc2UtY29udGVudC10eXBlPWltYWdlJTJGd2VicCJ9.I2CL4WzSD7jmVnD6nJXkhGLrfVPYciGVwY94XJRZrMU)](https://private-user-images.githubusercontent.com/220771096/541808562-a6cc0ca3-59df-48f9-9c16-7c843fccff96.webp?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNTY4NDksIm5iZiI6MTc3NjM1NjU0OSwicGF0aCI6Ii8yMjA3NzEwOTYvNTQxODA4NTYyLWE2Y2MwY2EzLTU5ZGYtNDhmOS05YzE2LTdjODQzZmNjZmY5Ni53ZWJwP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI2MDQxNiUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNjA0MTZUMTYyMjI5WiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9NDgzMTk4ZjJiNmJjY2U2NmExNTQ4YTAxYTlkOGUxODQxNGRmMjA0ZmQ3MzFkYjI5OGU5MTBjNTBlMzk5MWFiYyZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QmcmVzcG9uc2UtY29udGVudC10eXBlPWltYWdlJTJGd2VicCJ9.I2CL4WzSD7jmVnD6nJXkhGLrfVPYciGVwY94XJRZrMU)

### Alerts

Use alerts in SigNoz to get notified when anything unusual happens in your application. You can set alerts on any type of telemetry signal (logs, metrics, traces), create thresholds and set up a notification channel to get notified. Advanced features like alert history and anomaly detection can help you create smarter alerts.

Alerts in SigNoz help you identify issues proactively so that you can address them before they reach your customers.

Read [more](https://signoz.io/alerts-management/).

[![alerts-cover](https://private-user-images.githubusercontent.com/83692067/375960709-03873bb8-1b62-4adf-8f56-28bb7b1750ea.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNTY4NDksIm5iZiI6MTc3NjM1NjU0OSwicGF0aCI6Ii84MzY5MjA2Ny8zNzU5NjA3MDktMDM4NzNiYjgtMWI2Mi00YWRmLThmNTYtMjhiYjdiMTc1MGVhLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDE2MjIyOVomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTMxNDQwYzY5ZGM1NWFkNWU2MjBkYTQxMDhlZGEzMzYxYjliMWIwNTNhNzQyNmY0NzBiNmNhNWU3NjI1NzIzNTcmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.N1FipJ0DKXX6rasTdnKKpwop5xYvUmfACke2gQNzO5w)](https://private-user-images.githubusercontent.com/83692067/375960709-03873bb8-1b62-4adf-8f56-28bb7b1750ea.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNTY4NDksIm5iZiI6MTc3NjM1NjU0OSwicGF0aCI6Ii84MzY5MjA2Ny8zNzU5NjA3MDktMDM4NzNiYjgtMWI2Mi00YWRmLThmNTYtMjhiYjdiMTc1MGVhLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDE2MjIyOVomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTMxNDQwYzY5ZGM1NWFkNWU2MjBkYTQxMDhlZGEzMzYxYjliMWIwNTNhNzQyNmY0NzBiNmNhNWU3NjI1NzIzNTcmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.N1FipJ0DKXX6rasTdnKKpwop5xYvUmfACke2gQNzO5w)

### Exceptions Monitoring

Monitor exceptions automatically in Python, Java, Ruby, and Javascript. For other languages, just drop in a few lines of code and start monitoring exceptions.

See the detailed stack trace for all exceptions caught in your application. You can also log in custom attributes to add more context to your exceptions. For example, you can add attributes to identify users for which exceptions occurred.

Read [more](https://signoz.io/exceptions-monitoring/).

[![exceptions-cover](https://private-user-images.githubusercontent.com/83692067/375960714-4be37864-59f2-4e8a-8d6e-e29ad04298c5.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNTY4NDksIm5iZiI6MTc3NjM1NjU0OSwicGF0aCI6Ii84MzY5MjA2Ny8zNzU5NjA3MTQtNGJlMzc4NjQtNTlmMi00ZThhLThkNmUtZTI5YWQwNDI5OGM1LnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDE2MjIyOVomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTY4ODRkMjEyNmQ2OTEwOGYzNzQ4NWFhMGI0MzIwOWZhMWY4OTk4NDhhYWM5OGFiZTJjMDk5YjQwYWNhMWE1NjkmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.pGw3GKQnfD3ne1nKkLNO3awu2YQ6S8qey_reCc7ddHw)](https://private-user-images.githubusercontent.com/83692067/375960714-4be37864-59f2-4e8a-8d6e-e29ad04298c5.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNTY4NDksIm5iZiI6MTc3NjM1NjU0OSwicGF0aCI6Ii84MzY5MjA2Ny8zNzU5NjA3MTQtNGJlMzc4NjQtNTlmMi00ZThhLThkNmUtZTI5YWQwNDI5OGM1LnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDE2MjIyOVomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTY4ODRkMjEyNmQ2OTEwOGYzNzQ4NWFhMGI0MzIwOWZhMWY4OTk4NDhhYWM5OGFiZTJjMDk5YjQwYWNhMWE1NjkmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.pGw3GKQnfD3ne1nKkLNO3awu2YQ6S8qey_reCc7ddHw)

## Why SigNoz?

SigNoz is a single tool for all your monitoring and observability needs. Here are a few reasons why you should choose SigNoz:

- Single tool for observability(logs, metrics, and traces)
- Built on top of [OpenTelemetry](https://opentelemetry.io/), the open-source standard which frees you from any type of vendor lock-in
- Correlated logs, metrics and traces for much richer context while debugging
- Uses ClickHouse (used by likes of Uber & Cloudflare) as datastore - an extremely fast and highly optimized storage for observability data
- DIY Query builder, PromQL, and ClickHouse queries to fulfill all your use-cases around querying observability data
- Open-Source - you can use open-source, our [cloud service](https://signoz.io/teams/) or a mix of both based on your use case

## Getting Started

### Create a SigNoz Cloud Account

SigNoz cloud is the easiest way to get started with SigNoz. Our cloud service is for those users who want to spend more time in getting insights for their application performance without worrying about maintenance.

[Get started for free](https://signoz.io/teams/)

### Deploy using Docker(self-hosted)

Please follow the steps listed [here](https://signoz.io/docs/install/docker/) to install using docker

The [troubleshooting instructions](https://signoz.io/docs/install/troubleshooting/) may be helpful if you face any issues.

### Deploy in Kubernetes using Helm(self-hosted)

Please follow the steps listed [here](https://signoz.io/docs/deployment/helm_chart) to install using helm charts

We also offer managed services in your infra. Check our [pricing plans](https://signoz.io/pricing/) for all details.

## Join our Slack community

Come say Hi to us on [Slack](https://signoz.io/slack) 👋

### Languages supported:

SigNoz supports all major programming languages for monitoring. Any framework and language supported by OpenTelemetry is supported by SigNoz. Find instructions for instrumenting different languages below:

- [Java](https://signoz.io/docs/instrumentation/java/)
- [Python](https://signoz.io/docs/instrumentation/python/)
- [Node.js or Javascript](https://signoz.io/docs/instrumentation/javascript/)
- [Go](https://signoz.io/docs/instrumentation/golang/)
- [PHP](https://signoz.io/docs/instrumentation/php/)
- [.NET](https://signoz.io/docs/instrumentation/dotnet/)
- [Ruby](https://signoz.io/docs/instrumentation/ruby-on-rails/)
- [Elixir](https://signoz.io/docs/instrumentation/elixir/)
- [Rust](https://signoz.io/docs/instrumentation/rust/)
- [Swift](https://signoz.io/docs/instrumentation/swift/)

You can find our entire documentation [here](https://signoz.io/docs/introduction/).

## Comparisons to Familiar Tools

### SigNoz vs Prometheus

Prometheus is good if you want to do just metrics. But if you want to have a seamless experience between metrics, logs and traces, then current experience of stitching together Prometheus & other tools is not great.

SigNoz is a one-stop solution for metrics and other telemetry signals. And because you will use the same standard(OpenTelemetry) to collect all telemetry signals, you can also correlate these signals to troubleshoot quickly.

For example, if you see that there are issues with infrastructure metrics of your k8s cluster at a timestamp, you can jump to other signals like logs and traces to understand the issue quickly.

### SigNoz vs Jaeger

Jaeger only does distributed tracing. SigNoz supports metrics, traces and logs - all the 3 pillars of observability.

Moreover, SigNoz has few more advanced features wrt Jaeger:

- Jaegar UI doesn’t show any metrics on traces or on filtered traces
- Jaeger can’t get aggregates on filtered traces. For example, p99 latency of requests which have tag - customer\_type='premium'. This can be done easily on SigNoz
- You can also go from traces to logs easily in SigNoz

### SigNoz vs Elastic

- SigNoz Logs management are based on ClickHouse, a columnar OLAP datastore which makes aggregate log analytics queries much more efficient
- 50% lower resource requirement compared to Elastic during ingestion

We have published benchmarks comparing Elastic with SigNoz. Check it out [here](https://signoz.io/blog/logs-performance-benchmark/?utm_source=github-readme&utm_medium=logs-benchmark)

### SigNoz vs Loki

- SigNoz supports aggregations on high-cardinality data over a huge volume while loki doesn’t.
- SigNoz supports indexes over high cardinality data and has no limitations on the number of indexes, while Loki reaches max streams with a few indexes added to it.
- Searching over a huge volume of data is difficult and slow in Loki compared to SigNoz

We have published benchmarks comparing Loki with SigNoz. Check it out [here](https://signoz.io/blog/logs-performance-benchmark/?utm_source=github-readme&utm_medium=logs-benchmark)

## Contributing

We ❤️ contributions big or small. Please read [CONTRIBUTING.md](https://github.com/SigNoz/signoz/blob/main/CONTRIBUTING.md) to get started with making contributions to SigNoz.

Not sure how to get started? Just ping us on `#contributing` in our [slack community](https://signoz.io/slack)

## Documentation

You can find docs at [https://signoz.io/docs/](https://signoz.io/docs/). If you need any clarification or find something missing, feel free to raise a GitHub issue with the label `documentation` or reach out to us at the community slack channel.

## Community

Join the [slack community](https://signoz.io/slack) to know more about distributed tracing, observability, or SigNoz and to connect with other users and contributors.

If you have any ideas, questions, or any feedback, please share on our [Github Discussions](https://github.com/SigNoz/signoz/discussions)

As always, thanks to our amazing contributors!

[![](https://camo.githubusercontent.com/3267ed973d01e503235f559083c3c35682de68186cad3bcc1f73dc1dfcd388d8/68747470733a2f2f636f6e747269622e726f636b732f696d6167653f7265706f3d7369676e6f7a2f7369676e6f7a)](https://github.com/signoz/signoz/graphs/contributors)