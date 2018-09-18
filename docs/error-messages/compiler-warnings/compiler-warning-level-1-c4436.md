---
title: Upozornění (úroveň 1) C4436 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
ms.assetid: 2b54a1fc-c9c6-4cc9-90be-faa44fc715d5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2484b5420347f49a74d8eb3cdf65a8221741cc63
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46076499"
---
# <a name="compiler-warning-level-1-c4436"></a>Kompilátor upozornění (úroveň 1) C4436

přetypování dynamic_cast z virtuální base 'class1' na 'class2' v konstruktoru nebo destruktoru by mohly selhat s částečně vytvořeným objektem kompilace s možností/vd2 nebo definovat 'class2' s #pragma vtordisp(2) platit

Kompilátor narazil `dynamic_cast` operace s následujícími vlastnostmi.

- Přetypování je z ukazatele na základní třídu na ukazatel na odvozenou třídu.

- Odvozená třída virtuálně dědí základní třídy.

- Odvozená třída nemá `vtordisp` pole pro virtuální základní třídy.

- Přetypování se nachází v konstruktor nebo destruktor odvozené třídy nebo některé třídy, která dále dědí z odvozené třídy.

Toto upozornění označuje, `dynamic_cast` nemusí provést správně, pokud je zpracovávána v částečně vytvořených objektů.  K tomu dojde, pokud konstruktor nebo destruktor odvozené pracuje na dílčí objekt některé další odvozené objektu.  Pokud je odvozená třída s názvem v tomto upozornění nikdy další odvozena, lze ignorovat upozornění.

## <a name="example"></a>Příklad

Následující ukázka generuje C4436 a ukazuje problém s generováním kódu, který vyplývá z chybějící `vtordisp` pole.

```cpp
// C4436.cpp
// To see the warning and runtime assert, compile with: /W1
// To eliminate the warning and assert, compile with: /W1 /vd2
//       or compile with: /W1 /DFIX
#include <cassert>

struct A
{
public:
    virtual ~A() {}
};

#if defined(FIX)
#pragma vtordisp(push, 2)
#endif
struct B : virtual A
{
    B()
    {
        A* a = static_cast<A*>(this);
        B* b = dynamic_cast<B*>(a);     // C4436
        assert(this == b);              // assert unless compiled with /vd2
    }
};
#if defined(FIX)
#pragma vtordisp(pop)
#endif

struct C : B
{
    int i;
};

int main()
{
    C c;
}
```

## <a name="see-also"></a>Viz také

[dynamic_cast – operátor](../../cpp/dynamic-cast-operator.md)<br/>
[vtordisp](../../preprocessor/vtordisp.md)<br/>
[Upozornění kompilátoru (úroveň 4) C4437](../../error-messages/compiler-warnings/compiler-warning-level-4-c4437.md)