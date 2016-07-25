# Кэш анализа модуля #

Начиная с версии 5.1 среда PowerShell предоставляет описанные ниже средства управления файлом, в котором кэшируются сведения о модуле, например экспортируемые им команды.

По умолчанию этот кэш хранится в файле `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.
Кэш обычно считывается при запуске в процессе поиска команды и записывается в фоновом потоке через некоторое время после импорта модуля.

Чтобы изменить расположение кэша по умолчанию, задайте переменную среды PSModuleAnalysisCachePath перед запуском PowerShell. Изменения, вносимые в эту переменную среды, влияют только на дочерние процессы.
Значение должно быть полным путем (включая имя файла), на создание и запись файлов по которому у среды PowerShell есть разрешение.
Чтобы отключить файловый кэш, в качестве этого значения можно указать недопустимое расположение, например:

```PowerShell
$env:PSModuleAnalysisCachePath = 'nul'
```

Таким образом задается путь к недопустимому устройству. Если среда PowerShell не может осуществлять запись по указанному пути, ошибка не выводится, хотя в трассировщике может выводиться сообщение об ошибке:

```PowerShell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

При выгрузке кэша среда PowerShell ищет модули, которые больше не существуют, чтобы кэш не был излишне большим.
Иногда эти проверки нежелательны. В этом случае их можно отключить, задав

```PowerShell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

Новое значение этой переменной среды вступает в силу немедленно в текущем процессе.

<!--HONumber=Jul16_HO1-->

