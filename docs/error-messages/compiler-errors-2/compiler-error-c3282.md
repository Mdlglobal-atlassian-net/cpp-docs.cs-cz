---
title: Chyba kompilátoru C3282
ms.date: 11/04/2016
f1_keywords:
- C3282
helpviewer_keywords:
- C3282
ms.assetid: bac2ac89-c360-4c24-bb81-c20c62ece9ba
ms.openlocfilehash: 7092ddc3bf6859212cbb143572de1ef3604a13d3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50491504"
---
# <a name="compiler-error-c3282"></a>Chyba kompilátoru C3282

obecný parametr seznamy se může vyskytovat jenom u spravované nebo WinRTclasses, struktury nebo funkcí

Seznam obecných parametrů nebyl použit správně.  Další informace najdete v tématu [obecných typů](../../windows/generics-cpp-component-extensions.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3282 a ukazuje, jak ho opravit.

```
// C3282.cpp
// compile with: /clr /c
generic <typename T> int x;   // C3282

ref struct GC0 {
   generic <typename T> int x;   // C3282
};

// OK
generic <typename T>
ref class M {};
```