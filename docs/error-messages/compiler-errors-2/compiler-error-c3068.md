---
title: Chyba kompilátoru C3068
ms.date: 11/04/2016
f1_keywords:
- C3068
helpviewer_keywords:
- C3068
ms.assetid: 613e3447-b4a8-4268-a661-297bed63ccdf
ms.openlocfilehash: 4790c9caafd28722f3631104cfe5cfc762cf6426
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406883"
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