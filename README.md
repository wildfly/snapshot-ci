# WildFly Snapshot CI

This allows you to test how your feature branches integrate into WildFly
without doing releases of each component.

To do this, open an issue following the syntax defined in the 
Overbård Multi Repo CI [documentation](https://github.com/overbaard/multi-repo-ci).
This will trigger a GitHub Actions Workflow run, which generates a fuller workflow
Yaml file. This generated Yaml file in turn is pushed to a branch, triggering 
another, longer workflow run. 

Tests from the WildFly and WildFly Core testsuites are run in parallel, so the
whole run should be reasonably quick.

You can check the progress of the workflow run in the [Actions](../../actions) pane
of this repository. They will also leave a comment and label your trigger issue
indicating failure or success. If your workflow run fails, the logs for the 
affected tests will be attached as an artifact to the workflow run.

To rerun the workflow, you presently need to edit the issue you created to
trigger the workflow run in the first place.

The generated workflow Yaml is complex, so if your workflow run has failing tests,
and those tests are not reproducible locally
you can dig into those by creating an empty repository (or a clone of this one, 
but it is not necessary) and copying [reproducer-template.yml](reproducer-template.yml)
into it. Adjust as indicated in the comments in the yaml, push and you
will get a quicker run focussing on the problem. It also contains some information
about how to get SSH access to the VM running the workflow.

Report any issues in the issues section of this repository.

Enjoy :)
