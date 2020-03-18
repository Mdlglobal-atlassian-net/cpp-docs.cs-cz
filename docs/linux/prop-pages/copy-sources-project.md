---
title: Kopírovat zdrojové vlastnosti projektu (Linux C++)
ms.date: 10/16/2019
ms.assetid: 1a44230d-5dd8-4d33-93b4-e77e03e00150
ms.openlocfilehash: 732a13520a223f1aa73733cd4098c247052f8d3b
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441384"
---
# <a name="copy-sources-project-properties-linux-c"></a>Kopírovat zdrojové vlastnosti projektu (Linux C++)

::: moniker range="vs-2015"

Podpora pro Linux je k dispozici v systému Visual Studio 2017 nebo novějším.

::: moniker-end

::: moniker range=">=vs-2017"

Vlastnosti nastavené na této stránce vlastností se vztahují na všechny soubory v projektu s výjimkou toho, kde jsou nastavené vlastnosti na úrovni souboru.

| Vlastnost | Popis |
|--|--|
| Zdroje ke zkopírování | Určuje zdroje, které se zkopírují do vzdáleného systému. Změna tohoto seznamu se může posunout nebo jinak ovlivnit adresářovou strukturu, do které se zkopírují soubory do vzdáleného systému. |
| Kopírovat zdroje | Určuje, jestli se mají kopírovat zdroje do vzdáleného systému. |
| Další zdroje ke zkopírování | Určuje další zdroje ke zkopírování do vzdáleného systému. Volitelně můžete zadat místní a vzdálené páry mapování pomocí syntaxe takto: fulllocalpath1: = fullremotepath1; fulllocalpath2: = fullremotepath2, kde se dá místní soubor zkopírovat do zadaného vzdáleného umístění ve vzdáleném systému. |

@SourcesToCopyRemotely a @DataFilesToCopyRemotely v souboru projektu odkazují na skupiny položek. Chcete-li upravit, které zdroje nebo datové soubory se zkopírují vzdáleně, upravte soubor *vcxproj* takto:

```xml
<ItemGroup>
   <MyItems Include="foo.txt" />
   <MyItems Include="bar.txt" />
   <DataFilesToCopyRemotely Include="@(MyItems)" />
</ItemGroup>
```

::: moniker-end
