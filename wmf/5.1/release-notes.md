---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,установка
title: Заметки о выпуске WMF 5.1
ms.openlocfilehash: 5c3075eda5482cc6a43bd237fe4fca0064136753
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219442"
---
# <a name="windows-management-framework-wmf-51-release-notes"></a>Заметки о выпуске Windows Management Framework (WMF) 5.1 #

WMF 5.1 включает компоненты PowerShell, WMI, WinRM и Software Inventory Logging (SIL), которые были выпущены с Windows Server 2016.
Службу WMF 5.1 можно установить на Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 и 2012 R2; она предоставляет ряд улучшений в WMF 5.0 RTM, включая следующие:

- Новые командлеты: локальные пользователи и группы; Get-ComputerInfo.
- Улучшения PowerShellGet включают принудительное подписание модулей и установку модулей JEA.
- Дополнительная поддержка PackageManagement для контейнеров, установка CBS, установка на основе EXE, пакеты CAB.
- Улучшения отладки для классов DSC и PowerShell.
- Улучшения для системы безопасности, включая принудительное использование модулей, подписанных каталогом и полученных от опрашивающего сервера, а также при использовании командлетов PowerShellGet.
- Ответы на разные запросы пользователей и решение проблем.

**Важные примечания.**

- **Для WMF 5.1 требуется .NET Framework 4.5.2** (или более поздняя версия). Если платформа .NET 4.5.2 (или более поздняя версия) не установлена, установка WMF 5.1 будет выполнена, но основные функции работать не будут. Инструкции см. в разделе [Установка и настройка WMF 5.1](https://msdn.microsoft.com/powershell/wmf/5.1/install-configure).
- Перед установкой WMF 5.1 RTM нужно удалить предварительную версию WMF 5.1.
- WMF 5.1 можно установить непосредственно на WMF 5.0 или WMF 4.0.
- Устанавливать WMF 4.0 перед установкой WMF 5.1 в Windows 7 и Windows Server 2008 R2 __не требуется__. Эта проблема имела место для предварительной версии WMF 5.1 и была устранена.
