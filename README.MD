# Create Drupal 11.x.
```bash
composer create-project drupal/recommended-project <my-site-name-dir>
cd my-site-name-dir
```

################## <span style="color:red;">Or For DDEV</span> #####################
```bash
mkdir my-drupal-site && cd my-drupal-site
ddev config --project-type=drupal11 --docroot=web
## Start DDEV (this may take a minute):
ddev start

## Install Drupal via Composer:
ddev composer create-project drupal/recommended-project
ddev composer require drush/drush

## Run Drupal installation and launch:
ddev drush site:install --account-name=admin --account-pass=admin -y
ddev launch
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
  drupal/schemadotorg:^1.0@alpha\
  wikimedia/composer-merge-plugin;
```

# Add the merge-plugin settings to extras.
### ``` in the composer.json
```json lines
 {
  //...
  "extras": {
    //...
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

## Or For DDEV
ddev drush pm-list --format=list | grep schemadotorg | xargs ddev drush install -y
```


# Install Schema.org Blueprints Core modules.
```bash
drush pm-list --format=list --package='Schema.org Blueprints Cor' | xargs drush install -y

## Or For DDEV
ddev drush pm-list --format=list --package='Schema.org Blueprints Cor' | xargs ddev drush install -y
```

# Install Schema.org Blueprints Core modules.
```bash
drush pm-list --format=list --package='Schema.org Blueprints Cor' | xargs drush install -y

## Or For DDEV
ddev drush pm-list --format=list --package='Schema.org Blueprints Cor' | xargs ddev drush install -y
```

# UnInstall Those Schema.org Blueprints modules.
```bash
drush pmu schemadotorg_descriptions  schemadotorg_content_model_documentation

## Or For DDEV
ddev drush pmu schemadotorg_descriptions  schemadotorg_content_model_documentation
```


# Enable additional Core and Contrib modules.
```bash
drush en -y media_library devel_generate

## Or For DDEV
ddev drush en -y media_library devel_generate

```

# Add Links to the Module Recipes in the Project Root.
```bash
  ln -sf <my-project-root-path>/web/core/recipes/audio_media_type <my-project-root-path>/recipes/schemadotorg_recipes/audio_media_type;\
  ln -sf <my-project-root-path>/web/core/recipes/document_media_type <my-project-root-path>/recipes/schemadotorg_recipes/document_media_type;\
  ln -sf <my-project-root-path>/web/core/recipes/image_media_type <my-project-root-path>/recipes/schemadotorg_recipes/image_media_type;\
  ln -sf <my-project-root-path>/web/core/recipes/local_video_media_type <my-project-root-path>/recipes/schemadotorg_recipes/local_video_media_type;\
  ln -sf <my-project-root-path>/web/core/recipes/remote_video_type <my-project-root-path>/recipes/schemadotorg_recipes/remote_video_media_type;\
  ln -sf <my-project-root-path>/web/core/recipes/editorial_media_type <my-project-root-path>/recipes/schemadotorg_recipes/editorial_media_type;

  # Example to test don't use it.
  ln -sf /home/ahmed_galal/workspace/schemademo/web/modules/contrib/schemadotorg/config/schema/ /home/ahmed_galal/workspace/schemademo/recipes/schemadotorg_recipes;
```
### <span style="color:red"> (Optional) Dont use it.</span>
```diff
# Apply the schema.org JSON-LD recipe which enables Core and Contributed modules With JSON-LD support.
- ddev deush -y recipe ../recipes/schemadotorg_recipes/schemadotorg_recipe_jsonld; ddev drush cr; ddev drush cr;
```

### <span style="color:green"> instead use Module "Schema.org Mapping Sets" to generate the schema you desire.</span>


# Install Gen Admin Theme.
```bash
composer require 'drupal/gin:^5.0'

## Or For DDEV
ddev composer require 'drupal/gin:^5.0'

## Enable the theme ##

drush then gin
drush config:set system.theme admin gin

```

### Heper modules
```shell
composer require 'drupal/pathauto:^1.14'
composer require 'drupal/config_split:^2.0'
composer require 'drupal/field_group:^4.0'
composer require 'drupal/webform:^6.3@beta'
composer require 'drupal/simple_sitemap:^4.2'

```

### ECA Workflow Install
https://www.drupal.org/project/workflow_eca
```shell
composer require 'drupal/workflow_eca:^1.0@beta'
```


[![ECA Tutorial](https://img.youtube.com/vi/VIDEO_ID/0.jpg)](https://www.youtube.com/watch?v=unAM6MeSeQQ)

## Modern web development with headless Drupal
[![ECA Tutorial 2](https://img.youtube.com/vi/VIDEO_ID/0.jpg)](https://www.youtube.com/watch?v=okycKKNhH_0x)


## Content fields Best Widgets
<details open>
<summary>For Autocomplete</summary>

- [Autocomplete Deluxe](https://www.drupal.org/project/autocomplete_deluxe) <span style="color:red">(*****)</span>
- [Entity Reference Tree Widget](https://www.drupal.org/project/entity_reference_tree)
- [Hierarchical Select](https://www.drupal.org/project/hierarchical_select) <span style="color:red">(*****)</span>
  [![Hierarchical Select](https://www.drupal.org/files/images/hs2.png)]
- [Simple hierarchical select](https://www.drupal.org/project/shs)
- [Webform Simple Hierarchical Select](https://www.drupal.org/project/webform_shs)
</details>


<details open>
<summary>For Form</summary>

- [Inline Entity Form](https://www.drupal.org/project/inline_entity_form)  <span style="color:red">(*****)</span>
  - Beter to use it's complex widget
  - ////////////////////////////////////////////////////
- [Entity Reference Hierarchy](https://www.drupal.org/project/entity_hierarchy)<span style="color:red">(**)</span>
- [Dynamic Entity Reference](https://www.drupal.org/project/dynamic_entity_reference)<span style="color:red">(*****)</span>
  - Important it's allow to insert diferent types in the same field ex. user | person | actor
- [Field Group](https://www.drupal.org/project/field_group)<span style="color:red">(*****)</span>
- [Group](https://www.drupal.org/project/group)<span style="color:red">(*****)</span>
- [Conditional Fields](https://www.drupal.org/project/conditional_fields) <span style="color:red">(***)</span>
  - manually download it from [download](http://google.com)
</details>

## How to configure your project for patches
1- Update composer.json file
```jsonpath
{
  // ...
  "require": {
    // ...
    "cweagans/composer-patches": "^1.7" (1.7.3),
  },
  // ...
  "extras": {
    //...
    "patches": {
        "drupal/group":{
            "drupal.org/i/3494447:Undefiend function field_ui_entity_operation": "http://git.drupalcode.org/project/group/-/merge_requests/204.patch"
        },
    }
  }
}
```
