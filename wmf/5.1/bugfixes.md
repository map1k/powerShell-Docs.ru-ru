---
title: "Исправления ошибок в WMF 5.1 (предварительная версия)"
ms.date: 2016-07-13
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
translationtype: Human Translation
ms.sourcegitcommit: 57049ff138604b0e13c8fd949ae14da05cb03a4b
ms.openlocfilehash: 90d57af0c8b90e709769525455ae39557b9c7176

---

# Исправления ошибок в WMF 5.1 (предварительная версия)#

## Устранение ошибок ##

В WMF 5.1 исправлены следующие важные ошибки.

### При автоматическом обнаружении модулей полностью учитывается `$env:PSModulePath` ###

Автоматическое обнаружение модулей (их автоматическая загрузка без явного вызова Import-Module при вызове команды) появилось в WMF 3. В этой версии среда PowerShell проверяла команды в `$PSHome\Modules` перед использованием `$env:PSModulePath`.

В WMF 5.1 это поведение изменилось: `$env:PSModulePath` учитывается полностью. Это позволяет автоматически загружать созданные пользователями модули, в которых определяются предоставляемые PowerShell команды (например, `Get-ChildItem`), и правильно переопределять встроенные команды.

### При перенаправлении файлов больше не задается жестко `-Encoding Unicode` ###

Во всех предыдущих версиях PowerShell было невозможно контролировать кодировку файлов, используемую оператором перенаправления файлов, например `get-childitem > out.txt`, так как среда PowerShell добавляла параметр `-Encoding Unicode`.

Начиная с версии WMF 5.1 можно изменять кодировку файлов при перенаправлении, задавая `$PSDefaultParameterValues`, например:

```
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### Исправлена регрессия при доступе к членам `System.Reflection.TypeInfo` ###

Появившаяся в WMF 5.0 регрессия нарушала доступ к членам `System.Reflection.RuntimeType`, например `[int].ImplementedInterfaces`.
Эта ошибка исправлена в WMF 5.1.


### Исправлены некоторые проблемы с COM-объектами ###

В WMF 5.0 появился новый модуль привязки COM для вызова методов применительно к COM-объектам и доступа к свойствам COM-объектов.
Этот новый модуль значительно повысил производительность, но в нем был ряд ошибок, которые исправлены в WMF 5.1.

#### Преобразование аргументов не всегда выполнялось правильно ####

Рассмотрим следующий пример:

```
$obj = new-object -com wscript.shell
$obj.SendKeys([char]173)
```

Метод SendKeys требует строку, но среда PowerShell не преобразовала char в string, отложив преобразование до вызова метода IDispatch::Invoke, который использует VariantChangeType для выполнения преобразования. В этом примере это приводит к отправке ключей "1", "7" и "3" вместо требуемого ключа Volume.Mute.

#### Перечисляемые COM-объекты не всегда обрабатывались правильно ####

Среда PowerShell, как правило, перечисляет большинство перечисляемых объектов, но регрессия, появившаяся в WMF 5.0, препятствовала перечислению COM-объектов, реализующих интерфейс IEnumerable.  Например:

```
function Get-COMDictionary
{
    $d = New-Object -ComObject Scripting.Dictionary
    $d.Add('a', 2)
    $d.Add('b', 2)
    return $d
}

$x = Get-COMDictionary
```

В приведенном выше примере WMF 5.0 неправильно записывает Scripting.Dictionary в конвейер вместо перечисления пар "ключ-значение".

Это изменение также затрагивает [проблемы с подключением 1752224](https://connect.microsoft.com/PowerShell/feedback/details/1752224).

### `[ordered]` не разрешалось использовать в классах ###

В WMF 5 появились классы, в которых проверялось использование литералов типов.  `[ordered]` выглядит как литерал типа, но в действительности не является типом .Net.  В WMF 5 неправильно выдавалась ошибка для `[ordered]` внутри класса:

```
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```


### Вызов разделов справки при наличии нескольких версий не работал ###

До версии WMF 5.1 при наличии нескольких установленных версий модуля с общим разделом справки, например "about_PSReadline", команда `help about_PSReadline` возвращала несколько разделов без возможности просмотреть саму справку.

В WMF 5.1 эта проблема устранена: теперь возвращается последняя версия раздела.

Командлет Get-Help не позволяет указать версию, по которой требуется справка. В качестве обходного решения можно перейти к каталогу модулей и открыть справку напрямую, например с помощью любимого редактора. 



<!--HONumber=Jul16_HO3-->

