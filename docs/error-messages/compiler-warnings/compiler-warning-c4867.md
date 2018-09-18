---
title: Upozornění kompilátoru C4867 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4867
dev_langs:
- C++
helpviewer_keywords:
- C4867
ms.assetid: 8a257d70-c3a7-462d-b285-e57c952a8bf7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b444156ae87e43b068521a3ad6687abe71df293f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074315"
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