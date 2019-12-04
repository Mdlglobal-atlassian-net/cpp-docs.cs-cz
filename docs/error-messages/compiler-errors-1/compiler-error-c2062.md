---
title: Chyba kompilátoru C2062
ms.date: 11/04/2016
f1_keywords:
- C2062
helpviewer_keywords:
- C2062
ms.assetid: 6cc98353-2ddf-43ab-88a2-9cc91cdd6033
ms.openlocfilehash: a709a540b24756a7e08f98552c5888a55c3ea601
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74735967"
---
# <a name="compiler-error-c2062"></a>Chyba kompilátoru C2062

typ typu je neočekávaný.

Kompilátor neočekával název typu.

Následující ukázka generuje C2062:

```cpp
// C2062.cpp
// compile with: /c
struct A {  : int l; };   // C2062
struct B { private: int l; };   // OK
```

K C2062 může také dojít v důsledku toho, jak kompilátor zpracovává nedefinované typy v seznamu parametrů konstruktoru. Pokud kompilátor narazí na nedefinovaný (nesprávně napsaný) typ?), předpokládá se, že konstruktor je výraz a vydává problémy C2062. Chcete-li tento problém vyřešit, použijte pouze definované typy v seznamu parametrů konstruktoru.
