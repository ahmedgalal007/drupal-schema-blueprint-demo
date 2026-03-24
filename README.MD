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

# Enable additional Core and Contrib modules.
```bash
drush en -y navigation media_library devel_generate
```
## Or For DDEV
```bash
# For DDEV
ddev drush en -y navigation media_library devel_generate

```

# Add Links to the Module Recipes in the Project Root.
```bash
  ln -sf <my-project-root-path>/web/core/recipes/audio_media_type <my-project-root-path>/recipes/schemadotorg_recipes/audio_media_type;\
  ln -sf <my-project-root-path>/web/core/recipes/document_media_type <my-project-root-path>/recipes/schemadotorg_recipes/document_media_type;\
  ln -sf <my-project-root-path>/web/core/recipes/image_media_type <my-project-root-path>/recipes/schemadotorg_recipes/image_media_type;\
  ln -sf <my-project-root-path>/web/core/recipes/local_video_media_type <my-project-root-path>/recipes/schemadotorg_recipes/local_video_media_type;\
  ln -sf <my-project-root-path>/web/core/recipes/remote_video_type <my-project-root-path>/recipes/schemadotorg_recipes/remote_video_media_type;\
  ln -sf <my-project-root-path>/web/core/recipes/editorial_media_type <my-project-root-path>/recipes/schemadotorg_recipes/editorial_media_type;
```
### <span style="color:red"> (Optional) Dont use it.</span>
```diff
# Apply the schema.org JSON-LD recipe which enables Core and Contributed modules With JSON-LD support.
- ddev deush -y recipe ../recipes/schemadotorg_recipes/schemadotorg_recipe_jsonld; ddev drush cr; ddev drush cr;
```

### <span style="color:green"> instead use Module "Schema.org Mapping Sets" to generate the schema you desire.</span>
