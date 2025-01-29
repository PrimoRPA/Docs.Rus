# Установка обновлений для релиза 24.12

Если вы обновляете Idea Hub до версии 24.12, выполните следующие команды:
1. ```drush migrate:import params_ru --update```
2. ```drush migrate:import library_items --execute-dependencies --update```
3. ```drush ev "require_once (\Drupal::root() . '/../scripts/RandomContent.php');(new RandomContent())->createDashboards();"```
