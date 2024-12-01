# Custom Workflow Lab

## Introduction

In this lab you will customize the existing workflow to trigger when a change is made to the `src` folder on the `main` branch. You will also add steps to the workflow to use an action that greets Mona the Octocat.

> Duration: 10-15 minutes

## Instructions

1. Open the workflow file [custom-workflow.yml](/.github/workflows/custom-workflow.yml)
2. Edit the file and copy the following YAML content in the `on` section:

   ```YAML
     push:
       branches:
         - main
       paths:
         - 'src/**'
   ```

3. Commit the workflow changes into the `main` branch
4. Change a file inside the folder [src](/src)
5. Commit the changes into the `main` branch
6. Go to `Actions` and see the details of your running workflow

## Add steps to your workflow

1. Open the workflow file [custom-workflow.yml](/.github/workflows/custom-workflow.yml)
2. Edit the file and copy the following YAML content at the end of the file:

   ```YAML
     # This step uses GitHub's hello-world-javascript-action: https://github.com/actions/hello-world-javascript-action
   - name: Hello world
     uses: actions/hello-world-javascript-action@main
     with:
       who-to-greet: "Mona the Octocat"
     id: hello
   # This step prints an output (time) from the previous step's action.
   - name: Echo the greeting's time
     run: echo 'The time was ${{ steps.hello.outputs.time }}.'

   ```

3. Optional remove the `paths` to trigger the workflow on any push to main branch
4. Commit the changes into the `main` branch
5. Change a file inside the folder [src](/src) and commit the changes into the `main` branch
6. Go to `Actions` and see the details of your running workflow

## Summary

You have successfully customized the workflow to trigger when a change is made to the `src` folder on the `main` branch. You have also added steps to the workflow to use an action that greets Mona the Octocat.

## Additional Resources

- [Events that trigger workflows](https://docs.github.com/en/actions/using-workflows/events-that-trigger-workflows)
- [Adding an action to your workflow](https://docs.github.com/en/actions/learn-github-actions/finding-and-customizing-actions#adding-an-action-to-your-workflow)
