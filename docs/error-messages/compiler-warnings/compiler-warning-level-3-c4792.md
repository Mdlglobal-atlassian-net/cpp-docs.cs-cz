---
title: Kompilátoru (úroveň 3) upozornění C4792 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4792
dev_langs:
- C++
helpviewer_keywords:
- C4792
ms.assetid: c047ce69-a622-44e1-9425-d41aa9261c61
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a4b0867305c56fc551e55680b6ed48bdb701cc09
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292097"
---
# <a name="compiler-warning-level-3-c4792"></a>C4792 kompilátoru upozornění (úroveň 3)
Funkce 'function' deklarováno s použitím import systému a na něj odkazovat z nativního kódu; Importovat knihovny potřebné k propojení  
  
 Nativní funkce, které byly naimportovány do programu s DllImport byla volána nespravované funkce. Proto musíte propojit knihovny importu pro knihovnu DLL.  
  
 Toto upozornění nelze vyřešit v kódu nebo tak, že změníte způsob kompilace. Použití [upozornění](../../preprocessor/warning.md) – Direktiva pragma pro vypnutí tohoto upozornění.  
  
 Následující ukázka generuje C4792:  
  
```  
// C4792.cpp  
// compile with: /clr /W3  
// C4792 expected  
using namespace System::Runtime::InteropServices;  
[DllImport("msvcrt")]  
extern "C" int __cdecl puts(const char *);  
int main() {}  
  
// Uncomment the following line to resolve.  
// #pragma warning(disable : 4792)  
#pragma unmanaged  
void func(void){  
   puts("test");  
}  
```