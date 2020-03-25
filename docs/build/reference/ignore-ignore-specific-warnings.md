---
title: /IGNORE (Ignorovat konkrétní varování)
ms.date: 11/04/2016
f1_keywords:
- /OVERWRITE
helpviewer_keywords:
- /IGNORE linker option
ms.assetid: 37e77387-8838-4697-898f-d376ac641124
ms.openlocfilehash: c1f9374c168e5b21dfd761f8c984f00ceae9f1bc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170615"
---
# <a name="ignore-ignore-specific-warnings"></a>/IGNORE (Ignorovat konkrétní varování)

```
/IGNORE:warning[,warning]
```

## <a name="parameters"></a>Parametry

*warning*<br/>
Číslo upozornění linkeru, které se má potlačit, v rozsahu 4000 až 4999.

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení propojí sestavy všechna upozornění. Zadáním **/Ignore:** `warning` sdělte linkeru pokyn, aby potlačil konkrétní číslo upozornění. Chcete-li ignorovat více upozornění, oddělte čísla upozornění čárkami.

Linker nepovoluje ignorování některých upozornění. V této tabulce jsou uvedena upozornění, která nejsou potlačena nástrojem **/Ignore**:

|Upozornění linkeru||
|--------------------|-|
|LNK4017|příkaz `keyword` není pro cílovou platformu podporován. přeskočen|
|[LINKERŮ LNK4044](../../error-messages/tool-errors/linker-tools-warning-lnk4044.md)|Nerozpoznaná možnost '`option`'; přeskočen|
|LNK4062|'`option`' není kompatibilní s cílovým počítačem '`architecture`'; možnost ignorována|
|[LINKERŮ LNK4075](../../error-messages/tool-errors/linker-tools-warning-lnk4075.md)|ignoruje se`option1`z důvodu specifikace "`option2`".|
|[LINKERŮ LNK4086](../../error-messages/tool-errors/linker-tools-warning-lnk4086.md)|parametr entryPoint '`function`' není __stdcall s '`number`' bajtů argumentů; Image se možná nespustí.|
|LNK4088|Obrázek vygenerovaný z důvodu možnosti/FORCE; Image se možná nespustí.|
|[LINKERŮ LNK4105](../../error-messages/tool-errors/linker-tools-warning-lnk4105.md)|nebyl zadán žádný argument s možností '`option`'; ignoruje se přepínač|
|LNK4203|Při čtení databáze programu`filename`došlo k chybě. propojování objektu, jako by nebyly žádné ladicí informace|
|[LINKERŮ LNK4204](../../error-messages/tool-errors/linker-tools-warning-lnk4204.md)|v`filename`chybí ladicí informace pro odkazující modul. propojování objektu, jako by nebyly žádné ladicí informace|
|[LINKERŮ LNK4205](../../error-messages/tool-errors/linker-tools-warning-lnk4205.md)|`filename`chybí aktuální ladicí informace pro odkazující modul. propojování objektu, jako by nebyly žádné ladicí informace|
|[LINKERŮ LNK4206](../../error-messages/tool-errors/linker-tools-warning-lnk4206.md)|předkompilované informace o typu se nenašly. '`filename`' není propojen nebo přepsán; propojování objektu, jako by nebyly žádné ladicí informace|
|LNK4207|'`filename`' zkompilované/YC/Yu/Z7; Nelze vytvořit soubor PDB; znovu kompilovat pomocí/Zi; propojování objektu, jako by nebyly žádné ladicí informace|
|LNK4208|nekompatibilní formát PDB v '`filename`'; Odstranit a znovu sestavit; propojování objektu, jako by nebyly žádné ladicí informace|
|LNK4209|informace o ladění jsou poškozené; rekompilovat modul; propojování objektu, jako by nebyly žádné ladicí informace|
|[LINKERŮ LNK4224](../../error-messages/tool-errors/linker-tools-warning-lnk4224.md)|`option` už není podporovaný. přeskočen|
|LNK4228|'`option`' je pro knihovnu DLL neplatný; přeskočen|
|[LINKERŮ LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)|Našla se neplatná direktiva/`directive`; přeskočen|

Obecně upozornění linkeru, která nelze ignorovat, reprezentují selhání sestavení, chyby příkazového řádku nebo chyby konfigurace, které byste měli opravit.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Ve složce **linker** vyberte stránku vlastností **příkazový řádek** .

1. Upravte vlastnost **Další možnosti** .

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Podívejte se na téma <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.
