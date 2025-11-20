# HelloDotnetApp


Minimal .NET app containerized, pushed to GHCR by GitHub Actions, deployed on Render.

## How it works
- GitHub Actions builds Docker image from `MyApp/Dockerfile`
- Workflow pushes `ghcr.io/<owner>/<repo>:latest` and `:<sha>` to GHCR
- Render pulls the image from GHCR and runs it on port 8080

## Local test
1. Build:
   docker build -t ghcr.io/<owner>/<repo>:localtest -f MyApp/Dockerfile MyApp
2. Run:
   docker run -p 8080:8080 ghcr.io/<owner>/<repo>:localtest
3. Visit: http://localhost:8080/

## CI/CD
Push to `main` to trigger `.github/workflows/ci-cd.yml` which builds and pushes to GHCR.
This repo deals with Docker image and Render deploy
