---
title: Chyba kompilátoru C3068
ms.date: 11/04/2016
f1_keywords:
- C3068
helpviewer_keywords:
- C3068
ms.assetid: 613e3447-b4a8-4268-a661-297bed63ccdf
ms.openlocfilehash: 9e20333a4fc18219f7f2514f3aefe73b81f284a6
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759487"
---
# <a name="compiler-error-c3068"></a>Chyba kompilátoru C3068

' function ': funkce ' holé ' nemůže obsahovat objekty, které by vyžadovaly odvinutí, pokud C++ došlo k výjimce

Kompilátor nemohl provést unwind zásobníku u [holé](../../cpp/naked-cpp.md) funkce, která vygenerovala výjimku, protože byl vytvořen dočasný objekt v rámci funkce a C++ zpracování výjimek ([/EHsc](../../build/reference/eh-exception-handling-model.md)).

Chcete-li tuto chybu vyřešit, proveďte alespoň jednu z následujících akcí:

- Nekompilovat pomocí/EHsc.

- Neoznačujte funkci jako `naked`.

- Nevytvářejte dočasný objekt ve funkci.

Pokud funkce vytvoří v zásobníku dočasný objekt, pokud funkce vyvolá výjimku a je-li C++ povoleno zpracování výjimek, kompilátor vyčistí zásobník, pokud je vyvolána výjimka.

Při vyvolání výjimky se pro funkci spustí kód generovaný kompilátorem, který se nazývá prolog a epilog a který není přítomen v holé funkci.

## <a name="example"></a>Příklad

Následující ukázka generuje C3068:

```cpp
// C3068.cpp
// compile with: /EHsc
// processor: x86
class A {
public:
   A(){}
   ~A(){}
};

void b(A){}

__declspec(naked) void c() {
   b(A());   // C3068
};
```
