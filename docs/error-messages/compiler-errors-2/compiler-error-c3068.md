---
title: Chyba kompilátoru C3068 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3068
dev_langs:
- C++
helpviewer_keywords:
- C3068
ms.assetid: 613e3447-b4a8-4268-a661-297bed63ccdf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fdea26e204032c27f00639ee46a928c7bf084a4e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035616"
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