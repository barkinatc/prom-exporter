# TLS Certificate Expiry Exporter

## Overview

This project is a Prometheus exporter that monitors TLS certificate expiration dates for remote URLs.  
It checks configured endpoints, calculates remaining time until expiry, and exposes metrics for Prometheus.

It is packaged with Docker and can be deployed to Kubernetes using the included Helm chart.

---

## Metrics

The exporter exposes the following metrics:

- `tls_cert_expiry_timestamp_seconds` – Certificate expiry time (Unix timestamp)
- `tls_cert_remaining_days` – Remaining days until expiry
- `tls_cert_probe_success` – Whether the TLS probe succeeded (1/0)
- `tls_cert_probe_duration_seconds` – Probe duration in seconds

---

## Configuration

Example config:

```yaml
targets:
  - https://www.google.com
  - https://www.github.com

scrape_interval: 30s
listen_address: ":2112"
