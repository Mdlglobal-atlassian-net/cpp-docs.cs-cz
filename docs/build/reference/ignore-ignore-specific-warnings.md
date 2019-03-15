---
title: /IGNORE (Ignorovat konkrétní varování)
ms.date: 11/04/2016
f1_keywords:
- /OVERWRITE
helpviewer_keywords:
- /IGNORE linker option
ms.assetid: 37e77387-8838-4697-898f-d376ac641124
ms.openlocfilehash: 2b374e0e73f9fc14fa32ea4f63fa71039a5cf3c7
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57815837"
---
# <a name="ignore-ignore-specific-warnings"></a>/IGNORE (Ignorovat konkrétní varování)

```
/IGNORE:warning[,warning]
```

## <a name="parameters"></a>Parametry

*warning*<br/>
Počet upozornění můžete potlačit, v rozsahu 4000 na 4999 linkeru.

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení sestavy odkaz všechna upozornění. Zadejte **/ignorovat:** `warning` říct linkeru, aby potlačit konkrétní číslo upozornění. Ignorovat upozornění na více čísel upozornění oddělte čárkami.

Linker neumožňuje některé upozornění ignorovat. Tato tabulka obsahuje seznam upozornění, která nejsou potlačil **/Ignorovat**:

|Upozornění linkeru||
|--------------------|-|
|LNK4017|`keyword` příkaz není podporován pro cílovou platformu; Ignorovat|
|[LNK4044](../../error-messages/tool-errors/linker-tools-warning-lnk4044.md)|Nerozpoznaná možnost "`option`se ignoruje|
|LNK4062|"`option`"není kompatibilní s"`architecture`' cílový počítač; možnost se ignoruje|
|[LNK4075](../../error-messages/tool-errors/linker-tools-warning-lnk4075.md)|ignorování "`option1`"kvůli"`option2`" specifikace|
|[LNK4086](../../error-messages/tool-errors/linker-tools-warning-lnk4086.md)|vstupní bod "`function`"není __stdcall s"`number`' b argumentů; image se možná nespustí.|
|LNK4088|bitové kopie se generuje na možnosti/Force; bitové kopie se možná nespustí.|
|[LNK4105](../../error-messages/tool-errors/linker-tools-warning-lnk4105.md)|žádný argument zadaný pomocí možnosti "`option`"; ignoruje přepínač|
|LNK4203|Chyba při čtení databáze programu "`filename`"; objekt se propojí, jako by nebyly dostupné žádné ladicí informace|
|[LNK4204](../../error-messages/tool-errors/linker-tools-warning-lnk4204.md)|"`filename`' neobsahuje ladicí informace pro odkazující modul objekt se propojí, jako by nebyly dostupné žádné ladicí informace|
|[LNK4205](../../error-messages/tool-errors/linker-tools-warning-lnk4205.md)|"`filename`' chybí aktuální ladicí informace pro odkazující modul objekt se propojí, jako by nebyly dostupné žádné ladicí informace|
|[LNK4206](../../error-messages/tool-errors/linker-tools-warning-lnk4206.md)|Předkompilované informace o typu nebyl nalezen. "`filename`' není propojený nebo přepsat; objekt se propojí, jako by nebyly dostupné žádné ladicí informace|
|LNK4207|"`filename`" zkompilovat /Yc /Yu/Z7; nelze vytvořit soubor PDB, zkompilujte znovu s/zi, objektu, jako by nebyly dostupné žádné ladicí informace|
|LNK4208|nekompatibilní formát PDB v '`filename`"; odstraňte a znovu sestavte; objekt se propojí, jako by nebyly dostupné žádné ladicí informace|
|LNK4209|ladicí informace jsou poškozené; modul s rekompilujte; objekt se propojí, jako by nebyly dostupné žádné ladicí informace|
|[LNK4224](../../error-messages/tool-errors/linker-tools-warning-lnk4224.md)|`option` už není podporovaná; Ignorovat|
|LNK4228|"`option`" ignoruje neplatné pro knihovny DLL|
|[LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)|Neplatná direktiva /`directive` nalezen; ignoruje se.|

Obecně platí představují upozornění linkeru, které nelze ignorovat chyby sestavení, příkazového řádku chyby nebo chyby konfigurace, které by měla vyřešit.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. V **Linkeru** složky, vyberte **příkazového řádku** stránku vlastností.

1. Upravit **další možnosti** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.