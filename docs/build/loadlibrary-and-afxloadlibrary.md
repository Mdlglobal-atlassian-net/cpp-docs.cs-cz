---
title: LoadLibrary a AfxLoadLibrary | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: LoadLibrary
dev_langs: C++
helpviewer_keywords:
- DLLs [C++], AfxLoadLibrary
- DLLs [C++], LoadLibrary
- AfxLoadLibrary method
- LoadLibrary method
- explicit linking [C++]
ms.assetid: b4535d19-6243-4146-a31a-a5cca4c7c9e3
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7de79303e414691df7b069b55b82b2ba39f6ea1e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="loadlibrary-and-afxloadlibrary"></a>LoadLibrary a AfxLoadLibrary
Zpracovává volání [LoadLibrary](http://go.microsoft.com/fwlink/p/?LinkID=259187) (nebo [AfxLoadLibrary](../mfc/reference/application-information-and-management.md#afxloadlibrary)) explicitně propojit s knihovnou DLL. Pokud funkci úspěšné, mapuje zadané DLL do adresního prostoru volajícího procesu a vrátí popisovač pro knihovnu DLL, kterou lze použít s jinými funkcemi v explicitní propojování – například `GetProcAddress` a `FreeLibrary`.  
  
 `LoadLibrary`pokusí se najít knihovnu DLL pomocí stejné pořadí hledání, který se používá pro implicitní propojení. Pokud systém nemůže najít knihovnu DLL nebo pokud vstupní bod funkce vrátí hodnotu FALSE, `LoadLibrary` vrátí hodnotu NULL. Pokud volání `LoadLibrary` Určuje modul knihovny DLL, která je již namapována do adresním prostoru procesu volání funkce vrátí popisovač DLL a zvýší počet odkazů modulu.  
  
 Pokud knihovnu DLL má funkci vstupního bodu, operační systém zavolá funkci v kontextu vláken, která volá `LoadLibrary`. Funkce vstupního bodu není volána, pokud knihovnu DLL je již připojen k proces z důvodu předchozích volání `LoadLibrary` má bez odpovídajícího volání `FreeLibrary` funkce.  
  
 Pro aplikace MFC, které načítají MFC – rozšiřující knihovny DLL, doporučujeme použít `AfxLoadLibrary` místo `LoadLibrary`. `AfxLoadLibrary`Synchronizace vláken popisovače před voláním `LoadLibrary`. Rozhraní (prototyp funkce) pro `AfxLoadLibrary` je stejný jako `LoadLibrary`.  
  
 Pokud systém Windows nemůže načíst knihovnu DLL, můžete proces pokusí o zotavení z chyby. Proces může například upozornit uživatele chyby a požádat uživatele o zadejte jinou cestu ke knihovně DLL.  
  
> [!IMPORTANT]
>  Pokud je kód pro spuštění v systému Windows NT 4, Windows 2000 nebo Windows XP (před aktualizací SP1), nezapomeňte zadat celou cestu všechny knihovny DLL. V těchto operačních systémech je aktuální adresář vyhledávat nejprve při soubory jsou načteny. Pokud nemáte kvalifikovanou cestu k souboru, soubor, který není zamýšlené může načíst.  
  
## <a name="what-do-you-want-to-do"></a>Co chcete udělat?  
  
-   [Postup propojení implicitně s knihovny DLL](../build/linking-an-executable-to-a-dll.md#linking-implicitly)  
  
-   [Rozhodování o způsobu vytváření použít](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o?  
  
-   [Cesta hledání, který se používá v systému Windows k nalezení knihovny DLL](../build/search-path-used-by-windows-to-locate-a-dll.md)  
  
-   [FreeLibrary a AfxFreeLibrary](../build/freelibrary-and-afxfreelibrary.md)  
  
-   [GetProcAddress](../build/getprocaddress.md)  
  
## <a name="see-also"></a>Viz také  
 [Knihovny DLL v jazyce Visual C++](../build/dlls-in-visual-cpp.md)   
 [LoadLibrary](http://go.microsoft.com/fwlink/p/?LinkID=259187)   
 [AfxLoadLibrary](../mfc/reference/application-information-and-management.md#afxloadlibrary)