## Knative GitHub Actions and Workflows

These actions and workflows are used within the Knative project

The repo is organized as follows:

- [Reusable workflows](https://docs.github.com/en/actions/using-workflows/reusing-workflows) are under the `workflows` directory
 
  They can be used as follows:
  ```yaml
  on: [pull_request]

  jobs:
    job_name:
      steps:
      - uses: knative/actions/workflows/reusable-workflow.yml@main  
  ```

- [Composite actions](https://docs.github.com/en/actions/creating-actions/creating-a-composite-action) have their own unique folder the root of the repo

  They can be used as follows:
  ```yaml
  on: [pull_request]

  jobs:
    job_name:
      steps:
      - uses: knative/actions/some-action@main
  ```

## Contributing to Knative

For a list of all help wanted issues in Knative, look [here](https://clotributor.dev/search?project=knative&page=1)
