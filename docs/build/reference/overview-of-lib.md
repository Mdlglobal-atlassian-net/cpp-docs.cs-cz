---
title: "Přehled LIB | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Lib
dev_langs: C++
helpviewer_keywords: LIB [C++], modes
ms.assetid: e997d423-f574-434f-8b56-25585d137ee0
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ef3d1e57371fdea62bb557830baca633f4165637
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="overview-of-lib"></a>Přehled LIB
LIB vytvoří standardní knihovny, importovat knihovny a exportovat soubory, které můžete použít se [odkaz](../../build/reference/linker-options.md) při sestavování programu. LIB se spouští z příkazového řádku.  
  
 LIB můžete použít v následujících režimech:  
  
-   [Vytváříte nebo upravujete knihovnu COFF](../../build/reference/managing-a-library.md)  
  
-   [Extrahování člena objektu do souboru](../../build/reference/extracting-a-library-member.md)  
  
-   [Vytvoření souboru exportu a knihovnu importu](../../build/reference/working-with-import-libraries-and-export-files.md)  
  
 Tyto režimy se vzájemně vylučují. současně můžete použít LIB v pouze jeden režim.  
  
## <a name="lib-options"></a>Možnosti lib  
 Následující tabulka uvádí možnosti lib.exe, se zobrazí odkaz na další informace.  
  
 **/ DEF**  
 Vytvořte knihovnu importu a souboru exportu.  
  
 Další informace najdete v části [sestavení knihovny importu a exportu souboru](../../build/reference/building-an-import-library-and-export-file.md).  
  
 **/ ERRORREPORT**  
 Odesílat informace společnosti Microsoft o s lib.exe s interními chybami.  
  
 Další informace najdete v části [systémem LIB](../../build/reference/running-lib.md).  
  
 **/ EXPORT**  
 Export funkce z vaší aplikace.  
  
 Další informace najdete v části [sestavení knihovny importu a exportu souboru](../../build/reference/building-an-import-library-and-export-file.md).  
  
 **/ EXTRACT**  
 Vytvořte soubor objektu (.obj), který obsahuje kopii členem existující knihovnu.  
  
 Další informace najdete v části [extrahování člena knihovny](../../build/reference/extracting-a-library-member.md).  
  
 **/ INCLUDE**  
 Přidá symbol do tabulky symbolů.  
  
 Další informace najdete v části [sestavení knihovny importu a exportu souboru](../../build/reference/building-an-import-library-and-export-file.md).  
  
 **/ LIBPATH**  
 Přepíše danou cestu knihovny prostředí.  
  
 Další informace najdete v části [Správa knihovny](../../build/reference/managing-a-library.md).  
  
 **NEBO JEJICH VÝPISU**  
 Zobrazí informace o knihovně výstup standardním výstupu.  
  
 Další informace najdete v části [Správa knihovny](../../build/reference/managing-a-library.md).  
  
 **/ LTCG**  
 Způsobí, že knihovnu, která má být sestaven pomocí kódu v době propojování generace.  
  
 Další informace najdete v části [systémem LIB](../../build/reference/running-lib.md).  
  
 **/ MACHINE**  
 Určuje cílovou platformu programu.  
  
 Další informace najdete v části [systémem LIB](../../build/reference/running-lib.md).  
  
 **/ NAME**  
 Při sestavování knihovnu importu, určuje název knihovny DLL, pro kterou je vytvořený knihovny importu.  
  
 Další informace najdete v části [Správa knihovny](../../build/reference/managing-a-library.md).  
  
 **/ NODEFAULTLIB**  
 Odebere ze seznamu knihoven, které vyhledávání při rozpoznávání externí odkazy na jeden nebo více výchozí knihovny.  
  
 Další informace najdete v části [Správa knihovny](../../build/reference/managing-a-library.md).  
  
 **/ NOLOGO**  
 Potlačí zobrazení LIB autorským zprávu a verze číslo a zabraňuje zobrazování příkaz souborů.  
  
 Další informace najdete v části [systémem LIB](../../build/reference/running-lib.md).  
  
 **/ OUT**  
 Přepíše výchozí název výstupního souboru.  
  
 Další informace najdete v části [Správa knihovny](../../build/reference/managing-a-library.md).  
  
 **NEBO ODEBRAT**  
 Vynechá objekt z knihovny výstup.  
  
 Další informace najdete v části [Správa knihovny](../../build/reference/managing-a-library.md).  
  
 **/ SUBSYSTEM**  
 Informuje operačního systému, jak spustit program vytvořené připojování ke knihovně výstup.  
  
 Další informace najdete v části [Správa knihovny](../../build/reference/managing-a-library.md).  
  
 **/ VERBOSE**  
 Zobrazí podrobnosti o průběhu relace, včetně názvů soubory .obj, který chcete přidat.  
  
 Další informace najdete v části [systémem LIB](../../build/reference/running-lib.md).  
  
 **/WX**  
 Upozornění považovat za chyby.  
  
 Další informace najdete v části [systémem LIB](../../build/reference/running-lib.md).  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace LIB](../../build/reference/lib-reference.md)   
 [Vstupní soubory LIB](../../build/reference/lib-input-files.md)   
 [LIB – výstupní soubory](../../build/reference/lib-output-files.md)   
 [Další výstup LIB](../../build/reference/other-lib-output.md)   
 [Struktura knihovny](../../build/reference/structure-of-a-library.md)