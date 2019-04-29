---
title: Compiler Error C3156
ms.date: 11/04/2016
f1_keywords:
- C3156
helpviewer_keywords:
- C3156
ms.assetid: 1876da78-b94e-4af7-9795-28f72b209b3e
ms.openlocfilehash: 115e8cd63562964b19e4a67f7a649ecfab2596c1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62375337"
---
# <a name="compiler-error-c3156"></a>Compiler Error C3156

'class': nelze mít lokální definici typu spravované nebo typ WinRT

Funkce nesmí obsahovat definice nebo deklarace, spravované nebo WinRT třídy, struktury nebo rozhraní.

## <a name="example"></a>Příklad

Následující ukázka generuje C3156.

```
// C3156.cpp
// compile with: /clr /c
void f() {
   ref class X {};   // C3156
   ref class Y;   // C3156
}
```
