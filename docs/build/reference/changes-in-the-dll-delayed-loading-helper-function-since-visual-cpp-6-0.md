---
title: "Změny v knihovně DLL odložené načtení pomocné funkce od Visual C++ verze 6.0 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- delayed loading of DLLs, what's changed
- PFromRva method
- __delayLoadHelper2 function
- helper functions, what's changed
ms.assetid: 99f0be69-105d-49ba-8dd5-3be7939c0c72
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b3123a722e0e95119a4b04f5c060bd947b987cdf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="changes-in-the-dll-delayed-loading-helper-function-since-visual-c-60"></a>Změny v podpůrné funkci knihovny DLL s odloženým načtením od aplikace Visual C++ verze 6.0
Pokud máte více verzí aplikace Visual C++ v počítači, nebo pokud jste definovali vlastní pomocné funkce, které mohou být ovlivněny změny provedené na knihovnu DLL odložené načtení pomocné funkce. Příklad:  
  
-   **__delayloadhelper –** je nyní **__delayloadhelper2 –**  
  
-   **__pfnDliNotifyHook** je nyní **__pfnDliNotifyHook2**  
  
-   **__pfnDliFailureHook** je nyní **__pfnDliFailureHook2**  
  
-   **__FUnloadDelayLoadedDLL** je nyní **__FUnloadDelayLoadedDLL2**  
  
> [!NOTE]
>  Pokud používáte výchozí pomocné funkce, neovlivní tyto změny vám. Neexistují žádné změny o tom, jak vyvolání linkeru.  
  
## <a name="multiple-versions-of-visual-c"></a>Více verzí aplikace Visual C++  
 Pokud máte více verzí aplikace Visual C++ v počítači, ujistěte se, že linkeru odpovídá delayimp.lib. Pokud došlo k neshodě, zobrazí se linkeru zpráv o chybách buď `___delayLoadHelper2@8` nebo `___delayLoadHelper@8` ve formě nerozpoznané externí symbolu. První znamená nové linkeru s původním delayimp.lib a k tomu znamená původní linkeru s novou delayimp.lib.  
  
 Pokud dojde k chybě nerozpoznané linkeru, spusťte [dumpbin /linkermember](../../build/reference/linkermember.md): 1 na delayimp.lib, který bude obsahovat pomocné funkce zobrazíte funkci pomocné rutiny, která je definována místo. Pomocné funkce mohou být také definovány v souboru objektu; Spustit [dumpbin /symbols](../../build/reference/symbols.md) a vyhledejte `delayLoadHelper(2)`.  
  
 Pokud víte, že máte Visual C++ verze 6.0 linkeru, pak:  
  
-   Spuštění nástroje dumpbin na pomocné rutiny zatížení zpoždění .lib nebo .obj soubor k určení, zda definuje **__delayloadhelper2 –**. Pokud ne, propojení se nezdaří.  
  
-   Definování **__delayloadhelper –** v zpoždění načíst soubor .lib nebo .obj na pomocné rutiny.  
  
## <a name="user-defined-helper-function"></a>Uživatelem definované pomocné funkce  
 Pokud není definovaný vlastní pomocné funkce a použití aktuální verze aplikace Visual C++, postupujte takto:  
  
-   Podpůrná funkce pro přejmenování **__delayloadhelper2 –**.  
  
-   Vzhledem k tomu, že následující ukazatele v popisovači zpoždění (ImgDelayDescr v delayimp.h) se liší od absolutní adresy (poplašného) na relativní adresy (RVAs) fungoval podle očekávání v obou programů 32 - a 64-bit, budete muset převést tyto zpět na ukazatele. Je zavedený novou funkci: pfromrva –, v delayhlp.cpp nalezen. Tuto funkci můžete použít na každé pole v popisovači je převést zpět na buď 32 nebo 64-bit ukazatele. Podpůrná funkce výchozí zpoždění zatížení nadále funkční šablonu pro použití jako příklad.  
  
## <a name="load-all-imports-for-a-delay-loaded-dll"></a>Načtení všech importů pro knihovnu DLL s odloženým načtením  
 Linkeru můžete načtení všech importů z knihovny DLL, který jste zadali jako zpoždění načíst. V tématu [načtení všech importů pro knihovnu DLL Delay-Loaded](../../build/reference/loading-all-imports-for-a-delay-loaded-dll.md) Další informace.  
  
## <a name="see-also"></a>Viz také  
 [Základní informace o podpůrné funkci](understanding-the-helper-function.md)