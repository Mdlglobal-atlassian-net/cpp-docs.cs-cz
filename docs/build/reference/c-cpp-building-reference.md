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
ms.openlocfilehash: 116ddca6ed9f5e0b3ea02652958931f88cc8fc13
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45703219"
---
# <a name="cc-building-reference"></a>Odkaz sestavení C/C++

Visual C++ nabízí dva způsoby vytvoření programu v jazyce C/C++. Je nejjednodušší (a nejběžnější) způsobem [sestavení v rámci vývojového prostředí Visual C++](../../ide/building-cpp-projects-in-visual-studio.md). Druhý způsob je [sestavení z příkazového řádku pomocí nástroje příkazového řádku](../../build/building-on-the-command-line.md). V obou případech můžete vytvořit pomocí editoru zdrojového kódu jazyka Visual C++ nebo jiného editoru podle vašeho výběru zdrojových souborů.

Pokud program používá souboru pravidel, spíše než soubor .vcxproj, můžete pořád vytvářet ho ve vývojovém prostředí jako [externí projekt](../../ide/building-external-projects.md).

## <a name="in-this-section"></a>V tomto oddílu

[Kompilace programu v jazyce C/C++](../../build/reference/compiling-a-c-cpp-program.md) popisuje kompilátor, který vytvoří objektový soubor obsahující strojového kódu, direktivy linkeru, oddíly, externí odkazy a funkce/dat názvy.

[Propojení](../../build/reference/linking.md) popisuje linkeru, která kombinuje kódu ze souborů objekt vytvořený kompilátorem a ze staticky propojených knihoven, překládá název odkazy a vytvoří spustitelný soubor.

[Sestavení pro vydání](../../build/reference/release-builds.md) prezentuje informace o tom, proč a kdy chcete změnit ze sestavení pro ladění k sestavení pro vydání a také popisuje některé z problémů, kterým může dojít při přepnutí z ladění na sestavení pro vydání.

[Optimalizace kódu](../../build/reference/optimizing-your-code.md) obsahuje odkazy na témata popisující mechanismy pro optimalizaci kódu:

[Nástroje sestavení C/C++](../../build/reference/c-cpp-build-tools.md) poskytuje následující nástroje příkazového řádku pro zobrazení nebo manipulace s výstup sestavení:

[Chyby sestavení C/C++](../../error-messages/compiler-errors-1/c-cpp-build-errors.md) zavádí oddíl chyby sestavení v tabulce obsahu.

## <a name="related-sections"></a>Související oddíly

[Reference preprocesoru C/C++](../../preprocessor/c-cpp-preprocessor-reference.md) popisuje preprocesor, který připraví zdrojové soubory pro kompilátor překládá makra, operátory a direktivy.

[Kroky sestavení vlastní principy a události sestavení](../../ide/understanding-custom-build-steps-and-build-events.md) popisuje přizpůsobení procesu sestavení.

[Sestavení programu v jazyce C/C++](../../build/building-c-cpp-programs.md) obsahuje odkazy na témata popisující vytváření vaší aplikace z příkazového řádku nebo z integrovaného vývojového prostředí sady Visual Studio.

[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md) popisuje nastavení možnosti kompilátoru ve vývojovém prostředí nebo na příkazovém řádku.

[Možnosti kompilátoru](../../build/reference/compiler-options.md) obsahuje odkazy na témata popisující použití možnosti kompilátoru.

[Nastavení možností Linkeru](../../build/reference/setting-linker-options.md) popisuje nastavení možností linkeru uvnitř nebo mimo integrované vývojové prostředí.

[Možnosti linkeru](../../build/reference/linker-options.md) obsahuje odkazy na témata popisující použití možností propojovacího programu.

[BscMake – referenční dokumentace](../../build/reference/bscmake-reference.md) popisuje Nástroj Údržba informací procházení Microsoft (BSCMAKE. Soubor EXE), která sestavení informačního souboru procházení (.bsc) z .sbr soubory vytvořené během kompilace.

[Referenční dokumentace knihovny LIB](../../build/reference/lib-reference.md) popisuje správce knihovny Microsoft (LIB.exe), který vytváří a spravuje knihovnu objektových souborů Common Object File Format (COFF).

[Editbin – referenční dokumentace](../../build/reference/editbin-reference.md) popisuje Editor Microsoft COFF binární soubor (EDITBIN. Soubor EXE), který upravuje binárních souborů Common Object File Format (COFF).

[DUMPBIN – odkaz](../../build/reference/dumpbin-reference.md) popisuje Microsoft COFF – Vypisovač binárních souborů (DUMPBIN. Soubor EXE), která zobrazí informace o binárních souborů Common Object File Format (COFF).

[NMake – odkaz](../../build/nmake-reference.md) popisuje Nástroj Údržba programu Microsoft (NMAKE. (EXE), což je nástroj, který sestavuje projekty založené na příkazy, které jsou obsaženy v souboru popisu.