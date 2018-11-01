---
title: Chyba kompilátoru C3068
ms.date: 11/04/2016
f1_keywords:
- C3068
helpviewer_keywords:
- C3068
ms.assetid: 613e3447-b4a8-4268-a661-297bed63ccdf
ms.openlocfilehash: 4790c9caafd28722f3631104cfe5cfc762cf6426
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575471"
---
# <a name="compiler-error-c3068"></a>Chyba kompilátoru C3068

'function': funkci naked' nemůže obsahovat objekty, které by vyžadovaly vrácení zpět, pokud došlo k výjimce C++

Nebylo možné provést, v odvíjení zásobníku kompilátoru [naked](../../cpp/naked-cpp.md) funkce, která byla vyvolána výjimka, protože byl vytvořen dočasný objekt funkce a zpracování výjimek jazyka C++ ([/EHsc](../../build/reference/eh-exception-handling-model.md)) byl zadán.

Chcete-li vyřešit tuto chybu, proveďte splnit aspoň jednu z následujících akcí:

- Nejde zkompilovat/EHsc.

- Neoznačujte funkce jako `naked`.

- Nevytvářejte dočasný objekt ve funkci.

Pokud funkce vytvoří dočasný objekt v zásobníku, pokud funkce vyvolá výjimku, a pokud je povoleno zpracování výjimek jazyka C++, kompilátor vyčistí zásobník Pokud dojde k výjimce.

Když je vyvolána výjimka, kompilátor vygeneruje kód, volá se, kódu prologu a epilogu, které nejsou součástí neviditelné funkce, je provedena pro funkci.

## <a name="example"></a>Příklad

Následující ukázka generuje C3068:

```
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