---
title: Odkaz sestavení C/C++ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- compiling source code [C++], additional information
- cl.exe compiler [C++], building programs
- linker [C++], building reference
- builds [C++], additional information
ms.assetid: 100b4ccf-572c-4d1f-970c-fa0bc0cc0d2d
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9e2269be27dd039357c11d38a2be83b5fc9d6504
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cc-building-reference"></a>Odkaz sestavení C/C++
Visual C++ nabízí dva způsoby vytvoření programu C/C++. Způsob nejjednodušší (a nejběžnější) je [sestavení ve vývojovém prostředí Visual C++](../../ide/building-cpp-projects-in-visual-studio.md). Druhý způsob je [sestavení z příkazového řádku pomocí nástroje příkazového řádku](../../build/building-on-the-command-line.md). V obou případech můžete vytvořit pomocí editoru Visual C++ zdroje nebo třetích stran editoru podle své volby zdrojových souborů.  
  
 Pokud váš program používá souboru pravidel místo souboru, můžete přesto vytvořit ji ve vývojovém prostředí jako [externí projektu](../../ide/building-external-projects.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Kompilace programu v jazyce C/C++](../../build/reference/compiling-a-c-cpp-program.md)  
 Popisuje kompilátoru, který vytvoří soubor objekt obsahující zkompilovaný kód, linkeru direktivy, oddíly, externí odkazy a názvy funkce nebo data.  
  
 [Propojování](../../build/reference/linking.md)  
 Popisuje linkeru, která spojuje kód z objektu soubory vytvořené kompilátoru a staticky propojené knihovny, překládá název odkazy a vytvoří spustitelný soubor.  
  
 [Sestavení pro vydání](../../build/reference/release-builds.md)  
 Uvede informace o proč a kdy chcete změnit z ladění sestavení k sestavení pro vydání a taky popisuje některé potíže, které mohou nastat při změně ladění na sestavení pro vydání.  
  
 [Optimalizace kódu](../../build/reference/optimizing-your-code.md)  
 Obsahuje odkazy na témata pojednávající o mechanismy pro optimalizace kódu:  
  
 [Nástroje sestavení C/C++](../../build/reference/c-cpp-build-tools.md)  
 Poskytuje následující nástroje příkazového řádku pro zobrazení nebo manipulace s výstupu sestavení:  
  
 [Chyby sestavení C/C++](../../error-messages/compiler-errors-1/c-cpp-build-errors.md)  
 Představuje části chyby sestavení v tabulce obsahu.  
  
## <a name="related-sections"></a>Související oddíly  
 [C/C++ – referenční dokumentace preprocesoru](../../preprocessor/c-cpp-preprocessor-reference.md)  
 Popisuje preprocesor, který připraví zdrojové soubory pro kompilátor překladu makra, operátory a direktivy.  
  
 [Seznámení s kroky vlastního sestavení a s událostmi sestavení](../../ide/understanding-custom-build-steps-and-build-events.md)  
 Popisuje přizpůsobení procesu sestavení.  
  
 [Sestavení programu C/C++](../../build/building-c-cpp-programs.md)  
 Obsahuje odkazy na témata popisující sestavení programu z příkazového řádku nebo z integrovaného vývojového prostředí sady Visual Studio.  
  
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)  
 Popisuje možnosti kompilátoru nastavení ve vývojovém prostředí nebo na příkazovém řádku.  
  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)  
 Obsahuje odkazy na témata pojednávající o pomocí možnosti kompilátoru.  
  
 [Nastavení možností linkeru](../../build/reference/setting-linker-options.md)  
 Popisuje možnosti linkeru nastavení uvnitř nebo vně integrované vývojové prostředí.  
  
 [Možnosti linkeru](../../build/reference/linker-options.md)  
 Obsahuje odkazy na témata pojednávající o pomocí možnosti linkeru.  
  
 [BSCMAKE – referenční dokumentace](../../build/reference/bscmake-reference.md)  
 Popisuje nástroj údržba informací procházení Microsoft (BSCMAKE. Soubor EXE), která sestavení soubor s informacemi o procházení (.bsc) z .sbr soubory vytvořené během kompilace.  
  
 [Referenční dokumentace ke knihovně LIB](../../build/reference/lib-reference.md)  
 Popisuje Správce knihovny Microsoft (LIB.exe), které vytváří a spravuje knihovnu běžných objekt souboru formátu () objekt soubory COFF.  
  
 [EDITBIN – referenční dokumentace](../../build/reference/editbin-reference.md)  
 Popisuje Microsoft COFF binární soubor Editor (nástroje EDITBIN. EXE), který upravuje binární soubory běžné objekt souboru formátu (COFF).  
  
 [DUMPBIN – odkaz](../../build/reference/dumpbin-reference.md)  
 Popisuje Vypisovač binárních souborů Microsoft COFF (DUMPBIN. EXE), který zobrazí informace o běžných objekt souboru formátu (COFF) binární soubory.  
  
 [NMAKE – referenční zdroje](../../build/nmake-reference.md)  
 Popisuje nástroj Údržba programu Microsoft (NMAKE. EXE), což je nástroj, který vytvoří projekty založené na příkazy, které jsou obsaženy v souboru popis.