# <a name="desired-state-configuration-overview-for-engineers"></a>Общие сведения о настройке требуемого состояния Windows PowerShell для инженеров #

В этом документе, предназначенном для групп разработки и эксплуатации, описаны преимущества настройки требуемого состояния (DSC) PowerShell.
Обзор значения DSC с более высокой точки зрения см. в статье [Общие сведения о настройке требуемого состояния Windows PowerShell для руководителей](decisionMaker.md).

## <a name="benefits-of-desired-state-configuration"></a>Преимущества настройки требуемого состояния

Настройка требуемого состояния обеспечивает следующие преимущества:
- упрощение написания скриптов для Windows;
- повышение скорости итерации.

Понятие непрерывного развертывания становится все более важным. Непрерывное развертывание означает возможность выполнять развертывание часто (возможно, несколько раз в день).
Эти развертывания предназначены не для исправления ошибок, а для быстрой публикации компонентов.
Разрабатывая новые компоненты и вводя их в эксплуатацию с максимальной простотой и надежностью, можно сократить время окупаемости новой бизнес-логики.

Существуют две тенденции, которые увеличивают эту потребность в оперативных действиях. Переход на облачные вычисления подразумевает быстрые и масштабные изменения, но при этом постоянно сохраняется угроза сбоя.
Возможные последствия вынуждают использовать автоматизацию для обеспечения бесперебойной работы.
В ответ на эти изменения и был разработан подход DevOps. 


DSC — это платформа, которая обеспечивает декларативное, автономное и идемпотентное (повторяемое) развертывание, настройку и соответствие требованиям.
Платформа DSC гарантирует, что компоненты центра обработки данных имеют правильные настройки, что позволяет избежать ошибок и затратных сбоев при развертывании.
Рассматривая конфигурации DSC как часть кода приложения, DSC обеспечивает непрерывное развертывание.
Конфигурации DSC должны обновляться в составе приложения. Это является гарантией того, что сведения, необходимые для развертывания приложения, всегда актуальны и готовы к использованию.


## <a name="i-have-powershell-why-do-i-need-desired-state-configuration"></a>"Я использую PowerShell. Зачем мне настройка требуемого состояния?"

Конфигурации DSC отделяют намерение ("что мне нужно") от его реализации ("каким образом это сделать").
Это означает, что логика выполнения содержится внутри ресурсов.
Пользователи не должны знать, как реализовать или развернуть тот или иной компонент, если для него доступен ресурс DSC.
Это позволяет пользователям сосредоточиться на структуре развертывания.

Например, сценарий PowerShell должен выглядеть следующим образом:
```powershell
# Create a share in Windows Server 8
New-SmbShare -Name MyShare -Path C:\Demo\Temp -FullAccess Alice -ReadAccess Bob
```
Это простой и понятный скрипт. Тем не менее при попытке использовать этот скрипт в рабочей среде возникнет ряд проблем.
Что произойдет, если выполнить этот скрипт два раза подряд?
Что произойдет, если у Боба раньше был полный доступ к общей папке? 

Чтобы компенсировать эти проблемы, "реальная" версия этого скрипта будет выглядеть примерно так:
```powershell
# But actually creating a share in an idempotent way would be

$shareExists = $false
$smbShare = Get-SmbShare -Name $Name -ErrorAction SilentlyContinue
if($smbShare -ne $null)
{
    Write-Verbose -Message "Share with name $Name exists"
    $shareExists = $true
}

if ($shareExists -eq $false)
{
    Write-Verbose "Creating share $Name to ensure it is Present"
    New-SmbShare @psboundparameters
}
else
{
    # Need to call either Set-SmbShare or *ShareAccess cmdlets
    if ($psboundparameters.ContainsKey("ChangeAccess"))
    {
       #...etc, etc, etc
    }
}
```

Это более сложный скрипт с множеством выражений логики и обработкой ошибок.
Он сложнее, так как на этот раз вы указываете не что нужно сделать, а *как это сделать*.

DSC позволяет указать, что нужно сделать, абстрагируясь от базовой логики.

```powershell
# A configuration is a special kind of PowerShell function
Configuration Sample_Share
{
   Import-DscResource -Module xSmbShare
   # Nodes are the endpoint we wish to configure
   # A Configuration block can have zero or more Node blocks
   Node $NodeName
   {
      # Next, specify one or more resource blocks
      # Resources are simply PowerShell modules that
      # implement the logic of "how" to execute a task
      xSmbShare MySMBShare
      {
          Ensure      = "Present" 
          Name        = "MyShare"
          Path        = "C:\Demo\Temp"  
          ReadAccess  = "Alice"
          FullAccess  = "Bob"
          Description = "This is an updated description for this share"
      }
   }
} 
#Run the function to compile the configuration
Sample_Share
#Pass the configuration to the nodes we defined and configure them
Start-DscConfiguration Sample_Share
```

Этот скрипт четко отформатирован и удобен для чтения.
Логические пути и обработка ошибок по-прежнему присутствуют в реализации [ресурсов](resources.md), но они невидимы для автора скрипта. 



## <a name="separating-environment-from-structure"></a>Разделение среды и структуры

Обычно в DevOps используется несколько сред развертывания. Например, у вас может быть среда разработки, используемая для быстрого создания прототипа нового кода.
Из среды разработки код переходит в среду тестирования, где другие пользователи могут проверить новые функциональные возможности.
Наконец код переходит в рабочую среду активного сайта.

Конфигурации DSC включают конвейер "разработка — тестирование — производство", который реализуется благодаря использованию [данных конфигурации](configData.md).
Это позволяет отвлеченно рассматривать различия между структурой конфигурации и управляемыми узлами.
Например, вы можете определить конфигурацию, для которой требуется SQL Server, сервер IIS и сервер среднего уровня. Независимо от того, к каким узлам относятся различные части этой конфигурации, эти три элемента всегда будет присутствовать.
С помощью данных конфигурации можно указать все три элемента на одном компьютере в среде разработки, разделить три элемента на трех разных компьютерах в тестовой среде и, наконец, на всех рабочих серверах в рабочей среде.
Чтобы выполнить развертывание в различных средах, можно вызвать `Start-DscConfiguration` с помощью правильных данных конфигурации для целевой среды. 

## <a name="see-also"></a>См. также

[Конфигурации](configurations.md)

[Данные конфигурации](configData.md)

[Ресурсы](resources.md)