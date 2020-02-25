---
title: Použití Clang-uklizený v aplikaci Visual Studio
description: Jak používat Clang-uklizený v aplikaci Visual Studio pro analýzu C++ kódu společnosti Microsoft.
ms.date: 02/19/2020
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.clangtidy
author: frozenpandaman
ms.author: efessler
ms.openlocfilehash: 3dbe66e9d7117c027c0ec867011189824c59ce31
ms.sourcegitcommit: 21e168731b8fe0eaff18f070cee5d54aa5782c2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/24/2020
ms.locfileid: "77567875"
---
# <a name="using-clang-tidy-in-visual-studio"></a>Použití Clang-uklizený v aplikaci Visual Studio

::: moniker range="<=vs-2017"

Podpora pro Clang-uklizený vyžaduje Visual Studio 2019 verze 16,4 nebo novější. Pokud si chcete prohlédnout dokumentaci, vyberte v selektoru verze dokumentace možnost Visual Studio 2019.

::: moniker-end

::: moniker range=">=vs-2019"

Analýza kódu nativně podporuje [Clang-uklizený](https://clang.llvm.org/extra/clang-tidy/) pro projekty MSBuild i cmake bez ohledu na to, jestli používáte sady nástrojů pro CLANG nebo MSVC. Clang-uklizený kontroly mohou běžet jako součást analýzy kódu na pozadí. Zobrazují se jako upozornění v editoru (vlnovky) a zobrazují se v Seznam chyb.

Podpora Clang-uklizený je k dispozici počínaje verzí Visual Studio 2019 verze 16,4. Je automaticky zahrnutý při výběru C++ úlohy v instalační program pro Visual Studio.

Clang-uklizený je výchozím nástrojem analýzy při použití sady nástrojů LLVM/Clang-CL, která je dostupná jak v MSBuild, tak i v CMaki. Můžete ji nakonfigurovat při použití sady nástrojů MSVC ke spuštění společně nebo nahradit standardní prostředí pro analýzu kódu. Pokud používáte sadu nástrojů Clang-CL, analýza kódu společnosti Microsoft není k dispozici.

Clang-uklizený se spustí po úspěšné kompilaci. Možná budete muset vyřešit chyby zdrojového kódu a získat výsledky Clang-uklizený.

## <a name="msbuild"></a>MSBuild

Clang-uklizený můžete nakonfigurovat tak, aby běžela jako součást analýzy kódu a sestavení pod stránkou **obecné** > pro **analýzu kódu** v projektu okno Vlastnosti. Možnosti pro konfiguraci tohoto nástroje najdete v podnabídce Clang-uklizený.

Další informace naleznete v tématu [Postupy: nastavení vlastností analýzy kódu pro projekty C/C++ ](../code-quality/how-to-set-code-analysis-properties-for-c-cpp-projects.md).

## <a name="cmake"></a>CMake

V projektech CMake můžete nakonfigurovat kontroly Clang-uklizený v rámci `CMakeSettings.json`. Po otevření klikněte na Upravit JSON v pravém horním rohu editoru nastavení projektu CMake. Rozpoznávají se tyto klíče:

- `enableMicrosoftCodeAnalysis`: povolí analýzu kódu společnosti Microsoft.
- `enableClangTidyCodeAnalysis`: povoluje analýzu Clang-uklizený.
- `clangTidyChecks`: Konfigurace Clang-uklizený zadaná jako seznam oddělený čárkami, to znamená, že šeky budou povolené nebo zakázané.

Pokud není zadána žádná z možností "Enable", sada Visual Studio vybere Nástroj pro analýzu, který odpovídá použité sadě nástrojů platformy.

## <a name="warning-display"></a>Zobrazení upozornění

Clang-uklizený spustí výsledek v upozorněních zobrazených v Seznam chyb a jako editor vlnovek pod relevantními částmi kódu. Použijte sloupec Category v Seznam chyb k řazení a uspořádání upozornění Clang-uklizený. Můžete nakonfigurovat upozornění v editoru tak, že v nabídce **nástroje** > **Možnosti**zakážete nastavení zakázat vlnovky analýzy kódu.

## <a name="clang-tidy-configuration"></a>Konfigurace Clang-uklizený

Můžete nakonfigurovat kontroly, které Clang-uklizený spouští v rámci sady Visual Studio prostřednictvím možnosti **Clang-uklizený Checks** . Tento vstup je poskytován argumentem **--Checks** nástroje. Jakákoli další konfigurace může být součástí vlastních *`.clang-tidy`* souborů. Další informace najdete v dokumentaci k [Clang-uklizený v LLVM.org](https://clang.llvm.org/extra/clang-tidy/).

## <a name="see-also"></a>Viz také

- [Podpora Clang/LLVM pro projekty MSBuild](https://devblogs.microsoft.com/cppblog/clang-llvm-support-for-msbuild-projects/)
- [Podpora Clang/LLVM pro projekty CMake](https://devblogs.microsoft.com/cppblog/visual-studio-cmake-support-clang-llvm-cmake-3-14-vcpkg-and-performance-improvements/)

::: moniker-end
