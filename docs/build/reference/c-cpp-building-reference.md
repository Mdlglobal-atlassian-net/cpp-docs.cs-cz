---
title: Reference sestavení C/C++ – Visual Studio
description: Referenční obsah pro nástroje systému a sestavení projektů jazyka C/C++ v sadě Visual Studio.
ms.date: 12/10/2018
helpviewer_keywords:
- compiling source code [C++], additional information
- cl.exe compiler [C++], building programs
- linker [C++], building reference
- builds [C++], additional information
ms.assetid: 100b4ccf-572c-4d1f-970c-fa0bc0cc0d2d
ms.openlocfilehash: 4c3f7aa598a9c43af04c148ed0d4b3f555566ec7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62294756"
---
# <a name="cc-building-reference"></a>Odkaz sestavení C/C++

Visual C++ nabízí dva způsoby vytvoření programu v jazyce C/C++. Je nejjednodušší (a nejběžnější) způsobem [sestavení v integrovaném vývojovém prostředí sady Visual Studio](../creating-and-managing-visual-cpp-projects.md). Druhý způsob je [sestavení z příkazového řádku pomocí nástroje příkazového řádku](../building-on-the-command-line.md). V obou případech můžete vytvořit a upravit zdrojových souborů pomocí sady Visual Studio nebo jiného editoru podle vašeho výběru.

## <a name="in-this-section"></a>V tomto oddílu

[Referenční zdroje k nástroji MSBuild pro projekty C++](msbuild-visual-cpp-overview.md)

[Referenční zdroje ke kompilátorům MSVC](compiling-a-c-cpp-program.md)<br/>
Popisuje kompilátor MSVC, která vytvoří objektový soubor obsahující strojového kódu, direktivy linkeru, oddíly, externí odkazy a funkce/dat názvy.

[Referenční zdroje k linkeru MSVC](linking.md)<br/>
Popisuje linkeru, která kombinuje kódu ze souborů objekt vytvořený kompilátorem a ze staticky propojených knihoven, překládá název odkazy a vytvoří spustitelný soubor.

[Podpora kódování Unicode v kompilátoru a linkeru](unicode-support-in-the-compiler-and-linker.md)

[Nástroje pro vytváření dalších MSVC](c-cpp-build-tools.md)<br/>
Další nástroje příkazového řádku jazyka C++.

[Chyby sestavení C/C++](../../error-messages/compiler-errors-1/c-cpp-build-errors.md)<br/>
Představuje oddíl chyby sestavení v tabulce obsahu.

## <a name="related-sections"></a>Související oddíly

[C/C++ – referenční dokumentace preprocesoru](../../preprocessor/c-cpp-preprocessor-reference.md)<br/>
Tento článek popisuje preprocesor, který připraví zdrojové soubory pro kompilátor překládá makra, operátory a direktivy.

[Seznámení s kroky vlastního sestavení a s událostmi sestavení](../understanding-custom-build-steps-and-build-events.md)<br/>
Tento článek popisuje přizpůsobení procesu sestavení.

[Sestavení programu v jazyce C/C++](../projects-and-build-systems-cpp.md)<br/>
Obsahuje odkazy na témata popisující vytváření vaší aplikace z příkazového řádku nebo z integrovaného vývojového prostředí sady Visual Studio.

[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)<br/>
Popisuje nastavení možnosti kompilátoru ve vývojovém prostředí nebo na příkazovém řádku.

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
Obsahuje odkazy na témata popisující použití možnosti kompilátoru.

[Referenční zdroje k linkeru MSVC](linking.md)<br/>
Popisuje nastavení možností linkeru uvnitř nebo mimo integrované vývojové prostředí.

[Možnosti linkeru MSVC](linker-options.md)<br/>
Obsahuje odkazy na témata popisující použití možností propojovacího programu.

[BSCMAKE – referenční dokumentace](bscmake-reference.md)<br/>
Popisuje nástroj údržba informací procházení Microsoft (BSCMAKE. Soubor EXE), která sestavení informačního souboru procházení (.bsc) z .sbr soubory vytvořené během kompilace.

[Referenční dokumentace ke knihovně LIB](lib-reference.md)<br/>
Popisuje Správce knihovny Microsoft (LIB.exe), který vytváří a spravuje knihovnu objektových souborů Common Object File Format (COFF).

[EDITBIN – referenční dokumentace](editbin-reference.md)<br/>
Popisuje binární soubor Editor COFF společnosti Microsoft (EDITBIN. Soubor EXE), který upravuje binárních souborů Common Object File Format (COFF).

[DUMPBIN – odkaz](dumpbin-reference.md)<br/>
Popisuje Microsoft COFF – Vypisovač binárních souborů (DUMPBIN. Soubor EXE), která zobrazí informace o binárních souborů Common Object File Format (COFF).

[NMAKE – referenční zdroje](nmake-reference.md)<br/>
Popisuje nástroj Údržba programu Microsoft (NMAKE. (EXE), což je nástroj, který sestavuje projekty založené na příkazy, které jsou obsaženy v souboru popisu.
