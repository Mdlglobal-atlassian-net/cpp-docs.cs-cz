---
title: Chyba kompilátoru C2062 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2062
dev_langs:
- C++
helpviewer_keywords:
- C2062
ms.assetid: 6cc98353-2ddf-43ab-88a2-9cc91cdd6033
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bbda0894b25e09681207d6447bb40727d490fc02
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46072241"
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