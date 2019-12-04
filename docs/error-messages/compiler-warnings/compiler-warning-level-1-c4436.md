---
title: Upozornění kompilátoru (úroveň 1) C4436
ms.date: 11/04/2016
f1_keywords:
- C4436
helpviewer_keywords:
- C4436
ms.assetid: 2b54a1fc-c9c6-4cc9-90be-faa44fc715d5
ms.openlocfilehash: 762a458072a0a1104cd1af55ef1f61772485b6c9
ms.sourcegitcommit: 8762a3f9b5476b4dee03f0ee8064ea606550986e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74810607"
---
# <a name="compiler-warning-level-1-c4436"></a>Upozornění kompilátoru (úroveň 1) C4436

dynamic_cast z virtuální základní třídy Class1 do Class2 v konstruktoru nebo destruktoru by mohlo selhat s částečně vytvořeným objektem Zkompilováným pomocí/VD2 nebo definovat Class2 s #pragma vtordisp (2).

Kompilátor zjistil operaci `dynamic_cast` s následujícími charakteristikami.

- Přetypování je z ukazatele základní třídy na odvozený ukazatel třídy.

- Odvozená třída prakticky dědí základní třídu.

- Odvozená třída nemá pole `vtordisp` pro virtuální základnu.

- Přetypování je nalezeno v konstruktoru nebo destruktoru odvozené třídy nebo v některé třídě, která dále dědí z odvozené třídy.

Upozornění indikuje, že `dynamic_cast` nemusí správně fungovat, pokud je provozován na částečně vytvořeném objektu.  K tomu dochází, pokud odvozený konstruktor/destruktor pracuje na podobjektu nějakého dalšího odvozeného objektu.  Pokud není odvozená třída s názvem v upozornění nikdy dále odvozena, upozornění může být ignorováno.

## <a name="example"></a>Příklad

Následující ukázka generuje C4436 a ukazuje problém při generování kódu, který vzniká v poli chybějící `vtordisp`.

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

## <a name="see-also"></a>Viz také:

[dynamic_cast – operátor](../../cpp/dynamic-cast-operator.md)<br/>
[vtordisp](../../preprocessor/vtordisp.md)<br/>
[Upozornění kompilátoru (úroveň 4) C4437](../../error-messages/compiler-warnings/compiler-warning-level-4-c4437.md)