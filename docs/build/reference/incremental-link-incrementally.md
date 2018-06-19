---
title: -INCREMENTAL (Inkrementální odkaz) | Microsoft Docs
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
ms.openlocfilehash: 7495b3dda7b79f45045176fc949016f89c92506a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376478"
---
# <a name="incremental-link-incrementally"></a>/INCREMENTAL (inkrementální odkaz)
```  
/INCREMENTAL[:NO]  
```  
  
## <a name="remarks"></a>Poznámky  
 Určuje, jak linker zpracovává přírůstkové propojení.  
  
 Linker se standardně spouští v přírůstkovém režimu. Chcete-li přepsat výchozí přírůstkové propojení, zadejte parametr /INCREMENTAL:NO.  
  
 Přírůstkově propojené programu je funkčně srovnatelný program, který je propojený jiný postupně. Ale protože je připravená pro následné přírůstkové odkazy, postupně propojené spustitelný soubor, statické knihovny nebo soubor dynamické knihovny:  
  
-   Z důvodu odsazení kódu a dat je větší než jiné přírůstkově propojené program. Odsazení umožňuje propojovací program a zvyšte velikost funkce a dat bez nutnosti opětovného vytvoření souboru.  
  
-   Mohou obsahovat převodní rutiny odskoků, které ošetřují přemístění funkcí na nové adresy.  
  
    > [!NOTE]
    >  Aby se zajistilo, že vaše finální verzi sestavení neobsahuje odsazení nebo převody, bez přírůstkově propojte váš program.  
  
 Chcete-li program propojit přírůstkově bez ohledu na výchozí nastavení, zadejte parametr /INCREMENTAL. Pokud je vybraná tato možnost, linkeru vydá upozornění, pokud nelze přírůstkově propojit a potom program bez přírůstkově odkazy. Některé parametry a situace parametr /INCREMENTAL přepisují.  
  
 Většinu programů lze propojit přírůstkově. Některé změny jsou ale příliš rozsáhlé a některé parametry nejsou s přírůstkovým propojením kompatibilní. Při zadání libovolného z následujících parametrů provede příkaz LINK úplné propojení:  
  
-   Není vybráno přírůstkové propojení (/INCREMENTAL:NO)  
  
-   Je vybrán parametr /OPT:REF  
  
-   Je vybrán parametr /OPT:ICF  
  
-   Je vybrán parametr /OPT:LBR  
  
-   Je vybrán parametr /ORDER  
  
 / INCREMENTAL je zahrnuta, když [/DEBUG](../../build/reference/debug-generate-debug-info.md) je zadán.  
  
 Příkaz LINK navíc provede úplné propojení, pokud dojde k některé z následujících situací:  
  
-   Chybí soubor se stavem přírůstkového propojení (.ilk). (Příkaz LINK vytvoří nový soubor .ilk při přípravě na následné přírůstkové propojení.)  
  
-   Soubor .ilk nemá oprávnění k zápisu. (Odkaz ignoruje .ilk soubor a odkazy bez přírůstkově.)  
  
-   Chybí výstupní soubor .exe nebo .dll.  
  
-   Časové razítko souboru .ilk, .exe nebo .dll se změnilo.  
  
-   Některý parametr příkazu LINK se změnil. Při změně mezi sestaveními způsobí většina parametrů příkazu LINK úplné propojení.  
  
-   Je přidán nebo vynechán soubor objektů (.obj).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Vyberte **Linkeru** složky.  
  
3.  Vyberte **Obecné** stránku vlastností.  
  
4.  Změnit **Povolit přírůstkové propojování** vlastnost.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
1.  V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LinkIncremental%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)