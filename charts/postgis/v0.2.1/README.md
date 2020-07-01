# Postgis

This is Kartoza's Postgis Rancher charts

Postgis is an extension of PostgreSQL database with added support for Spatial Data

# How to Use

For helm:

```bash
helm install release-name kartoza/postgis
```

# Intro

This chart bootstrap a PostgreSQL database with Postgis installed in its main database.
It behaves like a PostgreSQL database, but with Postgis extension installed in its database.

# What it can do

The default install uses kartoza/postgis image, which can do the following:

- Generate superuser roles at startup
- Generate new database at startup if volume empty
- Generate one or more database with Postgis installed
- Accept locale and collations settings for the database
- Default TLS enabled
- GDAL Driver installed
- Support out-of-db rasters
- Enable multiple extensions

# Parameters

| Parameter | Description |
|---|---|
| image.registry | Docker image registry |
| image.repository | Docker image repository |
| image.tag | Docker image tag |
| image.pullPolicy | Docker image pull policy |
| postgresqlUsername | PostgreSQL superuser name |
| postgresqlPassword | PostgreSQL superuser password. If leave empty, it will be autogenerated every update. |
| postgresqlDatabase | Default main PostgreSQL database |
| postgresqlDataDir | Location in the pods of where the PostgreSQL Data Directory is |
| existingSecret | [tpl string] Provide secret name or tpl expression for where the secret is |
| extraPodEnv | [tpl string] Provide extra environment that will be passed into pods. Useful for non default image. |
| extraSecret | [tpl string] Provide extra secret that will be included in the pods. Useful for non default image. |
| extraConfigMap: | [tpl string] Provide extra config map that will be included in the pods. Useful for non default image. |
| extraVolumeMounts | [tpl string] Provide extra volume mounts declaration that will be included in the pods. Useful if you want to mount extra things. |
| extraVolume | [tpl string] Configuration pair with extraVolumeMounts. Declare which volume to mount in the pods. |
| persistence.enabled | Default to true. If set, it will make a volume claim |
| persistence.existingClaim | Default to false. If set, it will use an existing claim name provided |
| persistence.mountPath | The path where the volume will be in the pods |
| persistence.subPath | The path inside the the volume to mount to. Useful if you want to reuse the same volume but mount the subpath for different services. |
| persistence.size | Size of the volume to store PostgreSQL Data Dir |
| persistence.accessModes | Access mode of the volume. Normally ReadWriteOnce because PostgreSQL is stateful |
