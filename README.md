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

> [!NOTE]
> Note that directories in `sites/` named `default` and `settings` are ignored.
> The `default` directory is not necessary to set in most, if not all,
> circumstances in sites.php. The `settings` directory is conventionally used
> not as a site directory but as a location to store global settings files used
> by all sites.
