# OCR.ContentAI

Primo.OCR.ContentAI — NuGet-пакет для автоматизации работы с сервером ContentCapture. Пакет содержит элементы для обработки документов и получения результатов обработки роботом.

После установки пакета в Studio (Windows), в группе элементов **OCR** появится подгруппа **Content AI**. В нее входят элементы:
* [Сервер ContentCapture](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ocr-content-ai/attach-contentai-server) — автоматизирует подключение к серверу ContentCapture.
* [Обработать документы](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ocr-content-ai/process-document-server) — обрабатывает указанные документы на сервере ContentCapture.
* [Результаты обработки](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ocr-content-ai/get-process-result) — получает результат асинхронной обработки документов на сервере ContentCapture.

## Установка пакета

Ниже описан пошаговый способ установки пакета **Primo.OCR.ContentAI** в качестве зависимости:

1. Откройте Primo RPA Studio (Windows) и нажмите в главном меню кнопку **Управление зависимостями** <img src="../../../.gitbook/assets/managePackages32.png" alt="" data-size="line">

   ![](<../../../.gitbook/assets1/управление зависимостями.png>)

2. В окне **Управление зависимостями** перейдите на вкладку **Nuget.org**:
   * Введите в поисковом поле название пакета — **Primo.OCR.ContentAI**.
   * Справа нажмите кнопку **Установить**.
   * Внизу нажмите кнопку **Сохранить**.

   ![](<../../../.gitbook/assets1/windows_items/library/setup-nuget-content-ai.png>)

4. В открывшемся окне:
   * Нажмите кнопку **Установить**
   * Дождитесь окончания установки и нажмите **ОК**.
   * После чего закройте окно.

   ![](<../../../.gitbook/assets1/windows_items/library/setup-nuget-content-ai-2.png>)
 
5. Готово — пакет **Primo.OCR.ContentAI** установлен в качестве зависимости. Немного подождите, пока зависимость загрузится. 

6. Перейдите на панель элементов и найдите группу **OCR > Content AI**.

   ![](<../../../.gitbook/assets1/windows_items/library/ocr-content-ai-items.png>)

7. Перетащите нужный элемент в процесс, чтобы начать с ним работу.
