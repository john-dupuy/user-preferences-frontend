[![Build Status](https://travis-ci.org/RedHatInsights/user-preferences-frontend.svg?branch=master)](https://travis-ci.org/RedHatInsights/user-preferences-frontend)

# user-preferences-frontend

This application is for forms for users to change their preferences. If you want to be part of this application please open PR and update `src/config.json`. Each user preferences page uses this config and it will ayutomatically fetch new data driven form schemas based on it.

## Data driven forms

We rely heavily on library called [Data driven forms](https://data-driven-forms.org/), where we use schema to render components in form. Please go to their documentation if you want to enable new user preferences for your application.

## Expected pahts

In order to properly deliver DDF schema please expose the schema on URL `/api/${appName}/v1/user-config/${prefType}` where appName and prefType comes from `config.json`.

## Custom components

We have designed a few custom components to be used when working with data driven forms to properly show some information on screen.

* `DescriptiveCheckbox` this component is for displaing checkbox with title and description.
    - `descriptiveCheckbox` - component name to be used in DDF schema
    - `label` - will be shown as main title
    - `description` - will be shown under `label`
    - `isDanger` - to show title in danger color

## Hide form parts

If your application should be hidden behind some permission checker (similiar to [cloud-services-config#permissions](https://github.com/RedHatInsights/cloud-services-config/tree/ci-beta#permissionsmethod)) you can add `permissions` field to your application in `config.json`. It can either be object with method and list of arguments, or array with method and list of arguments.

The list of all methods can be found [insights-chrome#permissions](https://github.com/RedHatInsights/insights-chrome#permissions)

```JSON
{
    "email-preference": {
        ...
        "example": {
          "title": "Example",
          "permissions": {
              "method": "hasPermissions",
              "args": [
                  ["app:action:create"]
              ]
          }
        },
    }
}
```
