# iot-things-v2-config

Kustomize-konfiguration för [`iot-things-v2`](../iot-things-v2).

```sh
kubectl kustomize .
```

Deploymenten förutsätter att installationsmiljön skapar ConfigMap
`iot-things-v2-cfg-cm` med följande filer:

- `authz.rego` (obligatorisk, tjänsten avslutar om den saknas)
- `things.csv` (obligatorisk, tjänsten avslutar om den saknas; tom fil med endast rubrikrad är giltig)
- `catalog-seed.json` (valfri katalogseed, saknad fil ger endast varning)

Till skillnad från v1 används ingen `config.yaml`.

Miljön behöver även tillföra RabbitMQ- och PostgreSQL-konfiguration samt
hemligheter. Applikationens variabler dokumenteras i
`../iot-things-v2/cmd/iot-things-v2/main.go`; utan `POSTGRES_HOST` används
minneslagring.

Image-digesten i `overlays/production/patches/image.yaml` är avsiktligt inte
uppdaterad till en v2-build ännu.
