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

# Install modules.
```bash
drush install -y admin_toolbar devel schemadotorg_help
```

# Install all Schema.org Blueprints modules.
```bash
drush pm-list --format=list | grep schemadotorg | xargs drush install -y
```
## Or For DDEV
```bash
ddev drush pm-list --format=list | grep schemadotorg | xargs ddev drush install -y
```

# Install Schema.org Blueprints Core modules.
```bash
drush pm-list --format=list --package='Schema.org Blueprints Cor' | xargs drush install -y
```
## Or For DDEV
```bash
ddev drush pm-list --format=list --package='Schema.org Blueprints Cor' | xargs ddev drush install -y
```

# Install Schema.org Blueprints Core modules.
```bash
drush pm-list --format=list --package='Schema.org Blueprints Cor' | xargs drush install -y
```
## Or For DDEV
```bash
ddev drush pm-list --format=list --package='Schema.org Blueprints Cor' | xargs ddev drush install -y
```
