---
title: Upozornění kompilátoru (úroveň 4) C4434
ms.date: 11/04/2016
f1_keywords:
- C4434
helpviewer_keywords:
- C4434
ms.assetid: 24b8785e-353a-4c37-8bed-ed61001a871d
ms.openlocfilehash: fccc37ec531768adbe332ddf9fd91ceb708c7185
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990810"
---
# <a name="compiler-warning-level-4-c4434"></a>Upozornění kompilátoru (úroveň 4) C4434

konstruktor třídy musí mít privátní přístupnost; Změna na privátní přístup

C4434 označuje, že kompilátor změnil přístupnost statického konstruktoru. Statické konstruktory musí mít privátní přístupnost, protože jsou určeny pouze pro volání modulu CLR (Common Language Runtime). Další informace naleznete v tématu [statické konstruktory](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Static_constructors).

## <a name="example"></a>Příklad

Následující ukázka generuje C4434.

```cpp
// C4434.cpp
// compile with: /W4 /c /clr
public ref struct R {
   static R(){}   // C4434
};
```
