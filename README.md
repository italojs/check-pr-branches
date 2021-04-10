
# Check PR Branches
An action to check if I my PR branches is allowed to merge by branch's name

## Usage
**Case**: master branch only accept code/pr from develop

``` yml
name: pr-pipeline

on: pull_request

jobs:
  block-pr:
      name: check-pr-branches
      runs-on: ubuntu-latest
      steps:
        - uses: italojs/check-pr-branches@1.0.0
          with:
              when_base: master
              allow_only: develop
 ```

## Configuration
all args is required*

- **when_base**: when the base code is <branch_name> (we accept regex)
- **allow_only**: allow the merge if the compare branch is <branch_name> (we accept regex)

Example: 

only accept to merge into master when the `compare branch` matches with `release\/([0-9]).([0-9]).[0-9]` pattern
```yml
uses: italojs/check-pr-branches@1.0.0
        with:
            when_base: master
            allow_only: release\/([0-9]).([0-9]).[0-9]
```


