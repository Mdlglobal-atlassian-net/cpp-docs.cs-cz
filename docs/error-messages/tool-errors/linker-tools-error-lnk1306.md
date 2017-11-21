---
title: "Chyba linkerů Lnk1306 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1306
dev_langs: C++
helpviewer_keywords: LNK1306
ms.assetid: fad1df6a-0bd9-412f-b0d1-7c9bc749c584
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d020d7ca037c737dfb03c32ff2d773730c118311
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-error-lnk1306"></a>Chyba linkerů LNK1306  
  
> Funkce knihoven DLL vstupního bodu nelze spravovat; nativní kompilace  
  
`DllMain`Nelze kompilovat, k MSIL; musí být zkompilovány v nativním režimu.  
  
Chcete-li vyřešit tento problém  
  
-   Zkompilovat soubor, který obsahuje vstupní bod bez **/CLR**.  
  
-   Vstupní bod chápat `#pragma unmanaged` části.  
  
Další informace naleznete v tématu:  
  
-   [/ CLR (kompilace common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [spravované, nespravované](../../preprocessor/managed-unmanaged.md)  
  
-   [Inicializace smíšených sestavení](../../dotnet/initialization-of-mixed-assemblies.md)  
  
-   [Knihovny DLL a chování běhové knihovny jazyka Visual C++](../../build/run-time-library-behavior.md)  
  
## <a name="example"></a>Příklad  
  
Následující ukázka generuje LNK1306.  
  
```cpp  
// LNK1306.cpp  
// compile with: /clr /link /dll /entry:NewDllMain  
// LNK1306 error expected  
#include <windows.h>  
int __stdcall NewDllMain( HINSTANCE h, ULONG ulReason, PVOID pvReserved ) {  
   return 1;  
}  
```  
  
Chcete-li tento problém vyřešit, nepoužívejte / CLR – možnost kompilaci tohoto souboru, nebo používat `#pragma` – direktiva uvést definici vstupní bod do nespravovaných části, jak je znázorněno v tomto příkladu:  
  
```cpp  
// LNK1306fix.cpp  
// compile with: /clr /link /dll /entry:NewDllMain  
#include <windows.h>  
#pragma managed(push, off)  
int __stdcall NewDllMain( HINSTANCE h, ULONG ulReason, PVOID pvReserved ) {  
   return 1;  
}  
#pragma managed(pop)  
```  
