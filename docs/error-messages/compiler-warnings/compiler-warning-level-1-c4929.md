---
title: Upozornění kompilátoru (úroveň 1) C4929
ms.date: 11/04/2016
f1_keywords:
- C4929
helpviewer_keywords:
- C4929
ms.assetid: 95f8ab4f-4468-4caa-acd5-8f4592f03b3c
ms.openlocfilehash: f8ed1252d61748047077defb4e7e77c85e596107
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052275"
---
# <a name="compiler-warning-level-1-c4929"></a>Upozornění kompilátoru (úroveň 1) C4929

' file ': knihovny typů obsahuje sjednocení; ignoruje se kvalifikátor embedded_idl.

Atribut embedded_idl [#import](../../preprocessor/hash-import-directive-cpp.md) nelze použít na knihovnu typů, protože sjednocení je přítomno v knihovně typů. Chcete-li toto upozornění vyřešit, nepoužívejte embedded_idl.

## <a name="example"></a>Příklad

Následující příklad definuje komponentu.

```cpp
// C4929a.cpp
// compile with: /LD /link /TLBOUT:C4929a.tlb
#include <objbase.h>
[module(name="Test")];
[public, switch_type(short)] typedef union _TD_UNION_TYPE   {
   [case(24)]
      float fM;
   [case(25)]
      double dMN;
   [default]
      int x;
} TD_UNION_TYPE;

[export, public] typedef struct _TDW_TYPE {
   [switch_is(sU)] TD_UNION_TYPE w;
      short sU;
} TD_TYPE;

[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface I {
   HRESULT f(TD_TYPE*);
};

[coclass, uuid("00000000-0000-0000-0000-000000000002")]
struct C : I {
   HRESULT f(TD_TYPE*) { return 0; }
};
```

## <a name="example"></a>Příklad

Následující ukázka generuje C4929.

```cpp
// C4929b.cpp
// compile with: /c /W1
#import "C4929a.tlb" embedded_idl   // C4929
```