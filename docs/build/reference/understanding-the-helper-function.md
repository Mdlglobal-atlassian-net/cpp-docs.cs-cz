---
title: "Principy pomocné funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- delayed loading of DLLs, helper function
- __delayLoadHelper2 function
- delayimp.lib
- __delayLoadHelper function
- delayhlp.cpp
- delayimp.h
- helper functions
ms.assetid: 6279c12c-d908-4967-b0b3-cabfc3e91d3d
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c3a013cf584c37f84331a5ab5dfe74eaa213c851
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="understanding-the-helper-function"></a>Základní informace o podpůrné funkci
Podpůrná funkce pro podporované linkeru zpožděné načítání je co ve skutečnosti knihovnu DLL načte, v době běhu. Pomocné funkce přizpůsobit své chování tak, že zápis vlastní funkce a propojení s vaším programem místo pomocí zadané pomocné funkce v Delayimp.lib, můžete upravit. Jeden pomocné funkce slouží všechny knihovny DLL načtené zpoždění.  
  
 Pokud budete chtít provést zpracování specifické podle názvů knihovny DLL nebo importy, můžete zadat vlastní verzi pomocné funkce.  
  
 Pomocné funkce provede následující akce:  
  
-   Kontroluje uložené popisovač do knihovny a zjistěte, pokud již byl načten  
  
-   Volání **LoadLibrary** k pokusu o načtení knihovny DLL  
  
-   Volání **GetProcAddress** k pokusu o získání adresu procedury  
  
-   Vrátí k importu zpoždění načíst převodu volat nyní načíst vstupního bodu  
  
 Pomocné funkce můžete volat zpět k háku oznámení v programu po každém z následujících akcí:  
  
-   Při spuštění pomocné funkce  
  
-   Těsně před **LoadLibrary** je volána v podpůrné funkci  
  
-   Těsně před **GetProcAddress** je volána v podpůrné funkci  
  
-   Pokud volání **LoadLibrary** v pomocné funkce se nezdařilo  
  
-   Pokud volání **GetProcAddress** v pomocné funkce se nezdařilo  
  
-   Po pomocné rutiny funkce provádí zpracování  
  
 Každá z těchto bodů napojit může vrátit hodnotu, která bude úpravu normálního zpracování pomocnou rutinou nějakým způsobem kromě návratu do převodu zatížení import zpoždění.  
  
 Kód pomocného objektu výchozí naleznete v Delayhlp.cpp a Delayimp.h (v vc\include) a kompiluje v Delayimp.lib (v vc\lib). Je potřeba zahrnout do vaší kompilace této knihovny, pokud můžete psát vlastní pomocné funkce.  
  
 Následující témata popisují pomocné funkce:  
  
-   [Změny v podpůrné funkci knihovny DLL s odloženým načtením od aplikace Visual C++ verze 6.0](../../build/reference/changes-in-the-dll-delayed-loading-helper-function-since-visual-cpp-6-0.md)  
  
-   [Konvence volání, parametry a návratový typ](../../build/reference/calling-conventions-parameters-and-return-type.md)  
  
-   [Struktura a definice konstant](../../build/reference/structure-and-constant-definitions.md)  
  
-   [Výpočet nezbytných hodnot](../../build/reference/calculating-necessary-values.md)  
  
-   [Uvolnění knihovny DLL s odloženým načtením](../../build/reference/explicitly-unloading-a-delay-loaded-dll.md)  
  
## <a name="see-also"></a>Viz také  
 [Podpora linkeru pro knihovny DLL s odloženým načtením](../../build/reference/linker-support-for-delay-loaded-dlls.md)