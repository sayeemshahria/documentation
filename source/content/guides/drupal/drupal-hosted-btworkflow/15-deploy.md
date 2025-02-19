---
title: Upgrade a Drupal Site Created With the Pantheon Dashboard to the Latest Version of Drupal + Build Tools
subtitle: Deploy
description: 
cms: "Drupal"
tags: [code, launch, migrate, site, updates]
contributors: [wordsmither]
layout: guide
showtoc: false
permalink: docs/guides/drupal-hosted-btworkflow/deploy
anchorid: deploy
editpath: drupal/drupal-hosted-btworkflow/15-deploy.md
reviewed: "2022-12-12"
contenttype: [guide]
categories: [--]
newcms: [drupal9, drupal10]
audience: [development]
product: [dashboard, terminus]
integration: [--]
---

You should now have all three of the major components of your site imported into Pantheon. Clear your caches on the the Pantheon Dashboard, or with Terminus using the following command:

  ```bash{promptUser: user}
  terminus drush $SITE.dev cr
  ```

Review the site, then proceed to launch using the [Pantheon Relaunch](/relaunch) documentation.