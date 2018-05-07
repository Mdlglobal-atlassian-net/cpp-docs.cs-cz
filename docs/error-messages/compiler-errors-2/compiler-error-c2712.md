---
title: C2712 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2712
dev_langs:
- C++
helpviewer_keywords:
- C2712
ms.assetid: f7d4ffcc-7ed2-459b-8067-a728ce647071
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c26c5d7a24c022cacf4c20687b2d8c58f7e9e342
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2712"></a>C2712 chyby kompilátoru
nelze použít __try ve funkcích, které vyžadují unwinding objektu  
  
 Chyba C2712 může dojít, pokud používáte [/EHsc](../../build/reference/eh-exception-handling-model.md), a funkce s zpracování strukturovaných výjimka taky obsahuje objekty, které vyžadují unwinding (odstraňování).  
  
 Možná řešení:  
  
-   Přesunout kód, který vyžaduje jinou funkci SEH  
  
-   Přepisování funkcí, které pomocí SEH nepoužívejte místní proměnné a parametry, které mají destruktory. Nepoužívejte SEH v konstruktorech nebo destruktorů  
  
-   Kompilovat bez /EHsc  
  
 Chyba C2712 může také nastat, pokud při volání metody deklarovat pomocí [__event](../../cpp/event.md) – klíčové slovo. Vzhledem k tomu, že událost může použít v prostředí s více vlákny, kompilátor generuje kód, který brání manipulaci s podkladového objektu událostí a poté uzavře generovaný kód do SEH [try-finally – příkaz](../../cpp/try-finally-statement.md). V důsledku toho dojde chybě C2712, pokud volání metody událostí a předáte hodnotu argument jehož typ má destruktor. V takovém případě je předat argument jako konstantní odkaz jedno řešení.  
  
## <a name="example"></a>Příklad  
 C2712 může také dojít, když kompilujete s **/CLR: pure** a deklarovat statické pole ukazatele na funkce v `__try` bloku. Statický člen vyžaduje kompilátor používat dynamické inicializace pod **/CLR: pure**, což naznačuje zpracovávání výjimek v jazyce C++. Však není povolen zpracovávání výjimek v jazyce C++ v `__try` bloku.  
  
 **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015.  
  
 Následující ukázka generuje C2712 a ukazuje, jak ji odstranit.  
  
```  
// C2712.cpp  
// compile with: /clr:pure /c  
struct S1 {  
   static int smf();  
   void fnc();  
};  
  
void S1::fnc() {  
   __try {  
      static int (*array_1[])() = {smf,};   // C2712  
  
      // OK  
      static int (*array_2[2])();  
      array_2[0] = smf;  
    }  
    __except(0) {}  
}  
```