I spent some time testing OLake by building a small Postgres -> Iceberg pipeline.

I started with a simple PostgreSQL `orders` table, used OLake to sync it into Apache Iceberg through a REST catalog, and then queried the final table using Spark SQL.

The part I liked most was seeing how the pieces actually connect. Postgres was the source, OLake handled the ingestion, Iceberg handled the table format, MinIO acted as the object store, and Spark queried the result.

I did run into one Docker networking issue where OLake could not resolve the Iceberg REST container directly, so I ended up using `host.docker.internal` instead.

I wrote up the setup and the issue I ran into in the README.

Repo: [GitHub link]