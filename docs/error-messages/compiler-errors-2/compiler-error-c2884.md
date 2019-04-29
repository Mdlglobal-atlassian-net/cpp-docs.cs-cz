---
title: Chyba kompilátoru C2884
ms.date: 11/04/2016
f1_keywords:
- C2884
helpviewer_keywords:
- C2884
ms.assetid: 8b4d43e3-3fb5-4360-86c8-de59d8736d4f
ms.openlocfilehash: d920629dc0697d0f2fdd05ac5aca6118b89b88cb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62378853"
---
# <a name="compiler-error-c2884"></a>Chyba kompilátoru C2884

"name": zavedené pomocí deklarace je v konfliktu s lokální funkce 'function'

Pokusili jste se definovat funkci více než jednou. První definice je lokální definici. Druhým je z oboru názvů s `using` deklarace.

Následující ukázka generuje C2884:

```
// C2884.cpp
namespace A {
   void z(int);
}

void f() {
   void z(int);
   using A::z;   // C2884 z is already defined
}
```