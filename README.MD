# Create Drupal 11.x.
```bash
composer create-project drupal/recommended-project <my-site-name-dir>
cd my-site-name-dir
```

# Change minimum stability to dev.
```bash
composer config minimum-stability dev
```

# Require Packages.
```bash
composer require drush/drush\
  drupal/admin_toolbar\
  drupal/devel\
  drupal/schemadotorg\
  wikimedia/composer-merge-plugin;
```

# Add the merge-plugin settings to extras.
### ``` in the composer.json
```json lines
 {
  ...
  "extras": {
    ...
    "merge-plugin": {
      "include": [
        "web/modules/contrib/schemadotorg/composer.libraries.json"
      ],
      "merge-extra": true,
      "merge-extra-deep": true
    }
  }
}
```

# Run composer update
```bash
composer update
```
