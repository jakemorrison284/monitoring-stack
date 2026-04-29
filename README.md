# monitoring-stack

Prometheus + Grafana for NovaPay.

## Installation Instructions

1. **Prerequisites**: Ensure you have the following installed on your machine:
   - Docker
   - Docker Compose

2. **Clone the Repository**:
   ```bash
   git clone https://github.com/jakemorrison284/monitoring-stack.git
   cd monitoring-stack
   ```

3. **Start the Monitoring Stack**:
   Run the following command to start Prometheus and Grafana:
   ```bash
   docker-compose up -d
   ```

4. **Access Grafana**:
   After starting the services, you can access Grafana at `http://localhost:3000`.
   - Default credentials: 
     - Username: `admin`
     - Password: `admin` (you will be prompted to change this on first login)

5. **Prometheus Access**:
   You can access Prometheus at `http://localhost:9090`.

## Usage Examples

### Setting Up Alerts
- Configure alerts in the `prometheus.yml` file located in the root directory.
- Example alert rule:
  ```yaml
  groups:
  - name: example
    rules:
    - alert: HighPaymentErrorRate
      expr: payment_error_rate > 0.01
      for: 5m
      labels:
        severity: critical
      annotations:
        summary: "High payment error rate detected"
        description: "Payment error rate has exceeded 1% for more than 5 minutes."
  ```

### Querying Metrics
- You can query metrics using Prometheus's expression browser at `http://localhost:9090/graph`.

## Alert thresholds
- payment_error_rate > 1% → P1
- p99_latency > 2s → P2
