---
title: Chyba linkerů Lnk1306 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1306
dev_langs:
- C++
helpviewer_keywords:
- LNK1306
ms.assetid: fad1df6a-0bd9-412f-b0d1-7c9bc749c584
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bb340a4c28f94f18e0c4b65bea8749394e002bd3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33300495"
---
# <a name="linker-tools-error-lnk1306"></a>Chyba linkerů LNK1306  
  
> Funkce knihoven DLL vstupního bodu nelze spravovat; nativní kompilace  
  
`DllMain` Nelze kompilovat, k MSIL; musí být zkompilovány v nativním režimu.  
  
Chcete-li vyřešit tento problém  
  
-   Zkompilovat soubor, který obsahuje vstupní bod bez **/CLR**.  
  
-   Vstupní bod chápat `#pragma unmanaged` části.  
  
Další informace naleznete v tématu:  
  
-   [/clr (kompilace modulu Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [managed, unmanaged](../../preprocessor/managed-unmanaged.md)  
  
-   [Inicializace smíšených sestavení](../../dotnet/initialization-of-mixed-assemblies.md)  
  
-   [Knihovny DLL a chování běhové knihovny v jazyce Visual C++](../../build/run-time-library-behavior.md)  
  
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
