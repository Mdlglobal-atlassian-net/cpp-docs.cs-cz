---
title: Chyba kompilátoru C2062
ms.date: 11/04/2016
f1_keywords:
- C2062
helpviewer_keywords:
- C2062
ms.assetid: 6cc98353-2ddf-43ab-88a2-9cc91cdd6033
ms.openlocfilehash: dcfac9629a90b82744f87ec105c30301b2102cdf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50601471"
---
# <a name="compiler-error-c2062"></a>Chyba kompilátoru C2062

Typ 'type' neočekávané

Kompilátor nebyl očekáván název typu.

Následující ukázka generuje C2062:

```
// C2062.cpp
// compile with: /c
struct A {  : int l; };   // C2062
struct B { private: int l; };   // OK
```

C2062 může vzniknout také kvůli způsobu, jakým kompilátor zpracovává nedefinovaný typy v seznamu parametrů konstruktoru. Pokud kompilátor narazí Nedefinovaný typ (chybně?), předpokládá konstruktoru je výraz a vydá C2062. Pokud chcete vyřešit, použijte pouze definované typy v seznamu parametrů konstruktoru.