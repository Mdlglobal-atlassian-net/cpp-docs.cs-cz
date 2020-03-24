---
title: Referenční dokumentace nástroje C++ MSBuild pro projekty v aplikaci Visual Studio
ms.date: 12/08/2018
helpviewer_keywords:
- MSBuild reference [C++]
ms.openlocfilehash: ec1285a760d438a94863181a1b099e6db153c268
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168899"
---
# <a name="msbuild-reference-for-c-projects"></a>Referenční zdroje k nástroji MSBuild pro projekty C++

MSBuild je nativní sestavovací systém pro všechny projekty v aplikaci Visual Studio, včetně C++ projektů. Při sestavení projektu v integrovaném vývojovém prostředí (IDE) sady Visual Studio vyvolá nástroj MSBuild. exe, který zase používá soubor projektu. vcxproj, a různé soubory. targets a. props. Obecně doporučujeme, abyste pomocí prostředí Visual Studio IDE nastavili vlastnosti projektu a vyvolali MSBuild. Ruční úprava souborů projektu může vést k vážným problémům, pokud není provedeno správně.

Pokud z nějakého důvodu chcete použít MSBuild přímo z příkazového řádku, přečtěte si téma [použití nástroje MSBuild z příkazového řádku](../msbuild-visual-cpp.md). Další informace o nástroji MSBuild obecně naleznete v tématu [MSBuild](/visualstudio/msbuild/msbuild) v dokumentaci k sadě Visual Studio.

## <a name="in-this-section"></a>V tomto oddílu

[Vnitřní fungování nástroje MSBuild pro projekty C++](msbuild-visual-cpp-overview.md)<br/>
Informace o tom, jak vlastnosti a cíle jsou uloženy a spotřebovány.

[Běžná makra pro příkazy a vlastnosti sestavení](common-macros-for-build-commands-and-properties.md)<br/>
Popisuje makra (konstanty při kompilaci), které lze použít k definování vlastností, jako jsou například cesty a verze produktu.

[Typy souborů vytvořené pro C++ projekty](file-types-created-for-visual-cpp-projects.md)<br/>
Popisuje různé druhy souborů, které Visual Studio vytvoří pro různé typy projektů.

[Šablony projektů C++ sady Visual Studio](visual-cpp-project-types.md)<br>
Popisuje typy projektů založené na MSBuild, které jsou k dispozici pro C++.

[Šablony nových položek v C++](using-visual-cpp-add-new-item-templates.md)<br>
Popisuje zdrojové soubory a další položky, které lze přidat do projektu aplikace Visual Studio.

[Předkompilované hlavičkové soubory](../creating-precompiled-header-files.md) Jak používat předkompilované hlavičkové soubory a jak vytvořit vlastní předkompilovaný kód pro urychlení časů sestavení.

[Referenční dokumentace k vlastnostem projektu sady Visual Studio](property-pages-visual-cpp.md)<br/>
Referenční dokumentace k vlastnostem projektu, které jsou nastaveny v integrovaném vývojovém prostředí sady Visual Studio.

## <a name="see-also"></a>Viz také

[Referenční zdroje k sestavení programu v jazyce C/C++](c-cpp-building-reference.md)
