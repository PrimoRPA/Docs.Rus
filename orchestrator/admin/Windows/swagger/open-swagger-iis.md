# Открытие Swagger в IIS под Windows 2016 Server

Swagger – интерактивная документация по API Оркестратора. По умолчанию Swagger доступен только на машине Оркестратора по адресу: http://localhost:5001/swagger/index.html

Чтобы им можно было пользоваться на любой машине в сети организации, не открывая порт 5001 Оркестратора, требуется настроить в IIS проксирование этого адреса.

Как это сделать:

1. Перейдите в папку `C:\Primo\UI`.
2. Измените файл **web.config**: добавьте в начало секции `<rules/>` правило `Reverse Proxy to Swagger` для проксирования Swagger:

```
<rule name="Reverse Proxy to Swagger" stopProcessing="true">
	<match url="^swagger/(.*)" />
	<action type="Rewrite" url="http://localhost:5001/swagger/{R:1}" logRewrittenUrl="true" />
</rule>
```

![](<../../../../.gitbook/assets/swagger-iils-1.png>)

3\. При помощи оснастки IIS или cmd (iisreset) перезапустите узел Primo.UI:

![](<../../../../.gitbook/assets/swagger-iils-2.png>)

4\. Проверьте доступность Swagger по адресу:
https://{IP}:44392/swagger/index.html 

![](<../../../../.gitbook/assets/swagger-iils-3.png>)
