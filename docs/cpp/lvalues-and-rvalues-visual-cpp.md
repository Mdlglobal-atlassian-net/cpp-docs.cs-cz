---
title: 'Hodnota kategorie: Hodnoty lvalue a rvalue (C++)'
ms.date: 04/06/2018
helpviewer_keywords:
- R-values [C++]
- L-values [C++]
ms.assetid: a8843344-cccc-40be-b701-b71f7b5cdcaf
ms.openlocfilehash: 74bfac5f5bb56549eee41a5479babf8e71b00aa6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62245556"
---
# <a name="lvalues-and-rvalues-visual-c"></a>Hodnoty lvalue a rvalue (C++)

Každý výraz jazyka C++ má typ, patří *kategorií hodnot*. Hodnota kategorie jsou základem pro pravidla, která řídí kompilátory při vytváření, kopírování a přesouvání dočasné objekty při vyhodnocení výrazu.

Standardu C ++ 17 definuje kategorie hodnotu výrazu takto:

- A *glvalue* je výraz, jehož vyhodnocení určuje identitu objektu, bitového pole nebo funkce.
- A *hodnota, která není* je výraz, jehož vyhodnocení inicializuje objekt nebo bitové pole nebo vypočítá hodnotu operand operátoru, podle určeného kontextu, ve kterém se zobrazí.
- *Xvalue* je glvalue, který označuje objekt nebo bitové pole, jehož prostředky jde znovu použít (obvykle, protože je na konci svého životního cyklu). Příklad: Některé typy výrazy, které obsahují odkazy rvalue (8.3.2) yield osa x, hodnoty, jako je například přetypování na odkazový typ nebo volání funkce, jejíž návratový typ je odkaz rvalue.
- *L-hodnoty* je glvalue, který není xvalue.
- *Rvalue* hodnota, která není nebo xvalue.

Následující diagram znázorňuje vztahy mezi kategorií:

![Kategorie hodnotu výrazů C++](media/value_categories.png "kategorie hodnotu výrazu jazyka C++")

L-hodnota má adresu s přístupem k aplikaci. Výrazy l-hodnoty. Příklady názvy proměnných, včetně **const** proměnné, prvky pole, funkce volání, která vrátí odkaz na lvalue, bitová pole, sjednocení a členy třídy.

Hodnota, která není výraz nemá adresu, který je přístupný pro váš program. Příklady výrazů hodnota, která není jsou literály, volání funkce, které vracejí nereferenčního typu a dočasné objekty, které jsou vytvořeny během evalution výraz ale přístupný pouze pomocí kompilátoru.

Výraz hodnoty xvalue má adresu, která už nebude přístupný pro váš program však lze použít k inicializaci odkaz rvalue, který poskytuje přístup k výraz. Příklady zahrnují volání funkcí, které vrátí odkaz rvalue a dolní index pole, člen a ukazatel na člen výrazy kde pole nebo objekt je odkaz rvalue.

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

Podmínky *l-hodnoty* a *rvalue* jsou často používány při odkazu na odkazy objektu. Další informace o referencích naleznete v tématu [deklarátor odkazu Lvalue: &](../cpp/lvalue-reference-declarator-amp.md) a [Rvalue Reference Declarator: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="see-also"></a>Viz také:

[Základní koncepty](../cpp/basic-concepts-cpp.md)<br/>
[Deklarátor odkazu l-hodnoty: &](../cpp/lvalue-reference-declarator-amp.md)<br/>
[Deklarátor odkazu r-hodnoty: &&](../cpp/rvalue-reference-declarator-amp-amp.md)
