# API Testing with Postman and GitHub Actions

This repository contains Postman collections for API testing, along with a GitHub Actions workflow to automate these tests and generate detailed reports.

## Running Tests Locally

To run the tests locally and generate a report:

1. Start the server:

   ```bash
   cp mockApi/db_back_up.yaml mockApi/db_stage.yaml
   npx yaml-server --hotReload=off --autoStart=off --port 3000 --database ./mockApi/db_stage.yaml
   ```

2. Run the Postman collection with the `htmlextra` reporter:

   ```bash
   newman run ./path/to/your/store.collection.json \
     --reporters cli,htmlextra \
     --reporter-htmlextra-export newman/report.html
   ```

## Automated Testing with GitHub Actions

When you push to the `main` branch, GitHub Actions will automatically:

1. Start the server.
2. Run the Postman collection.
3. Generate an HTML report.
4. Publish the report to GitHub Pages.

## Viewing Reports

After the tests are run, you can view the report at:

```
https://<your-username>.github.io/<your-repo-name>/report.html
```
