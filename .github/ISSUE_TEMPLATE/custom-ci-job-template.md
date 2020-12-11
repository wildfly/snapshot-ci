---
name: Custom CI Job Template
about: Template to for issues to trigger custom CI jobs
title: ''
labels: ''
assignees: ''

---

```
name: My component into WildFly
components:
  # Add as many components as you like here, adjusting name (of the repo), org and branch
  # If your component has dependencies set them up with component name and version property
  - name: my-component
    org: my-org
    branch: '0.0'
    mavenOpts: -DskipTests
  # components - end

  # Our target/main components. Adjust the dependencies to pull in the prior ones
  - name: wildfly-core
    org: wildfly
    branch: master
    dependencies:
      - name: my-component
        property: version.my.component
  - name: wildfly
    org: wildfly
    branch: master
    dependencies:
      - name: wildfly-core
        property: version.org.wildfly.core
```
