---
title: Přehled LIB
ms.date: 11/04/2016
f1_keywords:
- Lib
helpviewer_keywords:
- LIB [C++], modes
ms.assetid: e997d423-f574-434f-8b56-25585d137ee0
ms.openlocfilehash: 03209bc409453cab1769606cb972f4572d3617bd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50548496"
---
# <a name="overview-of-lib"></a>Přehled LIB

LIB vytvoří standardní knihovny, importovat knihovny a exportovat soubory můžete použít s [odkaz](../../build/reference/linker-options.md) při sestavování programu. Lib – spustí z příkazového řádku.

Lib – můžete použít v následujících režimech:

- [Vytvářejí nebo upravují knihoven COFF](../../build/reference/managing-a-library.md)

- [Extrahování člena objektu do souboru](../../build/reference/extracting-a-library-member.md)

- [Vytvoření souboru exportu a knihovnu importu](../../build/reference/working-with-import-libraries-and-export-files.md)

Tyto režimy se vzájemně vylučují. lib – můžete použít v pouze jeden režim najednou.

## <a name="lib-options"></a>Lib – možnosti

V následující tabulce jsou uvedeny možnosti lib.exe odkazy na další informace.

|Možnost|Popis|
|-|-|
|**/ DEF**|Vytvořte knihovnu importu a souboru exportu.<br/><br/>Další informace najdete v části [sestavení knihovny importu a exportu souboru](../../build/reference/building-an-import-library-and-export-file.md).|
|**/ ERRORREPORT**|   Odesílat informace společnosti Microsoft o vnitřních chybách s lib.exe.<br/><br/>Další informace najdete v části [spuštění knihovny LIB](../../build/reference/running-lib.md).|
|**/EXPORT**|   Exportuje funkci z vaší aplikace.<br/><br/>Další informace najdete v části [sestavení knihovny importu a exportu souboru](../../build/reference/building-an-import-library-and-export-file.md).|
|**/ EXTRACT**|   Vytvořte soubor objektů (.obj), který obsahuje kopii členem existující knihovnu.<br/><br/>Další informace najdete v části [extrahování člena knihovny](../../build/reference/extracting-a-library-member.md).|
|**/ INCLUDE**|   Symbol se přidá do tabulky symbolů.<br/><br/>Další informace najdete v části [sestavení knihovny importu a exportu souboru](../../build/reference/building-an-import-library-and-export-file.md).|
|**/ LIBPATH**|   Přepíše cestu ke knihovně prostředí.<br/><br/>Další informace najdete v části [Správa knihovny](../../build/reference/managing-a-library.md).|
|**/ LIST**|   Zobrazí informace o výstupní knihovně na standardním výstupu.<br/><br/>Další informace najdete v části [Správa knihovny](../../build/reference/managing-a-library.md).|
|**/LTCG**|   Způsobí, že knihovna, která má být sestaven pomocí generování kódu při propojování.<br/><br/>Další informace najdete v části [spuštění knihovny LIB](../../build/reference/running-lib.md).|
|**/ MACHINE**|   Určuje cílovou platformu programu.<br/><br/>Další informace najdete v části [spuštění knihovny LIB](../../build/reference/running-lib.md).|
|**/ NAME**|   Při sestavování knihovny importů Určuje název knihovny DLL pro kterou má být sestaven knihovny importu.<br/><br/>Další informace najdete v části [Správa knihovny](../../build/reference/managing-a-library.md).|
|**/ NODEFAULTLIB**|   Odebere jeden nebo více výchozích knihoven ze seznamu knihoven, které prohledává při překladu externích odkazů.<br/><br/>Další informace najdete v části [Správa knihovny](../../build/reference/managing-a-library.md).|
|**/NOLOGO**|   Potlačí zobrazení LIB o autorských právech zprávu a číslo verze a zabraňuje zobrazování souborů příkazu.<br/><br/>Další informace najdete v části [spuštění knihovny LIB](../../build/reference/running-lib.md).|
|**/ OUT**|   Přepíše výchozí název výstupního souboru.<br/><br/>Další informace najdete v části [Správa knihovny](../../build/reference/managing-a-library.md).|
|**/ REMOVE**|   Vynechá objektu z výstupní knihovně.<br/><br/>Další informace najdete v části [Správa knihovny](../../build/reference/managing-a-library.md).|
|**/SUBSYSTEM**|   Říká operačnímu systému, jak spustit program vytvořil připojování ke knihovně výstup.<br/><br/>Další informace najdete v části [Správa knihovny](../../build/reference/managing-a-library.md).|
|**/ VERBOSE**|   Zobrazí podrobnosti o průběhu relace, včetně názvů přidávané soubory .obj.<br/><br/>Další informace najdete v části [spuštění knihovny LIB](../../build/reference/running-lib.md).|
|**/WX**|   Zpracovávat upozornění jako chyby.<br/><br/>Další informace najdete v části [spuštění knihovny LIB](../../build/reference/running-lib.md).|

## <a name="see-also"></a>Viz také

[Referenční dokumentace ke knihovně LIB](../../build/reference/lib-reference.md)<br/>
[Vstupní soubory knihovny LIB](../../build/reference/lib-input-files.md)<br/>
[Výstupní soubory knihovny LIB](../../build/reference/lib-output-files.md)<br/>
[Další výstup knihovny LIB](../../build/reference/other-lib-output.md)<br/>
[Struktura knihovny](../../build/reference/structure-of-a-library.md)