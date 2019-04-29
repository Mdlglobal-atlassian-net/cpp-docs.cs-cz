---
title: Kompilátor upozornění (úroveň 4) C4434
ms.date: 11/04/2016
f1_keywords:
- C4434
helpviewer_keywords:
- C4434
ms.assetid: 24b8785e-353a-4c37-8bed-ed61001a871d
ms.openlocfilehash: 6a7d760a7d192c7e0a7bd5e16f77efe1a4099c31
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391488"
---
# <a name="compiler-warning-level-4-c4434"></a>Kompilátor upozornění (úroveň 4) C4434

konstruktor třídy musí mít přístupnost private; Změna na soukromý přístup

C4434 udává, že kompilátor změnil usnadnění statický konstruktor. Statické konstruktory musí mít přístupnost private, jako jsou určená jenom pro být volán modul common language runtime. Další informace najdete v tématu [statické konstruktory](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Static_constructors).

## <a name="example"></a>Příklad

Následující ukázka generuje C4434.

```
// C4434.cpp
// compile with: /W4 /c /clr
public ref struct R {
   static R(){}   // C4434
};
```