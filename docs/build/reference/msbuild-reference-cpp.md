---
title: Referenční dokumentace nástroje MSBuild pro projekty C++ v sadě Visual Studio
ms.date: 12/08/2018
helpviewer_keywords:
- MSBuild reference [C++]
ms.openlocfilehash: 854dc0554c327f191b4b4b9694548cdb9983c5f8
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823097"
---
# <a name="msbuild-reference-for-c-projects"></a>Referenční dokumentace nástroje MSBuild pro projekty v jazyce C++

Nástroj MSBuild je systém nativní sestavení pro všechny projekty v sadě Visual Studio, včetně projektů v jazyce C++. Při vytváření projektu v sadě Visual Studio integrované vývojové prostředí (IDE), vyvolá nástroj msbuild.exe, která zase využívá souboru .vcxproj projektu a různé soubory .targets a .props. Obecně platí důrazně doporučujeme používat Visual Studio IDE k nastavení vlastností projektu a vyvolání MSBuild. Ruční úpravy souborů projektu může vést k vážným problémům, není-li prováděn správně.

Pokud z nějakého důvodu chcete použít nástroj MSBuild přímo z příkazového řádku, naleznete v tématu [pomocí nástroje MSBuild z příkazového řádku](../msbuild-visual-cpp.md). Další informace o nástroji MSBuild, naleznete v tématu [MSBuild](/visualstudio/msbuild/msbuild) v dokumentaci k sadě Visual Studio.

## <a name="in-this-section"></a>V tomto oddílu

[Interní informace o MSBuild pro projekty v jazyce C++](msbuild-visual-cpp-overview.md)<br/>
Informace o tom, jak jsou vlastnosti a cíle ukládat a používat.

[Běžná makra pro příkazy a vlastnosti sestavení](common-macros-for-build-commands-and-properties.md)<br/>
Popisuje makra (konstanty z doby kompilace), které lze použít k definování vlastností, jako je například cest a verzí produktu.

[Typy souborů vytvořených pro projekty v jazyce C++](file-types-created-for-visual-cpp-projects.md)<br/>
Popisuje různé typy souborů, které sada Visual Studio vytvoří pro různé typy projektů.

[Šablony projektů sady Visual Studio C++](visual-cpp-project-types.md)<br>
Popisuje typy založené na MSBuild projektů, které jsou k dispozici pro jazyk C++.

[Nová položka šablony jazyka C++](using-visual-cpp-add-new-item-templates.md)<br>
Popisuje zdrojové soubory a další položky, které přidáte do projektu sady Visual Studio.

[Předkompilované soubory hlaviček](../creating-precompiled-header-files.md) způsob použití předkompilované hlavičkové soubory a jak vytvořit vlastní předkompilovaný kód urychlit sestavování.

[Referenční dokumentace vlastností projektu Visual Studio](property-pages-visual-cpp.md)<br/>
Referenční dokumentace pro vlastnosti projektu, které jsou nastavené v integrovaném vývojovém prostředí sady Visual Studio.

## <a name="see-also"></a>Viz také

[Referenční zdroje k sestavení programu v jazyce C/C++](c-cpp-building-reference.md)