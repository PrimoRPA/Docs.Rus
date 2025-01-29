# Проверка установки
1. Войдите в систему как admin.
1. Перейдите на страницу статуса проекта - /admin/reports/status
1. При наличии **Ошибок** или **Предупреждений** об этом **необходимо** сообщить разработчикам Idea Hub.
1. Разработчики сообщат о том, какие вещи необходимо исправить, и могут подключиться для помощи.



### Установка обновлений для релиза 24.12
1. ```drush migrate:import params_ru --update```
2. ```drush migrate:import library_items --execute-dependencies --update```
3. ```drush ev "require_once (\Drupal::root() . '/../scripts/RandomContent.php');(new RandomContent())->createDashboards();"```


