# Open Telemetry & Grafana



[Grafana Concepts and Basic Configuration by Craig Golightly](https://app.pluralsight.com/ilx/video-courses/grafana-concepts-basic-config/course-overview)  

---

[Grafana Cloud Full-stack observability - Grafana Labs](https://grafana.com/products/cloud/?src=ggl-s&mdm=cpc&camp=b-grafana-exac-emea&cnt=118483912276&trm=grafana&device=c&gad_source=1&gad_campaignid=12428334401&gbraid=0AAAAADkOfquXqX2tMtLoDWSfudbbR6QNB&gclid=CjwKCAiAmp3LBhAkEiwAJM2JUIvWkqKPi4SlaUwufHSlIXrN0qPLqnSurt_Z7PzJ5PIXkk90dMY3VBoChcYQAvD_BwE)  

[OpenTelemetry - High-quality, ubiquitous, and portable telemetry to enable effective observability](https://opentelemetry.io/)  
[OpenTelemetry: Observability with .NET and C#](https://app.pluralsight.com/ilx/video-courses/opentelemetry-observability-dot-net-c-sharp/course-overview)  

---

[Prometheus - Open source metrics and monitoring for your systems and services](https://prometheus.io/)  

Instrument, collect, store, and query your metrics for alerting, dashboarding, and other use cases.

[Grafana Tempo](https://grafana.com/docs/tempo/latest/#:~:text=Grafana%20Tempo%20is%20an%20open,data%20with%20logs%20and%20metrics.)  

Grafana Tempo is an open-source, easy-to-use, and high-scale distributed tracing backend. 
Tempo lets you search for traces, generate metrics from spans, and link your tracing data with logs and metrics.

[Grafana Loki](https://grafana.com/oss/loki/)  

Loki is a log aggregation system designed to store and query logs from all your applications and infrastructure.  

[Statsd](https://github.com/statsd/statsd)   

A network daemon that runs on the Node.js platform and listens for statistics, like counters and timers, 
sent over UDP or TCP and sends aggregates to one or more pluggable backend services (e.g., Graphite).

- Daemon: The StatsD server (daemon) receives these packets, aggregates them (e.g., sums counters, calculates averages for timers), and batches them.
- Protocol: Metrics are sent in a simple text format (e.g., users.login.success:1|c for a counter).
- Client Libraries: Developers use language-specific libraries (Python, Node.js, Java, Go, Ruby, etc.) to send metrics from their applications.
- Backend: Periodically (e.g., every 10 seconds), the daemon "flushes" the aggregated data to a configured backend service (Graphite, InfluxDB, Datadog, Splunk, etc.) for visualization. 

Common Backends & Variations for Statsd



[Graphite](https://graphite.io/)  

---