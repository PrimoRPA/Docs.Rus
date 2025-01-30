# Установка обновлений для релиза 24.12

Если вы обновляете Idea Hub до версии 24.12, выполните последовательно следующие команды:
```
drush migrate:import params_ru --update
```
```
drush migrate:import library_items --execute-dependencies --update
```
```
drush ev "require_once (\Drupal::root() . '/../scripts/RandomContent.php');(new RandomContent())->createDashboards();"
```

## Что дальше 

Следующий шаг — [проверка установки](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-idea-hub/installation/linux/shecking-installation).
