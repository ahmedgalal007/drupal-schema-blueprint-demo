<!-- TOC -->
* [<span style=""> Install Drupal 11</span>](#install-drupal)
* [<span style="">Configure Drupal</span>](#configure-drupal)
* [<span style="">Install Schemadotorg Blueprint</span>](#install-schemadotorg-blueprint)
<!-- TOC -->


## Install Drupal
<details style="margin-left: 30px;">
    <summary style="font-size:16px;color:#00c4ff;">From Scratch</summary>

```bash
    composer create-project drupal/recommended-project <my-site-name-dir>
    cd my-site-name-dir
```

  </details>

  <details style="margin-left: 30px;">
    <summary style="font-size:16px;color:#00c4ff;">DDEV</summary>


```bash
    # mkdir my-drupal-site && cd my-drupal-site
    ddev config --project-type=drupal11 --docroot=web
    ddev start

    ddev composer create-project drupal/recommended-project
    ddev composer require drush/drush

    ddev drush site:install --account-name=admin --account-pass=admin -y
    ddev launch
```

  </details>


## Configure Drupal
#### Change minimum stability to dev.
```bash
ddev composer config minimum-stability dev
```

##### Require Packages.
```bash
ddev composer require drupal/admin_toolbar drupal/devel   wikimedia/composer-merge-plugin;
ddev composer require drupal/config_rewrite:^1.6
```

##### Add the merge-plugin settings to extras.
##### ``` in the composer.json
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

## Install Schemadotorg Blueprint

```bash
ddev composer require drupal/schemadotorg:^1.0@alpha;
```

#### Run composer update
```bash
ddev composer update
```




# Install modules.
```bash
ddev drush install -y admin_toolbar devel schemadotorg_help
ddev drush install -y config_rewrite;
```

# Enable additional Core and Contrib modules.
```bash
ddev drush en -y media_library devel_generate
```


<details>
<summary style="font-weight: bold; font-size: 24px;"> Install all Schema.org Blueprints modules.</summary>

```bash
Use the below Drush commands to install all or a package of Schema.org Blueprints modules.
# Install all Schema.org Blueprints modules.
ddev drush pm-list --format=list | grep schemadotorg | xargs ddev drush install -y

------------------------------------------------------------------------------------------

# Install Schema.org Blueprints Core modules.
ddev drush pm-list --format=list --package='Schema.org Blueprints Core' | xargs ddev drush install -y

# Install Schema.org Blueprints API modules.
ddev drush pm-list --format=list --package='Schema.org Blueprints API' | xargs ddev drush install -y

# Install Schema.org Blueprints Documentation modules.
ddev drush pm-list --format=list --package='Schema.org Blueprints Documentation' | xargs ddev drush install -y

# Install Schema.org Blueprints Entities modules.
ddev drush pm-list --format=list --package='Schema.org Blueprints Entities' | xargs ddev drush install -y

# Install Schema.org Blueprints Fields modules.
ddev drush pm-list --format=list --package='Schema.org Blueprints Fields' | xargs ddev drush install -y

# Install Schema.org Blueprints JSON-LD modules.
ddev drush pm-list --format=list --package='Schema.org Blueprints JSON-LD' | xargs ddev drush install -y

# Install Schema.org Blueprints Other modules.
ddev drush pm-list --format=list --package='Schema.org Blueprints Other' | xargs ddev drush install -y

# Install Schema.org Blueprints Paragraphs modules.
ddev drush pm-list --format=list --package='Schema.org Blueprints Paragraphs' | xargs ddev drush install -y

# Install Schema.org Blueprints Recipe modules.
ddev drush pm-list --format=list --package='Schema.org Blueprints Recipe' | xargs ddev drush install -y

# Install Schema.org Blueprints Starter Kit modules.
ddev drush pm-list --format=list --package='Schema.org Blueprints Starter Kit' | xargs ddev drush install -y

------------------------------------------------------------------------------------------

# Install all Schema.org Blueprints modules.
drush install -y schemadotorg\
  schemadotorg_additional_mappings\
  schemadotorg_additional_type\
  schemadotorg_address\
  schemadotorg_allowed_formats\
  schemadotorg_auto_entitylabel\
  schemadotorg_block_content\
  schemadotorg_cer\
  schemadotorg_content_model_documentation\
  schemadotorg_content_moderation\
  schemadotorg_custom_field\
  schemadotorg_descriptions\
  schemadotorg_diagram\
  schemadotorg_entity_reference_override\
  schemadotorg_epp\
  schemadotorg_existing_values_autocomplete_widget\
  schemadotorg_export\
  schemadotorg_field_group\
  schemadotorg_field_prefix\
  schemadotorg_field_validation\
  schemadotorg_geolocation\
  schemadotorg_help\
  schemadotorg_inline_entity_form\
  schemadotorg_jsonapi\
  schemadotorg_jsonapi_preview\
  schemadotorg_jsonld\
  schemadotorg_jsonld_breadcrumb\
  schemadotorg_jsonld_custom\
  schemadotorg_jsonld_embed\
  schemadotorg_jsonld_endpoint\
  schemadotorg_jsonld_preview\
  schemadotorg_layout_paragraphs\
  schemadotorg_mapping_set\
  schemadotorg_media\
  schemadotorg_mercury_editor\
  schemadotorg_metatag\
  schemadotorg_node\
  schemadotorg_office_hours\
  schemadotorg_options\
  schemadotorg_paragraphs\
  schemadotorg_pathauto\
  schemadotorg_physical\
  schemadotorg_recipe\
  schemadotorg_report\
  schemadotorg_role\
  schemadotorg_scheduler\
  schemadotorg_simple_sitemap\
  schemadotorg_smart_date\
  schemadotorg_starterkit\
  schemadotorg_taxonomy\
  schemadotorg_translation\
  schemadotorg_type_tray\
  schemadotorg_ui;

# Install Schema.org Blueprints production modules.
# The below modules should always be enabled on the production environment.
drush install -y schemadotorg\
  schemadotorg_additional_mappings\
  schemadotorg_additional_type\
  schemadotorg_address\
  schemadotorg_block_content\
  schemadotorg_custom_field\
  schemadotorg_descriptions\
  schemadotorg_entity_reference_override\
  schemadotorg_epp\
  schemadotorg_geolocation\
  schemadotorg_jsonld\
  schemadotorg_jsonld_breadcrumb\
  schemadotorg_jsonld_custom\
  schemadotorg_jsonld_embed\
  schemadotorg_layout_paragraphs\
  schemadotorg_office_hours\
  schemadotorg_paragraphs\
  schemadotorg_pathauto\
  schemadotorg_physical\
  schemadotorg_role\
  schemadotorg_scheduler\
  schemadotorg_smart_date\
  schemadotorg_taxonomy\
  schemadotorg_translation;

# Install Schema.org Blueprints development modules.
# The below modules should generally be enabled on only development environments.
drush install -y schemadotorg_allowed_formats\
  schemadotorg_auto_entitylabel\
  schemadotorg_cer\
  schemadotorg_content_model_documentation\
  schemadotorg_content_moderation\
  schemadotorg_diagram\
  schemadotorg_existing_values_autocomplete_widget\
  schemadotorg_export\
  schemadotorg_field_group\
  schemadotorg_field_prefix\
  schemadotorg_field_validation\
  schemadotorg_help\
  schemadotorg_inline_entity_form\
  schemadotorg_jsonapi\
  schemadotorg_jsonapi_preview\
  schemadotorg_jsonld_endpoint\
  schemadotorg_jsonld_preview\
  schemadotorg_mapping_set\
  schemadotorg_media\
  schemadotorg_mercury_editor\
  schemadotorg_metatag\
  schemadotorg_node\
  schemadotorg_options\
  schemadotorg_recipe\
  schemadotorg_report\
  schemadotorg_simple_sitemap\
  schemadotorg_starterkit\
  schemadotorg_type_tray\
  schemadotorg_ui;

```
</details>




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
<video src="https://user-images.githubusercontent.com" width="600"></video>
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


<details >
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

<details >
<summary>For Article Managment</summary>

- [Gin Type Tray](https://www.drupal.org/project/gin_type_tray) Arrange Create Content Form and the Articles by types
- [Coffee](https://www.drupal.org/project/coffee)
  * ddev composer require 'drupal/coffee:^2.0'
- [Gin Login](https://www.drupal.org/project/gin_login)
  * ddev composer require 'drupal/gin_login:^2.1'
</details>

## How to configure your project for patches
1- Update composer.json file
```json lines
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
