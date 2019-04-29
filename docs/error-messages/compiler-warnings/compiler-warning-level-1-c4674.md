---
title: Kompilátor upozornění (úroveň 1) C4674
ms.date: 11/04/2016
f1_keywords:
- C4674
helpviewer_keywords:
- C4674
ms.assetid: 638dae0b-b82c-4865-9599-72630827ca09
ms.openlocfilehash: f7db2f37224a8defffb545b0cfaf018fd4654227
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62374544"
---
# <a name="compiler-warning-level-1-c4674"></a>Kompilátor upozornění (úroveň 1) C4674

"metoda" by se měl deklarovat 'static' a mít přesně jeden parametr.

Podpis operátora převodu nebyl zadán správně. Metoda není považováno za uživatelsky definovaný převod. Další informace o definování operátory, naleznete v tématu [uživatelem definované operátory (C++vyhodnocovací)](../../dotnet/user-defined-operators-cpp-cli.md) a [uživatelem definovaných převodů (C++vyhodnocovací)](../../dotnet/user-defined-conversions-cpp-cli.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C4674.

```
// C4674.cpp
// compile with: /clr /WX /W1 /LD
ref class G {
   int op_Implicit(int i) {   // C4674
      return 0;
   }
};
```
