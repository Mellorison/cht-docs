---
title: "Setting Form Properties"
linkTitle: Form Properties
weight: 8
description: >
  Setting Form Properties
relatedContent: >
  apps/reference/forms/app/#formsappform_namepropertiesjson

---

The form properties file contains meta information related to the App form.

## Purpose of the Tutorial

This tutorial will take you through how to write the `<form_name>.properties.json` file.

You will be adding meta-data and context to an assessment workflow that allows Community Health Workers to conduct a health assessment for children under the age of 5.

## Brief Overview of Key Concepts

*[Form context]({{< ref "apps/reference/forms/app#formsappform_namepropertiesjson" >}})* defines when and where the form should be available in the app.

## Required Resources

You should have a [functioning CHT instance with `medic-conf` installed locally]({{< ref "apps/tutorials/local-setup" >}}) and a [project folder set up]({{< ref "apps/tutorials/local-setup#3-create-and-upload-a-blank-project" >}}) already and a [built assessment form]({{< ref "apps/tutorials/app-forms" >}}).

## Implementation Steps

Create a new file in the same folder as your `assessment.xlsx` file and name it `assessment.properties.json`.

### 1. Define the Form's Title

Edit the `assessment.properties.json` file and add a `title` key with the value corresponding to what you want your title to be.

```json
{
  "title": "Assessment"
}
```

### 2. Define the Form's Icon

Add a `resources` folder in your project folder and put your preferred icon for assessment in it. Name the icon file `icon-healthcare-assessment.png` if it is a `png` file or `icon-healthcare-assessment.svg` if it is an `svg` file.

Create a `resources.json` *file* in your project folder and add key/value pairs for your icon resources.

```json
{
  "icon-healthcare-assessment": "icon-healthcare-assessment.png"
}
```

Add an `icon` key in the `assessment.properties.json` file. Pick the key of the icon you require from the `resources.json` file and add it as the `icon` value.

```json
{
  "title": "Assessment",
  "icon": "icon-healthcare-assessment"
}
```

### 3. Define the Form's Context

Add a `context` key in the `assessment.properties.json` file. Add an object with `person`, `place` and `expression` keys. Add the boolean value `true` for the `person` key, the boolean value `false` for the `place` key and the expression `ageInYears(contact) < 5` for the `expression` key.

```json
{
  "title": "Assessment",
  "icon": "icon-healthcare-assessment",
  "context": {
        "person": true,
        "place": false,
        "expression": "ageInYears(contact) < 5"
    }
}
```

### 4. Upload the `<form_properties>.properties.json` File

Run the following command from the root folder to upload the `assessment.properties.json` file:

```zsh
medic-conf --url=https://<username>:<password>@localhost --accept-self-signed-certs upload-app-forms -- assessment
```

{{% alert title="Note" %}} Be sure to replace the values `<username>` and `<password>` with the actual username and password of your test instance. {{% /alert %}}
