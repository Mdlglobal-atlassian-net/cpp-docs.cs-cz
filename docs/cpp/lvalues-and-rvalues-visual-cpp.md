---
title: 'Kategorie hodnot: hodnoty lvalue a rvalue (C++)'
ms.date: 05/07/2019
helpviewer_keywords:
- R-values [C++]
- L-values [C++]
ms.assetid: a8843344-cccc-40be-b701-b71f7b5cdcaf
ms.openlocfilehash: 23625ddf44d16a4dc408b87f27b9cdfba7a9cbd4
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077240"
---
# <a name="lvalues-and-rvalues-c"></a>Hodnoty Lvalue a Rvalue (C++)

Každý C++ výraz má typ a patří do *kategorie hodnoty*. Kategorie hodnot jsou základem pro pravidla, která kompilátory musí dodržovat při vytváření, kopírování a přesouvání dočasných objektů během vyhodnocení výrazu.

Standard C++ 17 definuje kategorie hodnot výrazu následujícím způsobem:

- *Glvalue* je výraz, jehož vyhodnocení Určuje identitu objektu, bitového pole nebo funkce.
- *Prvalue* je výraz, jehož vyhodnocení inicializuje objekt nebo bitové pole nebo vypočítá hodnotu operandu operátoru, jak je uvedeno v kontextu, ve kterém se vyskytuje.
- *Hodnotu XValue* je glvalue, který označuje objekt nebo bitové pole, jejichž prostředky lze znovu použít (obvykle proto, že je poblíž konce své životnosti). Příklad: některé druhy výrazů zahrnující odkazy rvalue (8.3.2) poskytují XValues, jako je například volání funkce, jejíž návratový typ je odkaz rvalue nebo přetypování na odkazový typ rvalue.
- *L* -hodnota je glvalue, který není hodnotu XValue.
- *Rvalue* je prvalue nebo hodnotu XValue.

Následující diagram znázorňuje vztahy mezi těmito kategoriemi:

![C++kategorie hodnot výrazů](media/value_categories.png "C++kategorie hodnot výrazů")

L-hodnota má adresu, ke které má váš program přístup. Příklady výrazů lvalue zahrnují názvy proměnných, včetně **konstantních** proměnných, prvků pole, volání funkce, která vrací odkaz lvalue, bitová pole, sjednocení a členy třídy.

Výraz prvalue nemá žádnou adresu, ke které má váš program přístup. Příklady výrazů prvalue zahrnují literály, volání funkcí, která vracejí neodkazový typ, a dočasné objekty, které jsou vytvořeny během výrazu Evalution, ale přístupné pouze kompilátorem.

Výraz hodnotu XValue má adresu, která již není k dispozici pro váš program, ale lze ji použít k inicializaci odkazu rvalue, který poskytuje přístup k výrazu. Mezi příklady patří volání funkcí, která vracejí odkaz rvalue, a dolní index pole, člen a ukazatel na členské výrazy, kde je pole nebo objekt odkaz rvalue.

## <a name="example"></a>Příklad

Následující příklad ukazuje několik správných a nesprávných použití l-hodnot a r-hodnot:

```cpp
// lvalues_and_rvalues2.cpp
int main()
{
    int i, j, *p;

    // Correct usage: the variable i is an lvalue and the literal 7 is a prvalue.
    i = 7;

    // Incorrect usage: The left operand must be an lvalue (C2106).`j * 4` is a prvalue.
    7 = i; // C2106
    j * 4 = 7; // C2106

    // Correct usage: the dereferenced pointer is an lvalue.
    *p = i;

    // Correct usage: the conditional operator returns an lvalue.
    ((i < 3) ? i : j) = 7;

    // Incorrect usage: the constant ci is a non-modifiable lvalue (C3892).
    const int ci = 7;
    ci = 9; // C3892
}
```

> [!NOTE]
> Příklady v tomto tématu ukazují správné a nesprávné použití v případě, že operátory nejsou přetíženy. Přetěžováním operátorů lze vytvořit výraz jako l-hodnotu `j * 4`.

Výrazy *lvalue* a *rvalue* se často používají při odkazování na odkazy na objekty. Další informace o odkazech naleznete v tématu [lvalue reference deklarátor: &](../cpp/lvalue-reference-declarator-amp.md) and [rvalue reference deklarátor: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="see-also"></a>Viz také

[Základní koncepty](../cpp/basic-concepts-cpp.md)<br/>
[Deklarátor odkazu l-hodnoty: &](../cpp/lvalue-reference-declarator-amp.md)<br/>
[Deklarátor odkazu r-hodnoty: &&](../cpp/rvalue-reference-declarator-amp-amp.md)
