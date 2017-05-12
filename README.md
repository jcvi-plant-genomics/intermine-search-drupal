# intermine-search-drupal
Drupal module to enable searching a mine instance using InterMine Search API

## Installation

1. On the command line, change directory to the location of your Drupal modules and clone the `intermine-search-drupal` git repository, like so:
```
$ cd /opt/www/MTGD/htdocs/tripal
$ cd sites/all/modules
$ git clone https://github.com/jcvi-plant-genomics/intermine-search-drupal.git intermine_search
```
2. On the Drupal modules page <http://localhost/admin/modules>, activate the "InterMine Search" module. This can also be done from the command-line via `drush`, like so:
```
$ drush pm-enable intermine_search
```
3. On the module configuration page <http://locahost/admin/config/search/intermine_search>, update the settings to point to your InterMine instance. Click "Save Configuration" to store the settings in the database. For example, MedicMine was configured like so:  
    1. Instance name: **MedicMine**
    2. Base URL (without trailing slash): **http://medicmine.jcvi.org/medicmine**
    3. Search examples: **e.g. Medtr2g036650, plasma membrane, sucrose synthase**
4. On the Drupal Search Settings page <http://localhost/admin/config/search/settings>, enable the "InterMine Search" module, set it as the "Default search module", and click "Save Configuration".

## Usage

Any _%search_term%_ passed to the URL (like so: <http://localhost/search/medicmine/%search_term%>) will trigger a query against the Search API endpoint of the configured InterMine instance.

The results (returned in JSON format by the InterMine API) are used to populate a faceted, dynamic, search result page with contextual links to corresponding entities within the InterMine instance.
