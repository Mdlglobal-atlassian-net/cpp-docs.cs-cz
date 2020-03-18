---
title: Přehled LIB
description: Přehled použití a možností nástroje knihovna, LIB. exe.
ms.date: 02/09/2020
helpviewer_keywords:
- LIB [C++], modes
ms.assetid: e997d423-f574-434f-8b56-25585d137ee0
ms.openlocfilehash: 4ed725f383d956adf7abcf1c68002dee51703013
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439010"
---
# <a name="overview-of-lib"></a>Přehled LIB

LIB (lib. exe) vytvoří standardní knihovny, importovat knihovny a exportovat soubory, které můžete použít s [odkazem](linker-options.md) při sestavování programu. LIB spouští z příkazového řádku.

LIB můžete použít v následujících režimech:

- [Sestavení nebo úprava knihovny COFF](managing-a-library.md)

- [Extrakce objektu člena do souboru](extracting-a-library-member.md)

- [Vytvoření souboru exportu a knihovny importů](working-with-import-libraries-and-export-files.md)

Tyto režimy se vzájemně vylučují; v jednom okamžiku můžete použít LIB pouze v jednom režimu.

## <a name="lib-options"></a>Možnosti knihovny LIB

V následující tabulce jsou uvedeny možnosti pro lib. exe s odkazem na Další informace.

|Možnost|Popis|
|-|-|
|**/DEF**|Vytvořte knihovnu importu a soubor exportu.<br/><br/>Další informace najdete v tématu [sestavování knihovny importu a souboru exportu](building-an-import-library-and-export-file.md).|
|**/ERRORREPORT**| Zastaralé Další informace najdete v tématu [spuštění knihovny LIB](running-lib.md).|
|**/EXPORT**|   Vyexportuje funkci z programu.<br/><br/>Další informace najdete v tématu [sestavování knihovny importu a souboru exportu](building-an-import-library-and-export-file.md).|
|**/EXTRACT**|   Vytvořte soubor objektu (. obj), který obsahuje kopii člena existující knihovny.<br/><br/>Další informace naleznete v tématu [extrahování člena knihovny](extracting-a-library-member.md).|
|**/INCLUDE**|   Přidá symbol do tabulky symbolů.<br/><br/>Další informace najdete v tématu [sestavování knihovny importu a souboru exportu](building-an-import-library-and-export-file.md).|
|**/LIBPATH**|   Přepíše cestu ke knihovně prostředí.<br/><br/>Další informace najdete v tématu [Správa knihovny](managing-a-library.md).|
|**/LINKREPRO**|   Vytvoří artefakty potřebné k reprodukování chyby lib. exe nebo vnitřní chyby.<br/><br/>Další informace najdete v tématu [spuštění knihovny LIB](running-lib.md).|
|**/LINKREPROTARGET**|   Vygeneruje artefakty **/LINKREPRO** pouze v případě, že se soubor LIB. exe používá se zadaným souborem.<br/><br/>Další informace najdete v tématu [spuštění knihovny LIB](running-lib.md).|
|**/LIST**|   Zobrazí informace o výstupní knihovně pro standardní výstup.<br/><br/>Další informace najdete v tématu [Správa knihovny](managing-a-library.md).|
|**/LTCG**|   Způsobí sestavení knihovny pomocí generování kódu při propojování.<br/><br/>Další informace najdete v tématu [spuštění knihovny LIB](running-lib.md).|
|**/MACHINE**|   Určuje cílovou platformu pro program.<br/><br/>Další informace najdete v tématu [spuštění knihovny LIB](running-lib.md).|
|**/NAME**|   Při sestavování knihovny importů Určuje název knihovny DLL, pro kterou je vytvořena knihovna importu.<br/><br/>Další informace najdete v tématu [Správa knihovny](managing-a-library.md).|
|**/NODEFAULTLIB**|   Odebere jednu nebo více výchozích knihoven ze seznamu knihoven, které vyhledává při překladu externích odkazů.<br/><br/>Další informace najdete v tématu [Správa knihovny](managing-a-library.md).|
|**/NOLOGO**|   Potlačí zobrazení zprávy o autorských právech LIB a čísla verze a zabrání v vracení souborů příkazů.<br/><br/>Další informace najdete v tématu [spuštění knihovny LIB](running-lib.md).|
|**/OUT**|   Přepíše výchozí název výstupního souboru.<br/><br/>Další informace najdete v tématu [Správa knihovny](managing-a-library.md).|
|**/REMOVE**|   Vynechá objekt z výstupní knihovny.<br/><br/>Další informace najdete v tématu [Správa knihovny](managing-a-library.md).|
|**/SUBSYSTEM**|   Oznamuje operačnímu systému, jak spustit program vytvořený propojením s výstupní knihovnou.<br/><br/>Další informace najdete v tématu [Správa knihovny](managing-a-library.md).|
|**/VERBOSE**|   Zobrazí podrobnosti o průběhu relace, včetně názvů přidávaných souborů. obj.<br/><br/>Další informace najdete v tématu [spuštění knihovny LIB](running-lib.md).|
|**/WX**|   Považovat upozornění za chyby.<br/><br/>Další informace najdete v tématu [spuštění knihovny LIB](running-lib.md).|

## <a name="see-also"></a>Viz také

[Lib – referenční](lib-reference.md)\
[Vstupní soubory LIB](lib-input-files.md)\
\ [výstupních souborů lib](lib-output-files.md)
[Další výstupy LIB](other-lib-output.md)\
[Struktura knihovny](structure-of-a-library.md)
