# WordPress VIP Plugins Hub
Central hub for reusable workflows and similarly common files for WordPress VIP plugins.

This repository contains:

- Reusable workflows that can apply to all of the WordPress VIP plugins, such as running PHPUnit or Behat tests, or PHPCS.
- A collection of files that individual plugin repositories should have, such as `.editorconfig`, or GitHub Workflow files that reference the reusable workflow files.
- A synchronization workflow that runs automatically to sync the colletion of files down to the individual plugin repos.

## Why?

Previously, workflows across 10+ repositories would all need updating when a new version of PHP, or GitHub Action was available.

Having the common workflows in one location means that they can be updated far more easily, and the repos have a consistency that they would otherwise be missing. The process of syncing the standalone files, such as "local" workflows, also avoids having to update individual repositories to get them using the centralized code.

## Won't things break if a plugin isn't using a feature?

Hopefully not! As an example, not all of the WordPress VIP plugins use Behat for functional tests - but the reusable workflows include checks to see if the individual repo has some key config files (such as `composer.json` and `behat.yml`), and the workflow won't run if they aren't found. Repeat for `.phpcs.xml.dist`, `phpunit.xml.dist` and so on. 

## How do I install this package?

You don't - there's nothing to install, and it's only used to communicate with other repositories.

## How are other plugin repositories added into the sync process?

Two steps are needed:

- Add the bot account with Write access to the new plugin repository.
- Add the name of the repository to the list of targets in the sync workflow.

## How do I add new files to be synced down?

- Add them to this repository in the file path that you want them in the plugin repositories.
- Make sure that any reusable workflows have defensive checks so that they don't break on repositories that aren't using a feature/tool.
- Add the file name(s) to the sync workflow.

## Who came up with this idea?

The WP-CLI organization has a central [set of resusable workflows](https://github.com/wp-cli/.github/tree/main/.github/workflows) and synchronization workflows, so all credit goes to the WP-CLI maintainers and whoever they got the idea from.
