---
ms.date: 2017-06-05
keywords: "powershell,командлет"
title: "Введение в интегрированную среду сценариев Windows PowerShell"
ms.assetid: a0de70ca-909a-4807-94d1-6da86e5b52a0
ms.openlocfilehash: 61d31fc2555d91bc7872d7b90cfb1f2a9832ff9c
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/08/2017
---
# <a name="introducing-the-windows-powershell-ise"></a><span data-ttu-id="52984-103">Введение в интегрированную среду сценариев Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="52984-103">Introducing the Windows PowerShell ISE</span></span>
<span data-ttu-id="52984-104">Интегрированная среда сценариев Windows PowerShell (ISE) является ведущим приложением для Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="52984-104">The Windows PowerShell Integrated Scripting Environment (ISE) is a host application for Windows PowerShell.</span></span> <span data-ttu-id="52984-105">В интегрированной среде сценариев Windows PowerShell можно запускать команды, а также записывать, тестировать и выполнять отладку в одном графическом пользовательском интерфейсе на основе Windows с редактированием нескольких строк, заполнением нажатием клавиши TAB, раскраской синтаксических конструкций, выборочным выполнением, контекстной справкой и поддержкой письма справа налево.</span><span class="sxs-lookup"><span data-stu-id="52984-105">In Windows PowerShell ISE, you can run commands and write, test, and debug scripts in a single Windows-based graphic user interface with multiline editing, tab completion, syntax coloring, selective execution, context-sensitive help, and support for right-to-left languages.</span></span>
<span data-ttu-id="52984-106">Пункты меню и сочетания клавиш можно использовать для выполнения большинства тех же задач, которые выполняются в Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="52984-106">You can use menu items and keyboard shortcuts to perform many of the same tasks that you would perform in the Windows PowerShell console.</span></span>  <span data-ttu-id="52984-107">Например, при отладке сценария в интегрированной среде сценариев Windows PowerShell, чтобы задать точку останова строки, щелкните правой кнопкой мыши строку кода, а затем нажмите кнопку **Точка останова**.</span><span class="sxs-lookup"><span data-stu-id="52984-107">For example, when you debug a script in the Windows PowerShell ISE, to set a line breakpoint in a script, right-click the line of code, and then click **Toggle Breakpoint**.</span></span>

<span data-ttu-id="52984-108">Новые функции в интегрированной среде сценариев Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="52984-108">Try these features in Windows PowerShell ISE.</span></span>

-   <span data-ttu-id="52984-109">Редактирование нескольких строк. Чтобы вставить пустую строку под текущей строкой в области команд, нажмите клавиши SHIFT+ВВОД.</span><span class="sxs-lookup"><span data-stu-id="52984-109">Multiline editing: To insert a blank line under the current line in the Command pane, press SHIFT+ENTER.</span></span>

-   <span data-ttu-id="52984-110">Чтобы запустить фрагмент сценария, выберите текст, который нужно запустить, и нажмите кнопку **Выполнить сценарий**.</span><span class="sxs-lookup"><span data-stu-id="52984-110">Selective execution: To run part of a script, select the text you want to run, and then click the **Run Script** button.</span></span> <span data-ttu-id="52984-111">Также можно нажать клавишу F5.</span><span class="sxs-lookup"><span data-stu-id="52984-111">Or, press F5.</span></span>

-   <span data-ttu-id="52984-112">Контекстная справка. Введите **Invoke-Item** и нажмите клавишу F1.</span><span class="sxs-lookup"><span data-stu-id="52984-112">Context-sensitive help: Type **Invoke-Item**, and then press F1.</span></span> <span data-ttu-id="52984-113">В разделе справки откроется файл справки по командлету **Invoke-Item**.</span><span class="sxs-lookup"><span data-stu-id="52984-113">The Help file opens to the Help topic for the **Invoke-Item** cmdlet.</span></span>

<span data-ttu-id="52984-114">Интегрированная среда сценариев Windows PowerShell позволяет настроить некоторые аспекты его представления.</span><span class="sxs-lookup"><span data-stu-id="52984-114">The Windows PowerShell ISE lets you customize some aspects of its appearance.</span></span> <span data-ttu-id="52984-115">Он также содержит собственный профиль Windows PowerShell, в котором можно хранить функции, псевдонимы, переменные и команды, используемые в интегрированной среде сценариев Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="52984-115">It also has its own Windows PowerShell profile, where you can store functions, aliases, variables, and commands you use in the Windows PowerShell ISE.</span></span>

### <a name="to-start-the-windows-powershell-ise"></a><span data-ttu-id="52984-116">Запуск интегрированной среды сценариев Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="52984-116">To start the Windows PowerShell ISE</span></span>

1.  <span data-ttu-id="52984-117">Выполните одно из следующих действий.</span><span class="sxs-lookup"><span data-stu-id="52984-117">Do one of the following:</span></span>

    -   <span data-ttu-id="52984-118">Нажмите кнопку **Пуск**, откройте **Все программы**, **Windows PowerShell V2** и щелкните **Интегрированная среда сценариев Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="52984-118">Click **Start**, point to **All Programs**, point to **Windows PowerShell V2**, and then click **Windows PowerShell ISE**.</span></span>

    -   <span data-ttu-id="52984-119">В Cmd.exe консоли Windows PowerShell или в поле "Выполнить" введите **powershell_ise.exe**.</span><span class="sxs-lookup"><span data-stu-id="52984-119">In the Windows PowerShell console Cmd.exe, or in the Run box, type, **powershell_ise.exe**.</span></span>

### <a name="to-get-help-in-the-windows-powershell-ise"></a><span data-ttu-id="52984-120">Получение справки в интегрированной среде сценариев Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="52984-120">To get Help in the Windows PowerShell ISE</span></span>

-   <span data-ttu-id="52984-121">В меню **Справка** выберите **Справка Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="52984-121">On the **Help** menu, click **Windows PowerShell Help**.</span></span> <span data-ttu-id="52984-122">Также можно нажать клавишу F1.</span><span class="sxs-lookup"><span data-stu-id="52984-122">Or, press F1.</span></span> <span data-ttu-id="52984-123">В открывшемся файле будет описана интегрированная среда сценариев Windows PowerShell и служба Windows PowerShell, в том числе вся справка, доступная с помощью командлета Get-Help.</span><span class="sxs-lookup"><span data-stu-id="52984-123">The file that opens describes Windows PowerShell ISE and Windows PowerShell, including all of the help available from the Get-Help cmdlet.</span></span>
