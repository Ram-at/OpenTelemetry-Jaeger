# OpenTelemetry-Jaeger
How to use them

Jaeger lab


kubectl apply -f 01-otel-jaeger.yaml
kubectl get pods -A -w
# open http://<node-ip>:30686 → Service: frontend → Find Traces

Switch to the Tempo lab. Delete the first lab, because both use the same namespaces and ports:


kubectl delete -f 01-otel-jaeger.yaml
kubectl apply -f 02-otel-tempo.yaml
# open http://<node-ip>:30300 → Explore → Tempo → Search → Service Name = frontend
# TraceQL: { resource.service.name = "backend" && status = error }

Metrics and logs add-on. This needs the Tempo file running, because Grafana comes from there:


kubectl apply -f 03-metrics-logs-addon.yaml