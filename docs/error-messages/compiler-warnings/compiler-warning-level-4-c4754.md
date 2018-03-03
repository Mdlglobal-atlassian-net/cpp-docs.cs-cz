---
title: "Kompilátoru (úroveň 4) upozornění C4754 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4754
dev_langs:
- C++
helpviewer_keywords:
- C4754
ms.assetid: e0e4606a-754a-4f42-a274-21a34978d21d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ae6bad6452e1d119659c8588531c82671d031863
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4754"></a>C4754 kompilátoru upozornění (úroveň 4)
Převod pravidel pro aritmetické operace v porovnání to znamenat, že tento jeden větve nelze provést.  
  
 C4754 upozornění, protože výsledkem porovnání je vždy stejný. To znamená, že jeden z větve podmínky nikdy proveden, s největší pravděpodobností protože přidružené celočíselný výraz je nesprávný. Tento kód vadou nejčastěji dochází v kontroly přetečení nesprávný celých čísel na 64bitové architektury.  
  
 Pravidla převodu celé číslo jsou komplexní a existuje mnoho jemně nástrahy. Jako alternativu k opravě každý C4754 upozornění, můžete aktualizovat kód, který použije [SafeInt – knihovna](../../windows/safeint-library.md).  
  
## <a name="example"></a>Příklad  
 Tato ukázka generuje C4754:  
  
```cpp  
// C4754a.cpp  
// Compile with: /W4 /c  
#include "errno.h"  
  
int sum_overflow(unsigned long a, unsigned long b)   
{  
   unsigned long long x = a + b; // C4754  
  
   if (x > 0xFFFFFFFF)   
   {  
      // never executes!  
      return EOVERFLOW;  
   }  
   return 0;  
}  
```  
  
 Přidání `a + b` by mohlo způsobit aritmetického přetečení před výsledkem je přetypování nahoru na hodnotu 64-bit a přiřazenou proměnné 64-bit `x`. To znamená, že kontrola na `x` je redundantní a nikdy catch přetečení. V takovém případě kompilátor vydává toto upozornění:  
  
```Output  
Warning C4754: Conversion rules for arithmetic operations in the comparison at C4754a.cpp (7) mean that one branch cannot be executed. Cast '(a + ...)' to 'ULONG64' (or similar type of 8 bytes).  
```  
  
 Pokud chcete odstranit toto upozornění, můžete změnit přiřazení příkaz přetypovat operandy na 8 bajtů hodnoty:  
  
```cpp  
// Casting one operand is sufficient to force all the operands in   
// the addition be upcast according to C/C++ conversion rules, but  
// casting both is clearer.  
unsigned long long x =   
   (unsigned long long)a + (unsigned long long)b;  
```  
  
## <a name="example"></a>Příklad  
 Další vzorek vytvoří také C4754.  
  
```cpp  
// C4754b.cpp  
// Compile with: /W4 /c  
#include "errno.h"  
  
int wrap_overflow(unsigned long a)   
{  
   if (a + sizeof(unsigned long) < a) // C4754  
   {   
      // never executes!  
      return EOVERFLOW;  
   }  
   return 0;  
}  
```  
  
 `sizeof()` Vrátí operátor `size_t`, jejíž aktuální velikost je závislá na architekturu. Ukázkový kód funguje na 32bitové architektury kde `size_t` je typu 32-bit. Ale na 64bitové architektury `size_t` je typu 64-bit. Převod pravidel pro celá čísla znamenají, že `a` je přetypování nahoru na 64-bit hodnotu ve výrazu `a + b < a` jako kdyby byly napsány `(size_t)a + (size_t)b < (size_t)a`. Když `a` a `b` jsou 32bitová celá čísla, nikdy přetečení operace 64-bit sčítání a nikdy obsahuje omezení. V důsledku toho kód nikdy zjistí přetečení celé číslo na 64bitové architektury. Tento příklad způsobí, že kompilátor emitování toto upozornění:  
  
```Output  
Warning C4754: Conversion rules for arithmetic operations in the comparison at C4754b.cpp (7) mean that one branch cannot be executed. Cast '4' to 'ULONG' (or similar type of 4 bytes).  
```  
  
 Všimněte si, že upozornění explicitně uvádí konstantní hodnota 4 místo původní zdrojový řetězec – na době analysis upozornění zaznamená kód problematické `sizeof(unsigned long)` již byl převeden na konstantu. Proto možná budete muset sledovat dolů výrazu, který ve zdrojovém kódu souvisí s konstantní hodnotou v upozornění. Nejběžnější zdroje kód byl přeložen na konstanty v C4754 zprávy upozornění, jako jsou výrazy `sizeof(TYPE)` a `strlen(szConstantString)`.  
  
 V tomto případě kód pevné by vypadat takto:  
  
```cpp  
// Casting the result of sizeof() to unsigned long ensures  
// that all the addition operands are 32-bit, so any overflow   
// is detected by the check.  
if (a + (unsigned long)sizeof(unsigned long) < a)  
  
```  
  
 **Poznámka:** číslo řádku, které jsou uvedené v kompilátoru upozornění je poslední řádek příkazu. V upozornění o komplexní podmíněného příkaz, který je rozdělena na více řádků řádek, který má vadou kód může být Víceřádkový před řádek, který je hlášen. Příklad:  
  
```cpp  
unsigned long a;  
  
if (a + sizeof(unsigned long) < a || // incorrect check  
    condition1() ||   
    a == 0) {    // C4754 warning reported on this line  
         // never executes!  
         return INVALID_PARAMETER;  
}  
```