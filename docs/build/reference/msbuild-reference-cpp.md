---
title: Odkaz msbuild pro projekty jazyka C++ v sadě Visual Studio
ms.date: 12/08/2018
helpviewer_keywords:
- MSBuild reference [C++]
ms.openlocfilehash: 96987a252d12f718025dd55deecad5c6bac26872
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336213"
---
# <a name="msbuild-reference-for-c-projects"></a>Referenční zdroje k nástroji MSBuild pro projekty C++

MSBuild je nativní systém sestavení pro všechny projekty v sadě Visual Studio, včetně projektů jazyka C++. Při vytváření projektu v integrovaném vývojovém prostředí sady Visual Studio (IDE) vyvolá nástroj msbuild.exe, který zase spotřebovává soubor projektu .vcxproj a různé soubory .targets a .props. Obecně důrazně doporučujeme použít IDE visual studio nastavit vlastnosti projektu a vyvolat MSBuild. Ruční úprava souborů projektu může vést k vážným problémům, pokud není provedena správně.

Pokud z nějakého důvodu chcete msbuild použít přímo z příkazového řádku, přečtěte si část [Použití msbuildu z příkazového řádku](../msbuild-visual-cpp.md). Další informace o MSBuild obecně naleznete v tématu [MSBuild](/visualstudio/msbuild/msbuild) v dokumentaci k sadě Visual Studio.

## <a name="in-this-section"></a>V tomto oddílu

[Vnitřní fungování nástroje MSBuild pro projekty C++](msbuild-visual-cpp-overview.md)<br/>
Informace o tom, jak jsou uloženy a spotřebovány vlastnosti a cíle.

[Společná makra pro příkazy a vlastnosti sestavení](common-macros-for-build-commands-and-properties.md)<br/>
Popisuje makra (konstanty v době kompilace), které lze použít k definování vlastností, jako jsou cesty a verze produktu.

[Typy souborů vytvořené pro projekty jazyka C++](file-types-created-for-visual-cpp-projects.md)<br/>
Popisuje různé druhy souborů, které visual studio vytvoří pro různé typy projektů.

[Šablony projektů Visual Studio C++](visual-cpp-project-types.md)<br>
Popisuje typy projektů založené na MSBuild, které jsou k dispozici pro C++.

[Šablony nových položek v C++](using-visual-cpp-add-new-item-templates.md)<br>
Popisuje zdrojové soubory a další položky, které můžete přidat do projektu sady Visual Studio.

[Předkompilované soubory hlaviček](../creating-precompiled-header-files.md) Jak používat předkompilované soubory hlaviček a jak vytvořit vlastní předkompilovaný kód pro urychlení doby sestavení.

[Referenční vlastnost projektu sady Visual Studio](property-pages-visual-cpp.md)<br/>
Referenční dokumentace pro vlastnosti projektu, které jsou nastaveny v ide sady Visual Studio.

## <a name="see-also"></a>Viz také

[Odkaz sestavení C/C++](c-cpp-building-reference.md)
