---
title: "Uvolnění knihovny DLL odloženým načtením | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- __FUnloadDelayLoadedDLL2
- delayed loading of DLLs, unloading
ms.assetid: 6463bc71-020e-4aff-a4ca-90360411c54e
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0962059e6e55ce68133960cc9f8d1de8c7f0ef61
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="unloading-a-delay-loaded-dll"></a>Uvolnění knihovny DLL s odloženým načtením
Zadaný výchozí zpoždění zatížení pomocné rutiny zkontroluje Pokud popisovače načtení zpoždění mít v poli pUnloadIAT ukazatel a kopii původní tabulky adres import (IAT). Pokud ano, uloží ukazatel v seznamu do popisovače zpoždění importu. To umožňuje pomocné funkce najít knihovnu DLL podle názvu pro podporu explicitně uvolnění této knihovny DLL.  
  
 Zde jsou přidružené struktury a funkce pro explicitní uvolnění knihovny DLL s odloženým načtením:  
  
```  
//  
// Unload support from delayimp.h  
//  
  
// routine definition; takes a pointer to a name to unload  
  
ExternC  
BOOL WINAPI  
__FUnloadDelayLoadedDLL2(LPCSTR szDll);  
  
// structure definitions for the list of unload records  
typedef struct UnloadInfo * PUnloadInfo;  
typedef struct UnloadInfo {  
    PUnloadInfo     puiNext;  
    PCImgDelayDescr pidd;  
    } UnloadInfo;  
  
// from delayhlp.cpp  
// the default delay load helper places the unloadinfo records in the   
// list headed by the following pointer.  
ExternC  
PUnloadInfo __puiHead;  
```  
  
 Struktura UnloadInfo je implementovaná pomocí C++ třídu, která využívá **LocalAlloc** a **LocalFree** implementace jako jeho operátor **nové** a operátor  **Odstranit** v uvedeném pořadí. Tyto možnosti jsou uchovávány v standardní odkazovaného seznamu pomocí __puiHead jako první pozice v seznamu.  
  
 Volání __FUnloadDelayLoadedDLL se pokusí najít název zadáte v seznamu načíst knihovny DLL (je vyžadována přesná shoda). Pokud je nalezen, je zkopírovat kopii IAT v pUnloadIAT v horní části spuštěné IAT k obnovení jinou bitovou šířku ukazatele, knihovny uvolněno s **FreeLibrary**, shody **UnloadInfo** záznamu je odpojení od v seznamu a odstranit a hodnotu TRUE se vrátí.  
  
 Argument funkce __FUnloadDelayLoadedDLL2 je malá a velká písmena. Například zadali byste:  
  
```  
__FUnloadDelayLoadedDLL2("user32.DLL");  
```  
  
 a ne:  
  
```  
__FUnloadDelayLoadedDLL2("User32.DLL");.  
```  
  
## <a name="see-also"></a>Viz také  
 [Principy pomocné funkce](understanding-the-helper-function.md)