---
title: Convert a Standard Drupal Site to a Composer Managed Site
description: Upgrade a standard Drupal site, by converting it to a Composer-managed Drupal site on the new Integrated Composer framework. 
type: guide
permalink: docs/guides/:basename
tags: [composer, site, workflow]
contributors: [dustinleblanc, greg-1-anderson, stovak]
reviewed: "2022-12-12"
contenttype: [doc]
categories: [optimize]
newcms: [drupal8]
audience: [development]
product: [--]
integration: [--]
---

In this guide, we'll convert a standard Drupal site to use Composer to manage deployments and dependencies, then switch from `drops-8` to the new Integrated Composer `drupal-composer-managed` upstream while remaining on the current version of Drupal.

During this process, you will create a new branch based on the Git history of the new upstream.  You'll then re-add the contrib and custom code for your site to the new branch, and test it on a Multidev environment.  When everything is working correctly in the Multidev environment, you'll deploy the changes to the Dev environment by replacing your site's master branch with the new branch you've created.  Finally, after testing and confirming everything looks good, you'll use Terminus to switch the site over to the new upstream.

<Partial file="drupal/see-landing.md" />

## Overview

Drupal sites on Pantheon have [Integrated Composer](/guides/integrated-composer) built-in to manage site dependencies.

The goals of this conversion are:

1. Remove dependencies that Composer will manage from the existing Drupal site's Git repository, and have Composer manage those dependencies instead.

1. Switch to the `drupal-composer-managed` Integrated Composer upstream.

The `drupal-composer-managed` Integrated Composer upstream works with all versions of Drupal, and following the `drupal-composer-managed` upstream will help keep your site up to date with any general configuration changes recommended by Pantheon.

Add Drupal core dependency instructions to `drupal/core-recommended`, to keep the site on the current version of Drupal until you are ready to upgrade to the latest version of Drupal.

## Will This Guide Work for Your Site?

<Partial file="drupal/upgrade-site-requirements.md" />

## Before You Begin

- This guide is written for users with access to Pantheon's [Multidev](/guides/multidev) feature. Pantheon support is not available to users who avoid the Multidev steps.

- The site owner should ensure the trusted host setting is up-to-date. Refer to the [Trusted Host Setting](/guides/php/settings-php#trusted-host-setting) documentation for more information.

<Alert title="Note" type="info" >
  
The steps in this process migrate a site, so the new site will no longer maintain its existing commit history.

</Alert>

## Prepare the Local Environment

<Partial file="drupal/prepare-local-environment-no-clone.md" />

## Apply All Available Upstream Updates

<Partial file="drupal-apply-upstream-updates.md" />

## Add the Integrated Composer Upstream in a New Local Branch

<Partial file="drupal-8-convert-to-composer.md" />

### Troubleshooting: Provided host name not valid

If you receive the error message "The provided host name is not valid for this server.", then update your `settings.php` file with a trusted host setting. Refer to the [Trusted Host Setting](/guides/php/settings-php#trusted-host-setting) documentation for more information.

## Change Upstreams

Your Pantheon site is now set up to use the the latest version of Drupal Integrated Composer upstream. To continue tracking additional changes to the Pantheon upstream, change the upstream your site is tracking with Composer:

```bash{promptUser:user}
terminus site:upstream:set $SITE drupal-composer-managed
```

Following the `drupal-composer-managed` upstream will help keep your site up to date with any general configuration changes recommended by Pantheon. The dependency you added above on `drupal/core-recommended` will keep you on the current version of Drupal until you are ready to upgrade to the latest version.

## Working With Dependency Versions

<Partial file="composer-updating.md" />

## More Resources

- [Composer Fundamentals and Workflows](/guides/composer)

- [WordPress with Composer on Pantheon](/guides/wordpress-composer)
