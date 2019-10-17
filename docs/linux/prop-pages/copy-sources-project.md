---
title: Kopírovat zdrojové vlastnosti projektu (Linux C++)
ms.date: 10/16/2019
ms.assetid: 1a44230d-5dd8-4d33-93b4-e77e03e00150
ms.openlocfilehash: ceaa1240f08b83ebc83bd7fdc25a3215467eb3f1
ms.sourcegitcommit: 9aab425662a66825772f091112986952f341f7c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444942"
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

@SourcesToCopyRemotely a @DataFilesToCopyRemotely odkazují na skupiny položek v souboru projektu. Chcete-li upravit, které zdroje nebo datové soubory se zkopírují vzdáleně, upravte soubor *vcxproj* takto:

```xml
<ItemGroup>
   <MyItems Include=“foo.txt” />
   <MyItems Include=“bar.txt” />
   <DataFilesToCopyRemotely Include=”@(MyItems)” />
</ItemGroup>
```

::: moniker-end
