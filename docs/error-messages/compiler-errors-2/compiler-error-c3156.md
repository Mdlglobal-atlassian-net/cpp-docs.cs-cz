---
title: Chyba kompilátoru C3156
ms.date: 11/04/2016
f1_keywords:
- C3156
helpviewer_keywords:
- C3156
ms.assetid: 1876da78-b94e-4af7-9795-28f72b209b3e
ms.openlocfilehash: 259c6fae621b8f5f00992e85fe71ace9b6c789f3
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761826"
---
# <a name="compiler-error-c3156"></a>Chyba kompilátoru C3156

' class ': nelze mít místní definici typu spravovaného nebo WinRT

Funkce nemůže obsahovat definici nebo deklaraci spravovaného nebo třídy WinRT, struktury nebo rozhraní.

## <a name="example"></a>Příklad

Následující ukázka generuje C3156.

```cpp
// C3156.cpp
// compile with: /clr /c
void f() {
   ref class X {};   // C3156
   ref class Y;   // C3156
}
```
