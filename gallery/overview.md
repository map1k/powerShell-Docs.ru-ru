---
ms.date: 06/12/2017
contributor: JKeithB
keywords: коллекции,powershell,командлет,psgallery,psget
title: Коллекция PowerShell
ms.openlocfilehash: dc7e8dd7e4d96d8424a62cb3256c3164b63a3684
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2018
ms.locfileid: "34482936"
---
# <a name="the-powershell-gallery"></a>Коллекция PowerShell

Коллекция PowerShell — это центральный репозиторий для хранения содержимого PowerShell. В ней можно найти полезные модули PowerShell с командами и ресурсы настройки требуемого состояния (DSC).
Здесь также представлены скрипты PowerShell, некоторые из которых могут содержать рабочие процессы PowerShell. Они описывают набор задач и реализуют конвейер для их выполнения. Некоторые из этих элементов созданы корпорацией Майкрософт, а другие — сообществом PowerShell.

## <a name="powershellget-overview"></a>Обзор PowerShellGet

Модуль PowerShellGet содержит командлеты для обнаружения, установки, обновления и публикации артефактов PowerShell, таких как модули, ресурсы DSC, возможности ролей и скрипты из [коллекции PowerShell](https://www.PowerShellGallery.com) и других частных репозиториев.

## <a name="getting-started-with-the-gallery"></a>Начало работы с коллекцией

Для установки элементов из коллекции требуется последняя версия модуля PowerShellGet.
Полные инструкции по установке см. в разделе [Установка PowerShellGet](installing-psget.md).

Дополнительные сведения об использовании команд PowerShellGet при работе с коллекцией см. в статье [Начало работы](getting-started.md). Вы также можете запустить командлет *Update-Help -Module PowerShellGet*, чтобы установить локальную справку по этим командам.

## <a name="supported-operating-systems"></a>Поддерживаемые операционные системы

Для модуля **PowerShellGet** требуется **Windows PowerShell версии 3.0 или более поздней** либо **PowerShell Core версии 6.0 или более поздней**.

Подходящая версия **Windows PowerShell** доступна для следующих операционных систем:

- Windows 10
- Windows 8.1 Профессиональная
- Windows 8.1 Корпоративная
- Windows 7 с пакетом обновления 1 (SP1)
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2008 R2 с пакетом обновления 1 (SP1)

Для **PowerShellGet** также требуется .NET Framework 4.5 или более поздней версии. Установить .NET Framework 4.5 или более поздней версии можно [отсюда](https://msdn.microsoft.com/library/5a4x27ek.aspx).

**PowerShell Core** поддерживает множество операционных систем. Полный список можно найти в [этой статье](https://blogs.msdn.microsoft.com/powershell/2018/01/10/powershell-core-6-0-generally-available-ga-and-supported/).

Много модулей, размещенных в коллекции, поддерживают различные ОС и имеют дополнительные требования. Дополнительные сведения см. в документации по модулям.

## <a name="got-a-question-have-feedback"></a>Возник вопрос? Хотите поделиться мнением?

Дополнительные сведения о коллекции PowerShell и PowerShellGet см. на странице [Начало работы](getting-started.md). Оставить отзыв или сообщить о проблеме можно на сайте [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).
