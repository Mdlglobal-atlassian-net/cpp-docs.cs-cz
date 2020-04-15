---
title: Kopírovat zdroje vlastnosti projektu (Linux C++)
ms.date: 10/16/2019
ms.assetid: 1a44230d-5dd8-4d33-93b4-e77e03e00150
ms.openlocfilehash: 732a13520a223f1aa73733cd4098c247052f8d3b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "79441384"
---
# <a name="copy-sources-project-properties-linux-c"></a>Kopírovat zdroje vlastnosti projektu (Linux C++)

::: moniker range="vs-2015"

Podpora Linuxu je dostupná ve Visual Studiu 2017 a novějším.

::: moniker-end

::: moniker range=">=vs-2017"

Vlastnosti nastavené na této stránce vlastností platí pro všechny soubory v projektu s výjimkou, jejichž vlastnosti na úrovni souboru jsou nastaveny.

| Vlastnost | Popis |
|--|--|
| Zdroje ke kopírování | Určuje zdroje, které mají být kopírovány do vzdáleného systému. Změna tohoto seznamu může posunout nebo jinak ovlivnit adresářovou strukturu, do které jsou soubory zkopírovány ve vzdáleném systému. |
| Kopírovat zdroje | Určuje, zda mají být zdroje zkopírovány do vzdáleného systému. |
| Další zdroje ke kopírování | Určuje další zdroje, které mají být zkopírovány do vzdáleného systému. Volitelně zadejte místní dvojice mapování vzdáleného mapování pomocí syntaxe, jako je tato: fulllocalpath1:=fullremotepath1;fulllocalpath2:=fullremotepath2, kde lze místní soubor zkopírovat do zadaného vzdáleného umístění ve vzdáleném systému. |

@SourcesToCopyRemotelya @DataFilesToCopyRemotely odkazovat na skupiny položek v souboru projektu. Chcete-li upravit, které zdroje nebo datové soubory jsou zkopírovány vzdáleně, upravte soubor *vcxproj* takto:

```xml
<ItemGroup>
   <MyItems Include="foo.txt" />
   <MyItems Include="bar.txt" />
   <DataFilesToCopyRemotely Include="@(MyItems)" />
</ItemGroup>
```

::: moniker-end
