---
title: Kopírovat zdrojové vlastnosti projektu (Linux C++)
ms.date: 10/16/2019
ms.assetid: 1a44230d-5dd8-4d33-93b4-e77e03e00150
ms.openlocfilehash: bc99814e825cda091b6a0b00256ca2d8269ecdd3
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74305396"
---
# <a name="copy-sources-project-properties-linux-c"></a>Kopírovat zdrojové vlastnosti projektu (Linux C++)

::: moniker range="vs-2015"

Podpora pro Linux je k dispozici v systému Visual Studio 2017 nebo novějším.

::: moniker-end

::: moniker range=">=vs-2017"

Vlastnosti nastavené na této stránce vlastností se vztahují na všechny soubory v projektu s výjimkou toho, kde jsou nastavené vlastnosti na úrovni souboru.

Vlastnost | Popis
--- | ---
Zdroje ke zkopírování | Určuje zdroje, které se zkopírují do vzdáleného systému. Změna tohoto seznamu se může posunout nebo jinak ovlivnit adresářovou strukturu, do které se zkopírují soubory do vzdáleného systému.
Kopírovat zdroje | Určuje, jestli se mají kopírovat zdroje do vzdáleného systému.
Další zdroje ke zkopírování | Určuje další zdroje ke zkopírování do vzdáleného systému. Volitelně lze seznam zadat jako místní pro páry vzdáleného mapování pomocí syntaxe, jako je tato: fulllocalpath1: = fullremotepath1; fulllocalpath2: = fullremotepath2, kde lze místní soubor zkopírovat do zadaného vzdáleného umístění ve vzdáleném systému.

@SourcesToCopyRemotely a @DataFilesToCopyRemotely v souboru projektu odkazují na skupiny položek. Chcete-li upravit, které zdroje nebo datové soubory se zkopírují vzdáleně, upravte soubor *vcxproj* takto:

```xml
<ItemGroup>
   <MyItems Include="foo.txt" />
   <MyItems Include="bar.txt" />
   <DataFilesToCopyRemotely Include="@(MyItems)" />
</ItemGroup>
```

::: moniker-end
