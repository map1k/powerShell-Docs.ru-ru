---
ms.date: 06/12/2017
keywords: dsc,powershell,конфигурация,установка
title: Встроенные ресурсы настройки требуемого состояния для Linux
ms.openlocfilehash: ea700d24c7ff4377af671944184abb3f201852e8
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218507"
---
# <a name="built-in-desired-state-configuration-resources-for-linux"></a>Встроенные ресурсы настройки требуемого состояния для Linux

Ресурсы — это строительные блоки, которые можно использовать для написания сценария настройки требуемого состояния (DSC) PowerShell. DSC для Linux поставляется с набором встроенных возможностей для настройки ресурсов, таких как файлы и папки, пакеты, переменные среды, службы и процессы.

## <a name="built-in-resources"></a>Встроенные ресурсы

Список ресурсов и ссылки на статьи, в которых они рассматриваются подробно.

* Ресурс [nxArchive](lnxArchiveResource.md) — предоставляет механизм распаковки файлов архива в формате TAR или ZIP в заданную папку.
* Ресурс [nxEnvironment](lnxEnvironmentResource.md) — управляет переменными среды на целевых узлах.
* Ресурс [nxFile](lnxFileResource.md) — управляет файлами и каталогами Linux.
* Ресурс [nxFileLine](lnxFileLineResource.md) — управляет отдельными строками в файле Linux.
* Ресурс [nxGroup](lnxGroupResource.md) — управляет локальными группами Linux.
* Ресурс [nxPackage](lnxPackageResource.md) — управляет пакетами на узлах Linux.
* Ресурс [nxScript](lnxScriptResource.md) — запускает сценарии на целевых узлах.
* Ресурс [nxService](lnxServiceResource.md) — управляет службами Linux (управляющими программами или "демонами").
* Ресурс [nxSshAuthorizedKeys](lnxSshAuthorizedKeysResource.md) — управляет открытыми SSH-ключами для пользователей Linux.
* Ресурс [nxUser](lnxUserResource.md) — управляет локальными пользователями Linux.