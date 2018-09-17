---
title: -INCREMENTAL (Inkrementální odkaz) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /incremental
- VC.Project.VCLinkerTool.LinkIncremental
dev_langs:
- C++
helpviewer_keywords:
- /INCREMENTAL linker option
- -INCREMENTAL linker option
- INCREMENTAL linker option
- link incrementally option
- LINK tool [C++], options for full linking
- incremental linking
ms.assetid: 135656ff-94fa-4ad4-a613-22e1a2a5d16b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 02ba96a810703f653b101839d4c9b965da735588
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725046"
---
# <a name="incremental-link-incrementally"></a>/INCREMENTAL (inkrementální odkaz)

```
/INCREMENTAL[:NO]
```

## <a name="remarks"></a>Poznámky

Určuje, jak linker zpracovává přírůstkové propojení.

Linker se standardně spouští v přírůstkovém režimu. Chcete-li přepsat výchozí přírůstkové propojení, zadejte parametr /INCREMENTAL:NO.

Přírůstkově propojený program je funkčně ekvivalentní programu, který je mimo přírůstkově propojený. Ale protože je připraven pro následná přírůstková propojení, přírůstkově propojený spustitelný soubor, statické knihovny nebo soubor dynamické knihovny:

- Je větší než jiné přírůstkově propojený program z důvodu odsazení kódu a data. Odsazení umožňuje linkeru zvětšit velikost funkcí a dat bez nutnosti opětovného vytvoření souboru.

- Mohou obsahovat převodní rutiny odskoků, které ošetřují přemístění funkcí na nové adresy.

   > [!NOTE]
   > Zajistit, aby sestavení konečné verze neobsahuje odsazení nebo převodní rutiny, bez přírůstkové propojení programu.

Chcete-li program propojit přírůstkově bez ohledu na výchozí nastavení, zadejte parametr /INCREMENTAL. Pokud je vybraná tato možnost, linker vydá upozornění, pokud nemůže propojovat přírůstkově a pak program propojí bez postupně. Některé parametry a situace parametr /INCREMENTAL přepisují.

Většinu programů lze propojit přírůstkově. Některé změny jsou ale příliš rozsáhlé a některé parametry nejsou s přírůstkovým propojením kompatibilní. Při zadání libovolného z následujících parametrů provede příkaz LINK úplné propojení:

- Není vybráno přírůstkové propojení (/INCREMENTAL:NO)

- Je vybrán parametr /OPT:REF

- Je vybrán parametr /OPT:ICF

- Je vybrán parametr /OPT:LBR

- Je vybrán parametr /ORDER

/ INCREMENTAL je vyjádřena, když [/DEBUG](../../build/reference/debug-generate-debug-info.md) je zadán.

Příkaz LINK navíc provede úplné propojení, pokud dojde k některé z následujících situací:

- Chybí soubor se stavem přírůstkového propojení (.ilk). (Příkaz LINK vytvoří nový soubor .ilk při přípravě na následné přírůstkové propojení.)

- Soubor .ilk nemá oprávnění k zápisu. (Odkaz bude ignorovat soubor .ilk a odkazy bez postupně.)

- Chybí výstupní soubor .exe nebo .dll.

- Časové razítko souboru .ilk, .exe nebo .dll se změnilo.

- Některý parametr příkazu LINK se změnil. Při změně mezi sestaveními způsobí většina parametrů příkazu LINK úplné propojení.

- Je přidán nebo vynechán soubor objektů (.obj).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **Linkeru** složky.

1. Vyberte **Obecné** stránku vlastností.

1. Upravit **Povolit přírůstkové propojení** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

1. Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LinkIncremental%2A>.

## <a name="see-also"></a>Viz také

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)