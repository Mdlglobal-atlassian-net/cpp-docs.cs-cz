---
title: Hledání cesta používaná systémem Windows k nalezení knihovny DLL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- searching [C++], DLLs
- DLLs [C++], Windows search path
- Windows [C++], DLL search path
- known DLL searches [C++]
- locating DLLs
- finding DLLs
- search paths [C++]
ms.assetid: 84bfb380-ad7b-4962-b2d0-51b19a45f1bb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 166b5fccf6dd231029f79fede837909a49e7fc4f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
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
 [Knihovny DLL v jazyce Visual C++](../build/dlls-in-visual-cpp.md)