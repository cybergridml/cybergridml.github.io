---
title: Quick Setup
parent: Tutorials
nav_order: 2
---

This tutorial starts a CyberGridML application instance on your machine in a few minutes. The application and its PostgreSQL database both run in containers, so Java does not need to be installed on your host. The steps follow the [quickstart guide](https://github.com/cybergridml/cybergridapp-deployment/blob/main/quickstart.md) of the `cybergridapp-deployment` repository, with the step that is missing from it: getting the application JAR.

## Prerequisites

* [Podman](https://podman.io/) and either `podman compose` or `podman-compose`
* [Git](https://git-scm.com/)
* The `cybergridml-app-X.Y.Z.jar` file of the release you want to run (see step 2)

## 1. Get the deployment files

Clone the deployment repository and move into it:

```bash
git clone https://github.com/cybergridml/cybergridapp-deployment.git
cd cybergridapp-deployment
```

## 2. Download the application JAR

The application JAR is not stored in the deployment repository. You have to download it from the releases of the modeler:

1. Go to the [CyberGridML releases page](https://github.com/cybergridml/cybergrid-modeller/releases).
2. Open the release `X.Y.Z` you want to run.
3. In the **Assets** section, download `cybergridml-app-X.Y.Z.jar`.
4. Copy this file into the `cybergridapp-deployment` folder, next to the `Dockerfile`, and rename it `cybergridml-app.jar`. The `Dockerfile` copies the file under this exact name.

For example, on Linux or macOS, from the `cybergridapp-deployment` folder:

```bash
mv ~/Downloads/cybergridml-app-X.Y.Z.jar ./cybergridml-app.jar
```

Replace `X.Y.Z` with the version you downloaded, and adapt the path to the folder where your browser saved the file.

At this point, the project folder should look like this:

```text
.
├── cybergridml-app.jar
├── Dockerfile
├── compose.yaml
├── .env
└── data/
    └── postgres/
```

## 3. Create the environment file

Create a file named `.env` in the project folder with the following content:

```env
POSTGRES_USER=dbuser
POSTGRES_PASSWORD=dbpwd
POSTGRES_DB=cybergrid-db

APP_PORT=9090
DB_PORT=5433

POSTGRES_DATA_DIR=./data/postgres
APP_DATA_DIR=./data
```

The values above are examples. Change `POSTGRES_PASSWORD` before you use the instance for anything other than a local test.

## 4. Prepare the local data directory

Create the directory where PostgreSQL stores its data:

```bash
mkdir -p data/postgres
```

This directory should not be committed to Git. Make sure `.gitignore` contains the following entry:

```gitignore
data/
```

## 5. Start the application

From the project folder, run:

```bash
podman compose up -d --build
```

If `podman compose` is not available on your system, use `podman-compose` instead:

```bash
podman-compose up -d --build
```

This builds the application image, starts the PostgreSQL database, and starts the CyberGridML application. PostgreSQL data is stored in `data/postgres`.

## 6. Check that it runs

List the running containers:

```bash
podman ps
```

The containers `cybergrid-db` and `cybergrid-app` should both be listed as running. Then open the application in your browser:

```text
http://localhost:9090
```

## 7. Read the logs, stop, and clean up

Follow the application logs:

```bash
podman logs -f cybergrid-app
```

Follow the database logs:

```bash
podman logs -f cybergrid-db
```

Stop the containers without deleting the data:

```bash
podman compose down
```

Warning: the following command deletes the local PostgreSQL database files. Stop the containers first.

```bash
rm -rf data/postgres
```

## Troubleshooting

* **The image build fails on the `COPY` step**: the JAR is missing or has the wrong name. The file must be named `cybergridml-app.jar` and sit in the same folder as the `Dockerfile`.
* **Port 9090 or 5433 is already in use**: change `APP_PORT` or `DB_PORT` in `.env`, then start the application again.

Once the application runs, the [Example Model](example-models.md) tutorial shows how to test a model with a CyberGridML release.
