---
title: Chyba kompilátoru C2870
ms.date: 11/04/2016
f1_keywords:
- C2870
helpviewer_keywords:
- C2870
ms.assetid: 80523ee9-1fd3-4dc4-8a77-5083deb99066
ms.openlocfilehash: 3b006592723df1222d05e39b3bc9e5729efc8aa6
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755028"
---
# <a name="compiler-error-c2870"></a>Chyba kompilátoru C2870

' name ': definice oboru názvů musí být buď v oboru souborů, nebo přímo v jiné definici oboru názvů.

Obor názvů jste definovali `name` nesprávně. Obory názvů musí být definované v oboru souborů (mimo všechny bloky a třídy) nebo hned v jiném oboru názvů.

Následující ukázka generuje C2870:

```cpp
// C2870.cpp
// compile with: /c
int main() {
   namespace A { int i; };   // C2870
}
```
