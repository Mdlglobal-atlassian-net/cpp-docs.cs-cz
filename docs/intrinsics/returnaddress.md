---
title: _ReturnAddress | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: _ReturnAddress
dev_langs: C++
helpviewer_keywords:
- _ReturnAddress intrinsic
- ReturnAddress intrinsic
ms.assetid: 7f4a5811-35e6-4f64-ba7c-21203380eeda
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d207fcba6846d0a5e599d6273f5b35bb554bda40
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="returnaddress"></a>_ReturnAddress
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 `_ReturnAddress` Vnitřní poskytuje adresa instrukce ve volání funkce, která bude proveden po řízení vrátí volajícímu.  
  
 Vytvořte následující program a krok přes něj v ladicím programu. Krocích program, poznamenejte si adresu, která je vrácena z `_ReturnAddress`. Potom okamžitě po návratu z funkce kde `_ReturnAddress` byla použít, otevřete [postupy: použití okna zpětného překladu](/visualstudio/debugger/how-to-use-the-disassembly-window) a Všimněte si, že adresa instrukce další spouštění odpovídá adrese vrácená z `_ReturnAddress`.  
  
 Optimalizace například vložené může mít vliv na zpáteční adresu. Například, pokud je uvedený ukázkový program kompilovat s [/Ob1](../build/reference/ob-inline-function-expansion.md), `inline_func` bude vložená do volání funkce `main`. Proto volání `_ReturnAddress` z `inline_func` a `main` vytvoří každý stejnou hodnotu.  
  
 Když `_ReturnAddress` se používá v programu kompilovat s [/CLR](../build/reference/clr-common-language-runtime-compilation.md), obsahující funkce `_ReturnAddress` volání se zkompiluje jako nativní funkce. Když funkce zkompilovat jako spravované volání funkce obsahující `_ReturnAddress`, `_ReturnAddress` nemusí chovat podle očekávání.  
  
## <a name="requirements"></a>Požadavky  
 **Soubor hlaviček** \<intrin.h >  
  
## <a name="example"></a>Příklad  
  
```  
// compiler_intrinsics__ReturnAddress.cpp  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(_ReturnAddress)  
  
__declspec(noinline)  
void noinline_func(void)  
{  
   printf("Return address from %s: %p\n", __FUNCTION__, _ReturnAddress());  
}  
  
__forceinline  
void inline_func(void)  
{  
   printf("Return address from %s: %p\n", __FUNCTION__, _ReturnAddress());  
}  
  
int main(void)  
{  
   noinline_func();   
   inline_func();  
   printf("Return address from %s: %p\n", __FUNCTION__, _ReturnAddress());  
  
   return 0;  
}  
```  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [_AddressOfReturnAddress](../intrinsics/addressofreturnaddress.md)   
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)