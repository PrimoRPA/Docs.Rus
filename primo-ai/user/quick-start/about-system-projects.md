# О встроенных проектах

Primo RPA AI Server поставляется с набором обученных моделей\*, которые умеют:
* распознавать данные в изображениях паспортов;
* распознавать данные в изображениях СНИЛС;
* распознавать данные в изображениях Торг-12;
* классифицировать документы по типам: паспорт, СНИЛС, Торг-12.

Работа с обученными моделями осуществляется в рамках встроенных проектов, которые отображаются пользователю на главной странице сразу после входа в сервис.

![](<../../../.gitbook/assets1/primo-ai/embedded-projects.png>)

Наличие разных типов встроенных проектов поможет вам полностью автоматизировать процесс работы с документами:
1. Проект **Классификатор** будет полезен, если вы храните у себя смешанные изображения и вам необходимо автоматически определить тип документа на каждом изображении.
1. После завершения классификации, когда тип документа известен, вы можете отправить его в соответствующую модель для распознавания полей документа. В этом помогут проекты **Паспорт**, **СНИЛС** или **Торг-12**.

Таким образом, встроенные проекты позволяют:
* Быстро протестировать функции сервиса и оценить пользу для вашего бизнеса.
* Решить реальные бизнес-задачи, связанные с наиболее популярными типами документов — паспортом, СНИЛС, накладной Торг-12.



## Что дальше

См. [инструкцию](https://docs.primo-rpa.ru/primo-rpa/primo-ai-server/user/quick-start/system-projects) по работе со встроенным проектом.


> \**Файлы моделей входят в комплект поставки Primo RPA AI Server. Список моделей постоянно расширяется.*