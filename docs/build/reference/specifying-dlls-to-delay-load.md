---
title: "Určení knihoven DLL pro odložené načtení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- DELAYLOAD linker option
- delayed loading of DLLs
- delayed loading of DLLs, specifying
- /DELAYLOAD linker option
ms.assetid: 94cbecfe-7a42-40d1-a618-9f2786bac0d8
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: bfa7eb3c862c1ce5d1ed356ddd89c51ebff95860
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="specifying-dlls-to-delay-load"></a>Určení knihoven DLL pro odložené načtení
Můžete určit, které knihoven DLL pro odložené načítání vlivem [/delayload](../../build/reference/delayload-delay-load-import.md):`dllname` – možnost linkeru. Pokud neplánujete použít vlastní verzi pomocné funkce, je nutné také propojit váš program s delayimp.lib (pro desktopové aplikace) nebo dloadhelper.lib (pro aplikace pro store).  
  
 Toto je jednoduchý příklad odloženého načítání knihovny DLL:  
  
```  
// cl t.cpp user32.lib delayimp.lib  /link /DELAYLOAD:user32.dll  
#include <windows.h>  
// uncomment these lines to remove .libs from command line  
// #pragma comment(lib, "delayimp")  
// #pragma comment(lib, "user32")  
  
int main() {  
   // user32.dll will load at this point  
   MessageBox(NULL, "Hello", "Hello", MB_OK);  
}  
```  
  
 Sestavení ladicí verze projektu. Krok prostřednictvím kódu pomocí ladicího programu a můžete si všimněte, že user32.dll je načíst jenom v případě, že provedete volání `MessageBox`.  
  
## <a name="see-also"></a>Viz také  
 [Podpora linkeru pro knihovny DLL s odloženým načtením](../../build/reference/linker-support-for-delay-loaded-dlls.md)