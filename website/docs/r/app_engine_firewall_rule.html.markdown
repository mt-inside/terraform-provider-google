---
# ----------------------------------------------------------------------------
#
#     ***     AUTO GENERATED CODE    ***    AUTO GENERATED CODE     ***
#
# ----------------------------------------------------------------------------
#
#     This file is automatically generated by Magic Modules and manual
#     changes will be clobbered when the file is regenerated.
#
#     Please read more about how to change this file in
#     .github/CONTRIBUTING.md.
#
# ----------------------------------------------------------------------------
layout: "google"
page_title: "Google: google_app_engine_firewall_rule"
sidebar_current: "docs-google-app-engine-firewall-rule"
description: |-
  A single firewall rule that is evaluated against incoming traffic
  and provides an action to take on matched requests.
---

# google\_app\_engine\_firewall\_rule

A single firewall rule that is evaluated against incoming traffic
and provides an action to take on matched requests.


To get more information about FirewallRule, see:

* [API documentation](https://cloud.google.com/appengine/docs/admin-api/reference/rest/v1/apps.firewall.ingressRules)
* How-to Guides
    * [Official Documentation](https://cloud.google.com/appengine/docs/standard/python/creating-firewalls#creating_firewall_rules)

<div class = "oics-button" style="float: right; margin: 0 0 -15px">
  <a href="https://console.cloud.google.com/cloudshell/open?cloudshell_git_repo=https%3A%2F%2Fgithub.com%2Fterraform-google-modules%2Fdocs-examples.git&cloudshell_working_dir=app_engine_firewall_rule_basic&cloudshell_image=gcr.io%2Fgraphite-cloud-shell-images%2Fterraform%3Alatest&open_in_editor=main.tf&cloudshell_print=.%2Fmotd&cloudshell_tutorial=.%2Ftutorial.md" target="_blank">
    <img alt="Open in Cloud Shell" src="//gstatic.com/cloudssh/images/open-btn.svg" style="max-height: 44px; margin: 32px auto; max-width: 100%;">
  </a>
</div>
## Example Usage - App Engine Firewall Rule Basic


```hcl
resource "google_project" "my_project" {
  name       = "tf-test-project"
  project_id = "test-project"
  org_id     = "123456789"
}

resource "google_app_engine_application" "app" {
  project     = "${google_project.my_project.project_id}"
  location_id = "us-central"
}

resource "google_app_engine_firewall_rule" "rule" {
  project = "${google_app_engine_application.app.project}"
  priority = 1000
  action = "ALLOW"
  source_range = "*"
}
```

## Argument Reference

The following arguments are supported:


* `source_range` -
  (Required)
  IP address or range, defined using CIDR notation, of requests that this rule applies to.

* `action` -
  (Required)
  The action to take if this rule matches.


- - -


* `description` -
  (Optional)
  An optional string description of this rule.

* `priority` -
  (Optional)
  A positive integer that defines the order of rule evaluation.
  Rules with the lowest priority are evaluated first.
  A default rule at priority Int32.MaxValue matches all IPv4 and
  IPv6 traffic when no previous rule matches. Only the action of
  this rule can be modified by the user.
* `project` - (Optional) The ID of the project in which the resource belongs.
    If it is not provided, the provider project is used.



## Timeouts

This resource provides the following
[Timeouts](/docs/configuration/resources.html#timeouts) configuration options:

- `create` - Default is 4 minutes.
- `update` - Default is 4 minutes.
- `delete` - Default is 4 minutes.

## Import

FirewallRule can be imported using any of these accepted formats:

```
$ terraform import google_app_engine_firewall_rule.default {{project}}/{{priority}}
$ terraform import google_app_engine_firewall_rule.default {{priority}}
```

-> If you're importing a resource with beta features, make sure to include `-provider=google-beta`
as an argument so that Terraform uses the correct provider to import your resource.
