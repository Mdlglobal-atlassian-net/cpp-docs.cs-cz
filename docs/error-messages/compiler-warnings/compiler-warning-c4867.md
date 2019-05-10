---
title: Upozornění kompilátoru C4867
ms.date: 11/04/2016
f1_keywords:
- C4867
helpviewer_keywords:
- C4867
ms.assetid: 8a257d70-c3a7-462d-b285-e57c952a8bf7
ms.openlocfilehash: 0fd5de46f713aed08508f8755c9e54c3ff46366b
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447202"
---
# <a name="compiler-warning-c4867"></a>Upozornění kompilátoru C4867

'function': volání funkce chybí seznam argumentů.; Použijte 'volání' vytvořte ukazatel na člena

Ukazatel na členskou funkci byl inicializován nesprávně.

Toto upozornění mohou být generovány jako důsledek kompilátoru prací, které bylo provedeno pro Visual Studio 2005: Rozšířená přizpůsobení pointer-to-member.  Kód, který zkompiluje před Visual Studio 2005 nyní vygeneruje C4867.

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