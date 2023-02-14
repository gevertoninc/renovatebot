# renovatebot

Scans selected repositories, updates their dependency versions, and opens pull requests with the updates

List of parameters that can be changed in `config.js`: https://docs.renovatebot.com/renovate-schema.json. This is useful to know which fields can be added to the file, since the official doc is a bit confusing/outdated

## How to add to your pipeline

1. Create a new repository
2. Copy and paste this repository content
3. Create a PAT in GitHub without any access scopes (optional)
4. Create a PAT in Azure with the access scopes `code (read and write)` and `packaging (read)`
5. Create a library called `renovatebot` (or create another library and change `azure-pipelines.yml`)
6. Add the Azure PAT to the `RENOVATE_TOKEN` environment variable in the created library (or create another variable and change `config.js`)
7. Add the GitHub PAT to the `GITHUB_COM_TOKEN` environment variable in the created library (or create another variable and change `azure-pipelines.yml`)
8. Change the frequency of the Cron job execution according to your needs in `azure-pipelines.yml`
9. Change any configuration you want in `config.js`
10. Create a new pipeline with default settings

## How to add to your repository/repositories

1. Add the project/projects and repository/repositories you want to update to the `repositories` field in `config.js`
2. Subsequent pipeline runs will create PRs with the dependency updates

## Run locally

1. Create a `.env` file based on `.env.example`
2. Replace `GITHUB_COM_TOKEN` with a GitHub PAT without any access scopes (optional)
3. Replace `RENOVATE_TOKEN` with an Azure PAT with the access scopes `code (read and write)` and `packaging (read)`
4. Run `docker-compose up`
