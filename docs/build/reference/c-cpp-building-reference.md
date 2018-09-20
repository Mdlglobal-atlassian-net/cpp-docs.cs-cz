---
title: Reference sestavení C/C++ | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- compiling source code [C++], additional information
- cl.exe compiler [C++], building programs
- linker [C++], building reference
- builds [C++], additional information
ms.assetid: 100b4ccf-572c-4d1f-970c-fa0bc0cc0d2d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5935c0642ba0cd69992c68c521d284c3e8733ce4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46390029"
---
# <a name="cc-building-reference"></a>Odkaz sestavení C/C++

Visual C++ nabízí dva způsoby vytvoření programu v jazyce C/C++. Je nejjednodušší (a nejběžnější) způsobem [sestavení v rámci vývojového prostředí Visual C++](../../ide/building-cpp-projects-in-visual-studio.md). Druhý způsob je [sestavení z příkazového řádku pomocí nástroje příkazového řádku](../../build/building-on-the-command-line.md). V obou případech můžete vytvořit pomocí editoru zdrojového kódu jazyka Visual C++ nebo jiného editoru podle vašeho výběru zdrojových souborů.

Pokud program používá souboru pravidel, spíše než soubor .vcxproj, můžete pořád vytvářet ho ve vývojovém prostředí jako [externí projekt](../../ide/building-external-projects.md).

## <a name="in-this-section"></a>V tomto oddílu

[Kompilace programu v jazyce C/C++](../../build/reference/compiling-a-c-cpp-program.md)<br/>
Popisuje kompilátor, který vytvoří objektový soubor obsahující strojového kódu, direktivy linkeru, oddíly, externí odkazy a funkce/dat názvy.

[Propojování](../../build/reference/linking.md)<br/>
Popisuje linkeru, která kombinuje kódu ze souborů objekt vytvořený kompilátorem a ze staticky propojených knihoven, překládá název odkazy a vytvoří spustitelný soubor.

[Sestavení pro vydání](../../build/reference/release-builds.md)<br/>
Uvede informace o tom, proč a kdy chcete změnit z ladění od sestavení k sestavení pro vydání a také popisuje některé z problémů, na které můžete narazit při změně z ladění na sestavení pro vydání.

[Optimalizace kódu](../../build/reference/optimizing-your-code.md)<br/>
Obsahuje odkazy na témata popisující mechanismy pro optimalizaci kódu:

[Nástroje sestavení C/C++](../../build/reference/c-cpp-build-tools.md)<br/>
Poskytuje následující nástroje příkazového řádku pro zobrazení nebo manipulace s výstup sestavení:

[Chyby sestavení C/C++](../../error-messages/compiler-errors-1/c-cpp-build-errors.md)<br/>
Představuje oddíl chyby sestavení v tabulce obsahu.

## <a name="related-sections"></a>Související oddíly

[C/C++ – referenční dokumentace preprocesoru](../../preprocessor/c-cpp-preprocessor-reference.md)<br/>
Tento článek popisuje preprocesor, který připraví zdrojové soubory pro kompilátor překládá makra, operátory a direktivy.

[Seznámení s kroky vlastního sestavení a s událostmi sestavení](../../ide/understanding-custom-build-steps-and-build-events.md)<br/>
Tento článek popisuje přizpůsobení procesu sestavení.

[Sestavení programu v jazyce C/C++](../../build/building-c-cpp-programs.md)<br/>
Obsahuje odkazy na témata popisující vytváření vaší aplikace z příkazového řádku nebo z integrovaného vývojového prostředí sady Visual Studio.

[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)<br/>
Popisuje nastavení možnosti kompilátoru ve vývojovém prostředí nebo na příkazovém řádku.

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
Obsahuje odkazy na témata popisující použití možnosti kompilátoru.

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
Popisuje nastavení možností linkeru uvnitř nebo mimo integrované vývojové prostředí.

[Možnosti linkeru](../../build/reference/linker-options.md)<br/>
Obsahuje odkazy na témata popisující použití možností propojovacího programu.

[BSCMAKE – referenční dokumentace](../../build/reference/bscmake-reference.md)<br/>
Popisuje nástroj údržba informací procházení Microsoft (BSCMAKE. Soubor EXE), která sestavení informačního souboru procházení (.bsc) z .sbr soubory vytvořené během kompilace.

[Referenční dokumentace ke knihovně LIB](../../build/reference/lib-reference.md)<br/>
Popisuje Správce knihovny Microsoft (LIB.exe), který vytváří a spravuje knihovnu objektových souborů Common Object File Format (COFF).

[EDITBIN – referenční dokumentace](../../build/reference/editbin-reference.md)<br/>
Popisuje binární soubor Editor COFF společnosti Microsoft (EDITBIN. Soubor EXE), který upravuje binárních souborů Common Object File Format (COFF).

[DUMPBIN – odkaz](../../build/reference/dumpbin-reference.md)<br/>
Popisuje Microsoft COFF – Vypisovač binárních souborů (DUMPBIN. Soubor EXE), která zobrazí informace o binárních souborů Common Object File Format (COFF).

[NMAKE – referenční zdroje](../../build/nmake-reference.md)<br/>
Popisuje nástroj Údržba programu Microsoft (NMAKE. (EXE), což je nástroj, který sestavuje projekty založené na příkazy, které jsou obsaženy v souboru popisu.