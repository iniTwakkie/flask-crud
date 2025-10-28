# Flask-crud app

## Try Out Development Containers: Python
[![Open in Dev Containers](https://img.shields.io/static/v1?label=Dev%20Containers&message=Open&color=blue&logo=visualstudiocode)](https://vscode.dev/redirect?url=vscode://ms-vscode-remote.remote-containers/cloneInVolume?url=https://github.com/buildwithdan/flask-crud)

![visitors](https://visitor-badge.laobi.icu/badge?page_id=buildwithdan.MandalorianBounty)  
<!-- [![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https://github.com/buildwithdan/MandalorianBounty) -->

A simple Flask Python CRUD app to understand how the basics of CRUD works with a database.   

# Stack

- **Framework**: [Flask](https://flask.palletsprojects.com/en/2.2.x/)
- **Database**: [Postgres](https://www.postgresql.org/)
- **Authentication**: not applicable
- **Deployment**: [Vercel](https://vercel.com)
- **Styling**: [Bootstrap](https://getbootstrap.com/)
- **Analytics**: not applicable

## Running Locally

```bash Docker Compose Yml
services:
  app:
    image: buildwithdan/flask-crud:latest
    restart: unless-stopped
    ports:
      - "5100:5000"
    depends_on:
      db:
        condition: service_healthy

  db:
    image: postgres:latest
    restart: unless-stopped
    environment:
      POSTGRES_USER: postgres
      POSTGRES_PASSWORD: postgres
      POSTGRES_DB: postgres
    volumes:
      - /srv/docker/flask-crud/data:/var/lib/postgresql
    ports:
      - "5432:5432"
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U postgres"]
      interval: 10s
      timeout: 5s
      retries: 5

```

This application requires the latest python and flask to be installed.

```bash
git clone https://github.com/buildwithdan/flask-crud
cd flask-crud
flask --debug --app api.app run
```
