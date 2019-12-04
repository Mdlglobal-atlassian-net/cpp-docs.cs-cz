---
title: Upozornění kompilátoru (úroveň 4) C4437
ms.date: 11/04/2016
f1_keywords:
- C4437
helpviewer_keywords:
- C4437
ms.assetid: dc07e350-20eb-474c-a7ad-f841ae7ec339
ms.openlocfilehash: 6cd50d5c4d79b82c135ab4e84ec390dee9e906ef
ms.sourcegitcommit: 8762a3f9b5476b4dee03f0ee8064ea606550986e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74810651"
---
# <a name="compiler-warning-level-4-c4437"></a>Upozornění kompilátoru (úroveň 4) C4437

dynamic_cast z virtuální základní třídy ' Class1 ' na ' Class2 ' může selhat v některých kontextech Zkompilováných pomocí/VD2 nebo definovat ' Class2 ' s #pragma vtordisp (2) v platnosti.

Toto upozornění je ve výchozím nastavení vypnuté. Další informace najdete v tématu [Upozornění kompilátoru, která jsou ve výchozím nastavení vypnutá](../../preprocessor/compiler-warnings-that-are-off-by-default.md) .

Kompilátor zjistil operaci `dynamic_cast` s následujícími charakteristikami.

- Přetypování je z ukazatele základní třídy na odvozený ukazatel třídy.

- Odvozená třída prakticky dědí základní třídu.

- Odvozená třída nemá pole `vtordisp` pro virtuální základnu.

- Přetypování nebylo nalezeno v konstruktoru nebo destruktoru odvozené třídy nebo některá třída, která dále dědí z odvozené třídy (jinak se vydá upozornění kompilátoru C4436).

Upozornění indikuje, že `dynamic_cast` nemusí fungovat správně, pokud pracuje na částečně vytvořeném objektu.  K této situaci dochází, když je uzavírací funkce volána z konstruktoru nebo destruktoru třídy, která dědí odvozenou třídu pojmenovanou v upozornění.  Pokud odvozená třída, která je pojmenována v upozornění, již není dále odvozena, nebo není během konstrukce nebo zničení objektu volána uzavírací funkce, může být upozornění ignorováno.

## <a name="example"></a>Příklad

Následující ukázka generuje C4437 a ukazuje problém při generování kódu, který vzniká v poli chybějící `vtordisp`.

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