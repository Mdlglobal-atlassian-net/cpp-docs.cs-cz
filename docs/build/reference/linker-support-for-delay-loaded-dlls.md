---
title: Podpora linkeru pro knihovny DLL s odloženým načtením | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- delayed loading of DLLs, linker support
ms.assetid: b2d7e449-2809-42b1-9c90-2c0ca5e31a14
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aea4ca6d5391f71f27d59d0192fcf1f832dd6702
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="linker-support-for-delay-loaded-dlls"></a>Podpora linkeru pro knihovny DLL s odloženým načtením
Visual C++ linkeru teď podporuje zpožděné načítání knihovny DLL. To zbavuje kterou přináší nutnost je potřeba použít funkce Windows SDK **LoadLibrary** a **GetProcAddress** implementovat odložené načtení knihoven DLL.  
  
 Před Visual C++ verze 6.0, jediný způsob, jak načíst knihovny DLL v době běhu byl pomocí **LoadLibrary** a **GetProcAddress**; operačního systému by načíst knihovnu DLL při spustitelný soubor nebo knihovny DLL pomocí byla načtena.  
  
 Od verze Visual C++ verze 6.0, když staticky propojení s knihovnou DLL, poskytuje linkeru možnosti zpoždění načíst knihovnu DLL, dokud program zavolá funkci v této knihovně DLL.  
  
 Aplikaci může pozdržet načtení knihovny DLL pomocí [/DELAYLOAD (zpoždění načíst Import)](../../build/reference/delayload-delay-load-import.md) – možnost linkeru s pomocné funkce (výchozí implementace poskytovaná Visual C++). Pomocné funkce se načíst knihovnu DLL v době běhu voláním **LoadLibrary** a **GetProcAddress** za vás.  
  
 Měli byste zvážit s odloženým načtením knihovny DLL, pokud:  
  
-   Váš program nemusí volání funkce v knihovně DLL.  
  
-   Až v pozdějších spuštění vašeho programu nemusí zavolána funkce v knihovně DLL.  
  
 Zpožděné načítání knihovny DLL lze zadat během vytváření sestavení buď. Soubor EXE nebo. Projektu knihovny DLL. A. Projektu knihovny DLL, která zpozdí načítání knihoven DLL jeden nebo více nesmí samotné volání odloženým načtením vstupní bod v Dllmain.  
  
 Následující témata popisují odloženého načítání knihoven DLL:  
  
-   [Určení knihoven DLL pro odložené načtení](../../build/reference/specifying-dlls-to-delay-load.md)  
  
-   [Explicitní uvolnění knihovny DLL načtené se zpožděním](../../build/reference/explicitly-unloading-a-delay-loaded-dll.md)  
  
-   [Načtení všech importů pro knihovnu DLL se zpožděným načtením](../../build/reference/loading-all-imports-for-a-delay-loaded-dll.md)  
  
-   [Import vazeb](../../build/reference/binding-imports.md)  
  
-   [Zpracování chyb a oznámení](../../build/reference/error-handling-and-notification.md)  
  
-   [Výpis importu se zpožděným načtením](../../build/reference/dumping-delay-loaded-imports.md)  
  
-   [Omezení odloženého načítání knihoven DLL](../../build/reference/constraints-of-delay-loading-dlls.md)  
  
-   [Základní informace o podpůrné funkci](understanding-the-helper-function.md)  
  
-   [Vývoj vlastní pomocné funkce](../../build/reference/developing-your-own-helper-function.md)  
  
## <a name="see-also"></a>Viz také  
 [Knihovny DLL v jazyce Visual C++](../../build/dlls-in-visual-cpp.md)   
 [Propojování](../../build/reference/linking.md)