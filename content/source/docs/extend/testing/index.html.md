---
layout: "extend"
page_title: "Home - Extending Terraform"
sidebar_current: "docs-extend-testing"
description: |-
  Extending Terraform is a section for content dedicated to developing Plugins
  to extend Terraform's core offering.
---

# Testing Terraform Plugins

Here we cover information needed to write successful tests for Terraform
Plugins. Tests are a vital part of the Terraform ecosystem, verifying we can
deliver on our mission to safely and predictably create, change, and improve
infrastructure. Documentation for Terraform tests is broken into categories
briefly described below. Each category has more detailed information by clicking
on the matching item in the left navigation. 

## Acceptance Tests 

In order to
deliver on our promise to be safe and predictable, we need to be able to easily
and routinely verify that Terraform Plugins produce the expected outcome. The
most common usage of an acceptance test is in Terraform Providers, where each
Resource is tested with configuration files and the resulting infrastructure is
verified. Terraform includes a framework for constructing acceptance tests that
imitate the execution of one or more steps of applying one or more configuration
files, allowing multiple scenarios to be tested.

It’s important to reiterate that acceptance tests in resources *create actual
cloud infrastructure*, with possible expenses incurred, and are the
responsibility of the user running the tests. Creating real infrastructure in
tests verifies the described behavior of Terraform Plugins in real world use
cases against the actual APIs,  and verifies both local state and remote values
match. Acceptance tests require a network connection and often require
credentials to access an account for the given API. When writing and testing
plugins, **it is highly recommended to use an account dedicated to testing, to
ensure no infrastructure is created in error in any environment that cannot be
completely and safely destroyed.**

HashiCorp runs nightly acceptance tests of providers found in the [Terraform
Providers GitHub Organization](https://github.com/terraform-providers) to ensure
each Provider is working correctly.

For a given plugin, Acceptance Tests can be run from the root of the project by
using a common make task:

```shell
$ make testacc 
```

## Unit Tests

Testing plugin code in small, isolated units is distinct from Acceptance Tests,
and does not requires network connections. Unit tests are commonly used for
testing helper methods that expand or flatten API response data into data
structures for storage into state by Terraform. 

For a given plugin, Unit Tests can be run from the root of the project by using
a common make task:

```shell
$ make test
```

## Testing API

What is testing api section

## Test Patterns

What is test patterns


## Next Steps

See the navigation on the left of this page for documentation and guides on
writing tests for Terraform Plugins. 