---
title: "Hledání cesta používaná systémem Windows k nalezení knihovny DLL | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- searching [C++], DLLs
- DLLs [C++], Windows search path
- Windows [C++], DLL search path
- known DLL searches [C++]
- locating DLLs
- finding DLLs
- search paths [C++]
ms.assetid: 84bfb380-ad7b-4962-b2d0-51b19a45f1bb
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 79f6ca137c16100ac1d6b9bfa818f35d5ae21f14
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="search-path-used-by-windows-to-locate-a-dll"></a>Vyhledávací cesta používaná systémem Windows k nalezení knihovny DLL
S implicitní a explicitní propojování, Windows nejdřív hledá "známých knihoven DLL", jako je například Kernel32.dll a User32.dll. Windows pak hledá knihovny DLL v tomto pořadí:  
  
1.  Adresář, kde se nachází spustitelného souboru modulu pro aktuální proces.  
  
2.  Aktuální adresář.  
  
3.  Adresář systému Windows. **GetSystemDirectory** funkce načte cestu tohoto adresáře.  
  
4.  Adresář systému Windows. **GetWindowsDirectory** funkce načte cestu tohoto adresáře.  
  
5.  Adresáře uvedené v proměnné prostředí PATH.  
  
    > [!NOTE]
    >  LIBPATH – proměnná prostředí se nepoužije.  
  
## <a name="what-do-you-want-to-do"></a>Co chcete udělat?  
  
-   [Postup propojení implicitně s knihovny DLL](../build/linking-an-executable-to-a-dll.md#linking-implicitly)  
  
-   [Postup propojení explicitně s knihovny DLL](../build/linking-an-executable-to-a-dll.md#linking-explicitly)  
  
-   [Rozhodování o způsobu vytváření použít](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)  
  
## <a name="see-also"></a>Viz také  
 [Knihovny DLL v jazyce Visual C++](../build/dlls-in-visual-cpp.md)