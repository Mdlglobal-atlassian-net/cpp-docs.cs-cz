---
title: Upozornění kompilátoru C4867
ms.date: 11/04/2016
f1_keywords:
- C4867
helpviewer_keywords:
- C4867
ms.assetid: 8a257d70-c3a7-462d-b285-e57c952a8bf7
ms.openlocfilehash: a2298f5369ff941a9d5ac38838f531d6db478739
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165090"
---
# <a name="compiler-warning-c4867"></a>Upozornění kompilátoru C4867

' function ': ve volání funkce chybí seznam argumentů; Chcete-li vytvořit ukazatel na člena, použijte volání ' call '

Ukazatel na členskou funkci byl nesprávně inicializován.

Toto upozornění je možné vygenerovat v důsledku práce s shodami s kompilátorem, která byla provedena pro sadu Visual Studio 2005: Rozšířená shoda ukazatelů na člena.  Kód, který se zkompiluje před Visual Studio 2005, teď vygeneruje C4867.

Toto upozornění je vždy vyvoláno jako chyba. Toto upozornění můžete zakázat pomocí direktivy pragma [Upozornění](../../preprocessor/warning.md) . Další informace o C4867 a MFC/ATL naleznete v tématu [_ATL_ENABLE_PTM_WARNING](../../atl/reference/compiler-options-macros.md#_atl_enable_ptm_warning).

## <a name="example"></a>Příklad

Následující ukázka generuje C4867.

```cpp
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
