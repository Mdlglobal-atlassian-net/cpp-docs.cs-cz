---
title: "Kompilátoru (úroveň 1) upozornění C4747 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4747
dev_langs: C++
helpviewer_keywords: C4747
ms.assetid: af37befd-ba1f-4bdc-96e1-a953f7a2ad9c
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 23c0598c97bf0f2ab05169cb7bf72b9efd5a3f7c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4747"></a>C4747 kompilátoru upozornění (úroveň 1)
Volání metody spravované 'entrypoint': spravovaného kódu nemusí být možné spustit v zavaděči, včetně vstupní bod knihovny DLL a volání z vstupní bod knihovny DLL  
  
 Kompilátor najít zkompilovány do MSIL (pravděpodobných) knihovny DLL vstupní bod.  Z důvodu možných problémech při načítání knihovny DLL, jejichž vstupní bod se zkompiluje do MSIL jsou v kompilaci funkce DLL vstupního bodu do MSIL důrazně nedoporučuje.  
  
 Další informace najdete v tématu [inicializace smíšených sestavení](../../dotnet/initialization-of-mixed-assemblies.md) a [chyba Linkerů LNK1306](../../error-messages/tool-errors/linker-tools-error-lnk1306.md).  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Nejde kompilovat modul s **/CLR**.  
  
2.  Označit funkce vstupního bodu pomocí `#pragma unmanaged`.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4747.  
  
```  
// C4747.cpp  
// compile with: /clr /c /W1  
// C4747 expected  
#include <windows.h>  
  
// Uncomment the following line to resolve.  
// #pragma unmanaged  
  
BOOL WINAPI DllMain(HANDLE hInstance, ULONG Command, LPVOID Reserved) {  
   return TRUE;  
};  
```