---
title: Chyba kompilátoru C3077
ms.date: 11/04/2016
f1_keywords:
- C3077
helpviewer_keywords:
- C3077
ms.assetid: d9f3c619-d1e2-4656-81a5-a35a9586a7d4
ms.openlocfilehash: d59859b82c1a8d506bb793a2c4dcd887b0898d85
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406688"
---
# <a name="compiler-error-c3077"></a>Chyba kompilátoru C3077

"finalizační metody": finalizační metoda může být jenom členem odkazového typu

Nelze deklarovat finalizační metodu v nativní nebo hodnotového typu.

Další informace najdete v tématu [destruktory a finalizační metody v tom, jak: Definice a používání tříd a struktur (C++vyhodnocovací)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).

## <a name="example"></a>Příklad

Následující ukázka generuje C3077.

```
// C3077.cpp
// compile with: /clr /c
value struct vs {
   !vs(){}   // C3077
};

ref struct rs {
protected:
   !rs(){}   // OK
};
```