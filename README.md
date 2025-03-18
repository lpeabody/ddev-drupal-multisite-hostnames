# DDEV Drupal Multisite Hostnames

This addon for Drupal projects creates a `$sites` entry for each multisite
directory in the project. The entry is based on the name of the multisite
directory and the DDEV project name.

For example, if your project name is `my-ddev-project`, and you have two
multisite directories:

- default
- other_site

Then the `$sites` array will look like the following:

```php
$sites = [
  'other-site-my-ddev-project.ddev.site' => 'other_site',
];
```

## Installation

```bash
ddev add-on get lpeabody/ddev-drupal-multisite-hostnames
```

- `drupal_multisite/sites.ddev_multisite.php` is copied to `sites/sites.ddev_multisite.php`
- A command `multisite-start` is added to `.ddev/commands/host/multisite-start`

## Usage

In order to make DDEV aware of the hostnames, use `ddev multisite-start` instead
of `ddev start`.

1. `ddev multisite-start`
2. `ddev status` and confirm that there are URLs listed for your multisite
   directories.

> [!IMPORTANT]
> Every time you add a new multisite directory, you will need to re-run
> `ddev multisite-start` in order to update the hostnames listed in
> `.ddev/config.drupal_multisite_hosts.yaml` and apply the changes to your
> DDEV environment. Run `ddev status` afterward to confirm the new URL
> for the multisite(s) is listed.

> [!NOTE]
> Site directories named `default` and `settings` are ignored.
> The `default` directory is not necessary to set in most, if not all,
> circumstances in sites.php. The `settings` directory is conventionally used
> not as a site directory but as a location to store global settings files used
> by all sites.


### Customizing the hostname pattern

You can manually edit the `sites/sites.ddev_multisite.php` file and the
`multisite-start` command to customize the hostname pattern. When you update
the addon you might have to reapply your changes.
