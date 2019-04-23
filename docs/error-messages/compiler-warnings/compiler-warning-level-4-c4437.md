---
title: Kompilátor upozornění (úroveň 4) C4437
ms.date: 11/04/2016
ms.assetid: dc07e350-20eb-474c-a7ad-f841ae7ec339
ms.openlocfilehash: 9ff52ae6d10f7d4ba429bbf3457a2a6b969998d4
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59037815"
---
# <a name="compiler-warning-level-4-c4437"></a>Kompilátor upozornění (úroveň 4) C4437

přetypování dynamic_cast z virtuální base 'class1' na 'class2' může v některých kontextech kompilace s možností/vd2 selže nebo je 'class2' s #pragma vtordisp(2) platit

Toto upozornění je vypnuto ve výchozím nastavení. Zobrazit [kompilátoru upozornění, že je vypnuto ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Další informace.

Kompilátor narazil `dynamic_cast` operace s následujícími vlastnostmi.

- Přetypování je z ukazatele na základní třídu na ukazatel na odvozenou třídu.

- Odvozená třída virtuálně dědí základní třídy.

- Odvozená třída nemá `vtordisp` pole pro virtuální základní třídy.

- Přetypování nebyl nalezen v konstruktor nebo destruktor odvozené třídy nebo některé třídy, která dále dědí z odvozené třídy (jinak upozornění kompilátoru, které budou vydány C4436).

Toto upozornění znamená, že `dynamic_cast` nemusí provést správně, pokud je zpracovávána v částečně vytvořeným objektem.  Tato situace nastane, pokud nadřazené funkce je volána z konstruktoru nebo destruktoru třídy, která dědí odvozené třídy, která je uvedená v upozornění.  Pokud odvozené třídy, která je uvedená v upozornění se nikdy další odvozena, nebo nadřazené funkce není volána během vytváření objektu nebo zničení, upozornění můžete ignorovat.

## <a name="example"></a>Příklad

Následující ukázka generuje C4437 a ukazuje problém s generováním kódu, který vyplývá z chybějící `vtordisp` pole.

```cpp
// C4437.cpp
// To see the warning and runtime assert, compile with: /W4
// To eliminate the warning and assert, compile with: /W4 /vd2
//       or compile with: /W4 /DFIX
#pragma warning(default : 4437)
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
        func();
    }

    void func()
    {
        A* a = static_cast<A*>(this);
        B* b = dynamic_cast<B*>(a);     // C4437
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
[Upozornění kompilátoru (úroveň 1) C4436](../../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md)