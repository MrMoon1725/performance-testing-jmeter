# Performance Testing Suite — Apache JMeter

Performance test plan built with **Apache JMeter 5.6** covering **Load**, **Stress**, and **Spike** scenarios with configurable host/protocol properties, HTTP 200 assertions, and automated HTML Dashboard Report generation.

---

## Scenarios Included (`test_plans/ecommerce_load_stress_spike.jmx`)

| Thread Group | Virtual Users | Ramp-Up | Loops | Purpose |
| :--- | :--- | :--- | :--- | :--- |
| `01 - Load Test` | 20 | 30s | 3 | Validate baseline SLA under normal expected traffic |
| `02 - Stress Test` | 50 | 30s | 5 | Measure throughput saturation and latency degradation |
| `03 - Spike Test` | 100 | 5s | 2 | Verify system stability under sudden traffic bursts |

---

## Target SLAs & Metrics Analyzed

- **p95 Latency:** `< 800 ms` under Load, `< 1500 ms` under Stress
- **Error Rate:** `< 1.0%`
- **Throughput:** Requests/sec sustained without connection timeouts

---

## Running via JMeter CLI (Non-GUI Mode)

```bash
jmeter -n -t test_plans/ecommerce_load_stress_spike.jmx \
  -Jhost=restful-booker.herokuapp.com -Jprotocol=https \
  -l results/run_results.jtl \
  -e -o reports/dashboard
```
