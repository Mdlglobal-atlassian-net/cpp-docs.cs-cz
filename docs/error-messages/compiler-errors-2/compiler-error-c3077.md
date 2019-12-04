---
title: Chyba kompilátoru C3077
ms.date: 11/04/2016
f1_keywords:
- C3077
helpviewer_keywords:
- C3077
ms.assetid: d9f3c619-d1e2-4656-81a5-a35a9586a7d4
ms.openlocfilehash: b2dfe4c17ee122baa8f648669f9080b28584a66f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756731"
---
# <a name="compiler-error-c3077"></a>Chyba kompilátoru C3077

"finalizační metoda": finalizační metoda může být jedině členem typu odkazu.

Finalizační metodu nelze deklarovat v nativním nebo hodnotovém typu.

Další informace naleznete v tématu [destruktory a finalizační metody v tématu How to: Define and spotřebovávají Classes andC++Structs (/CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).

## <a name="example"></a>Příklad

Následující ukázka generuje C3077.

```cpp
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
