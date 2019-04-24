---
title: Upozornění kompilátoru C4867
ms.date: 11/04/2016
f1_keywords:
- C4867
helpviewer_keywords:
- C4867
ms.assetid: 8a257d70-c3a7-462d-b285-e57c952a8bf7
ms.openlocfilehash: 9fa9b382b42a2fb8ba72fd9744c612af5dd598d2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62311069"
---
# <a name="compiler-warning-c4867"></a>Upozornění kompilátoru C4867

'function': volání funkce chybí seznam argumentů.; Použijte 'volání' vytvořte ukazatel na člena

Ukazatel na členskou funkci byl inicializován nesprávně.

Toto upozornění mohou být generovány jako důsledek kompilátoru prací, které bylo provedeno pro Visual C++ 2005: Rozšířená přizpůsobení pointer-to-member.  Kód, který zkompiluje před Visual C++ 2005 se teď generovat C4867.

Toto upozornění je vždy vyvoláno jako chyba. Použití [upozornění](../../preprocessor/warning.md) direktivy pragma zakážete toto upozornění. Další informace o C4867 a knihovny MFC nebo ATL naleznete v tématu [_ATL_ENABLE_PTM_WARNING](../../atl/reference/compiler-options-macros.md#_atl_enable_ptm_warning).

## <a name="example"></a>Příklad

Následující ukázka generuje C4867.

```
// C4867.cpp
// compile with: /c
class A {
public:
   void f(int) {}

   typedef void (A::*TAmtd)(int);

   struct B {
      TAmtd p;
   };

   void g() {
      B b = {f};   // C4867
      B b2 = {&A::f};   // OK
   }
};
```