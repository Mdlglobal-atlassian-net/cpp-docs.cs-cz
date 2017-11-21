---
title: "Explicitní uvolnění knihovny DLL s odloženým načtením | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- /DELAY:UNLOAD linker option
- DELAY:UNLOAD linker option
- __FUnloadDelayLoadedDLL2
- delayed loading of DLLs, unloading
ms.assetid: 1c4c5172-fd06-45d3-9e4f-f12343176b3c
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b59ad181ea39382a4f79b1af5e6f1d1dbc1ded62
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="explicitly-unloading-a-delay-loaded-dll"></a>Explicitní uvolnění knihovny DLL načtené se zpožděním
[/Delay](../../build/reference/delay-delay-load-import-settings.md): unload – možnost linkeru umožňuje uvolnění knihovny DLL, která byla načtena zpoždění. Ve výchozím nastavení při kódu uvolnění knihovny DLL (pomocí/delay: Unload a **__FUnloadDelayLoadedDLL2**), importy s odloženým načtením zůstat v tabulky import adres (IAT). Ale pokud používáte/delay: Unload na příkazový řádek linkeru, pomocné funkce bude podporovat explicitní uvolnění knihovny DLL, obnovena IAT původní podobě; Neplatný ukazatele budou přepsány. Tabulku IAT je pole v [ImgDelayDescr](../../build/reference/calling-conventions-parameters-and-return-type.md) obsahující adresu kopii původní IAT (pokud existuje).  
  
## <a name="example"></a>Příklad  
  
### <a name="code"></a>Kód  
  
```  
// link with /link /DELAYLOAD:MyDLL.dll /DELAY:UNLOAD  
#include <windows.h>  
#include <delayimp.h>  
#include "MyDll.h"  
#include <stdio.h>  
  
#pragma comment(lib, "delayimp")  
#pragma comment(lib, "MyDll")  
int main()  
{  
    BOOL TestReturn;  
    // MyDLL.DLL will load at this point  
    fnMyDll();  
  
    //MyDLL.dll will unload at this point  
    TestReturn = __FUnloadDelayLoadedDLL2("MyDll.dll");  
  
    if (TestReturn)  
        printf_s("\nDLL was unloaded");  
    else  
        printf_s("\nDLL was not unloaded");  
}  
```  
  
### <a name="comments"></a>Komentáře  
 Důležité poznámky k uvolnění knihovny DLL odloženým načtením:  
  
-   Implementace můžete najít **__FUnloadDelayLoadedDLL2** funkce v souboru \VC7\INCLUDE\DELAYHLP. CPP.  
  
-   Název parametru **__FUnloadDelayLoadedDLL2** funkce musí přesně shodovat (včetně případě) co knihovny importu obsahuje (která řetězec je také v tabulky import do bitové kopie). Můžete zobrazit obsah knihovny importu s [DUMPBIN /DEPENDENTS](../../build/reference/dependents.md). Pokud se požaduje shodu velká a malá písmena řetězce, můžete je aktualizovat **__FUnloadDelayLoadedDLL2** použít jednu z řetězcové funkce CRT nebo volání rozhraní API systému Windows.  
  
 V tématu [uvolnění knihovny DLL Delay-Loaded](../../build/reference/unloading-a-delay-loaded-dll.md) Další informace.  
  
## <a name="see-also"></a>Viz také  
 [Podpora linkeru pro knihovny DLL s odloženým načtením](../../build/reference/linker-support-for-delay-loaded-dlls.md)