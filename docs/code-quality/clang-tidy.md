---
title: Použití clang-tidy v sadě Visual Studio
description: Použití clang-tidy v sadě Visual Studio pro analýzu kódu Microsoft C++.
ms.date: 02/19/2020
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.clangtidy
author: frozenpandaman
ms.author: efessler
ms.openlocfilehash: ff32f522eaacee67e19aedaa1153b2c68edc98d4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81355150"
---
# <a name="using-clang-tidy-in-visual-studio"></a>Použití clang-tidy v sadě Visual Studio

::: moniker range="<=vs-2017"

Podpora clang-tidy vyžaduje Visual Studio 2019 verze 16.4 nebo novější. Chcete-li zobrazit dokumentaci pro tuto verzi, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end

::: moniker range=">=vs-2019"

Analýza kódu nativně podporuje [Clang-Tidy](https://clang.llvm.org/extra/clang-tidy/) pro projekty MSBuild i CMake, ať už pomocí sad nástrojů Clang nebo MSVC. Clang-Tidy kontroly lze spustit jako součást analýzy kódu pozadí. Zobrazí se jako upozornění v editoru (vlnovky) a zobrazí se v seznamu chyb.

Podpora Clang-Tidy je k dispozici od visual studia 2019 verze 16.4. Je součástí automaticky, když zvolíte zatížení C++ v Instalační službě Visual Studia.

Clang-Tidy je výchozí analytický nástroj při použití sady nástrojů LLVM/clang-cl, která je k dispozici v msbuildi i cmake. Můžete nakonfigurovat při použití sady nástrojů MSVC spustit vedle nebo nahradit standardní prostředí analýzy kódu. Pokud používáte sadu nástrojů clang-cl, microsoft code analysis není k dispozici.

Clang-Tidy běží po úspěšné kompilaci. Možná budete muset vyřešit chyby zdrojového kódu získat clang-tidy výsledky.

## <a name="msbuild"></a>MSBuild

Můžete nakonfigurovat Clang-Tidy spustit jako součást analýzy kódu a sestavení pod stránku**Obecné** **analýzy** > kódu v okně Vlastnosti projektu. Možnosti konfigurace nástroje naleznete v podnabídce Clang-Tidy.

Další informace naleznete v [tématu How to: Set Code Analysis Properties for C/C++ Projects](../code-quality/how-to-set-code-analysis-properties-for-c-cpp-projects.md).

## <a name="cmake"></a>CMake

V projektech CMake můžete nakonfigurovat kontroly Clang-Tidy v rámci `CMakeSettings.json`aplikace . Po otevření klikněte na tlačítko "Upravit JSON" v pravém horním rohu Editoru nastavení projektu CMake. Jsou rozpoznány následující klávesy:

- `enableMicrosoftCodeAnalysis`: Povolí analýzu kódu společnosti Microsoft
- `enableClangTidyCodeAnalysis`: Umožňuje analýzu Clang-Tidy
- `clangTidyChecks`: Konfigurace Clang-Tidy, určená jako seznam oddělený čárkami, to znamená, že má být povolena nebo zakázána

Pokud není zadána ani jedna z možností "povolit", visual studio vybere analytický nástroj odpovídající použité sadě nástrojů platformy.

## <a name="warning-display"></a>Výstražný displej

Clang-Tidy spustí za následek upozornění zobrazené v seznamu chyb a jako in-editor klikyháky pod příslušné části kódu. Pomocí sloupce Kategorie v seznamu chyb můžete seřadit a uspořádat upozornění Clang-Tidy. Upozornění v editoru můžete nakonfigurovat přepnutím nastavení "Zakázat squiggles analýzy kódu" v části**Možnosti** **nástrojů** > .

## <a name="clang-tidy-configuration"></a>Konfigurace Clang-Tidy

Můžete nakonfigurovat kontroly, které clang-tidy běží uvnitř sady Visual Studio pomocí **Clang-Tidy kontroly** možnost. Tento vstup je k dispozici **--checks** argument nástroje. Jakákoli další konfigurace může *`.clang-tidy`* být zahrnuta do vlastních souborů. Další informace naleznete v [dokumentaci Clang-Tidy o LLVM.org](https://clang.llvm.org/extra/clang-tidy/).

## <a name="see-also"></a>Viz také

- [Podpora clang/LLVM pro projekty MSBuild](https://devblogs.microsoft.com/cppblog/clang-llvm-support-for-msbuild-projects/)
- [Podpora Clang/LLVM pro projekty CMake](https://devblogs.microsoft.com/cppblog/visual-studio-cmake-support-clang-llvm-cmake-3-14-vcpkg-and-performance-improvements/)

::: moniker-end
