---
title: __unaligned | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: __unaligned_cpp
dev_langs: C++
helpviewer_keywords: __unaligned keyword [C++]
ms.assetid: 0cd83aad-1840-47e3-ad33-59bfcbe6375b
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: da662cf9cbe17539381766d37255e63d958fb7b1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="unaligned"></a>__unaligned
Při deklaraci ukazatele s modifikátorem `__unaligned` kompilátor předpokládá, že ukazatel odkazuje na data, která nejsou zarovnána. V důsledku toho pro aplikaci, která cílí na počítač rodiny procesorů Itanium (IPF), kompilátor generuje kód, který čte nezarovnaná data po jednom bajtu.  
  
## <a name="remarks"></a>Poznámky  
 `__unaligned` Modifikátor je platný pro [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] a [!INCLUDE[vcpritanium](../cpp/includes/vcpritanium_md.md)] kompilátory ale ovlivňuje pouze aplikace, které cílí na počítači IPF. Tento modifikátor popisuje pouze zarovnání odkazovaných dat. Ukazatel sám je považován za zarovnaný.  
  
 [!INCLUDE[vcpritanium](../cpp/includes/vcpritanium_md.md)] Procesoru generuje chybu zarovnání, pokud přistupuje k chybně zarovnaných data a času na zpracování selhání oslabí výkonu. Modifikátorem `__unaligned` lze zajistit, že procesor bude číst data po jednom bajtu a k dané chybě nedojde. Není nutné pro tuto modifikační [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] aplikace protože [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] procesor zpracovává chybně zarovnaných data bez chybující.  
  
 Další informace o zarovnání naleznete v následujících tématech:  
  
-   [Zarovnat](../cpp/align-cpp.md)  
  
-   [__alignof – operátor](../cpp/alignof-operator.md)  
  
-   [pack](../preprocessor/pack.md)  
  
-   [/Zp (zarovnání členů struktury)](../build/reference/zp-struct-member-alignment.md)  
  
-   [Příklady zarovnání struktur](../build/examples-of-structure-alignment.md)  
  
## <a name="example"></a>Příklad  
  
```  
// unaligned_keyword.cpp  
// compile with: /c  
// processor: x64 IPF  
#include <stdio.h>  
int main() {  
   char buf[100];  
  
   int __unaligned *p1 = (int*)(&buf[37]);  
   int *p2 = (int *)p1;  
  
   *p1 = 0;   // ok  
  
   __try {  
      *p2 = 0;  // throws an exception  
   }  
   __except(1) {  
      puts("exception");  
   }  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Klíčová slova](../cpp/keywords-cpp.md)