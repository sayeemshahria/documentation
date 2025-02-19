---
title: Migrate a Drupal Site from Another Platform
subtitle: Troubleshooting
description: Troubleshoot common issues when migrating.
cms: "Drupal"
tags: [code, launch, migrate, site, updates]
contributors: [wordsmither]
layout: guide
showtoc: true
permalink: docs/guides/drupal-unhosted/troubleshooting
anchorid: troubleshooting
editpath: drupal/drupal-unhosted/15-troubleshooting.md
contenttype: [guide]
categories: [migrate]
newcms: [drupal9, drupal8, drupal10, drupal]
audience: [development]
product: [--]
integration: [--]
reviewed: "2022-12-13"
---

This section covers common troubleshooting scenarios when migrating a Drupal site from another host to Pantheon's platform.

## Provided host name not valid

If you receive the error message "The provided host name is not valid for this server.", then update your `settings.php` file with a trusted host setting. Refer to the [Trusted Host Setting](/guides/php/settings-php#trusted-host-setting) documentation for more information.

<Partial file="drupal/troubleshooting-drush.md" />

<Partial file="drupal/troubleshooting-general.md" />

