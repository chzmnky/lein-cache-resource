# Leiningen Cache Resource
A [Concourse.ci](http://concourse.ci/) resource for caching Leiningen dependencies.

The approach and code is based on [gradle-cache-resource](https://github.com/projectfalcon/gradle-cache-resource).

## Source Configuration
The resource uses the [git-resource](https://github.com/concourse/git-resource) internally, so any of
the git-resource parameters can be used. It is advisable to use the `paths` parameter to only listen
to changes of the `project.clj` of the Leiningen project.

## Behavior
### `check`: Check for git repo changes
Simply forwards the control to the `check` script of the git-resource to check for any changes in
the source repository.

It is advisable to track changes to the `project.clj` only, since that describes the project dependencies.

### `in`: Cache dependencies
The source repository is first cloned using the git-resource and then dependencies are cached
with `lein deps`.

### `out`: Not used
