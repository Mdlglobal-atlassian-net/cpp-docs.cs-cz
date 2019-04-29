---
title: Integrované operátory C++, Priorita a asociativita
ms.date: 11/04/2016
helpviewer_keywords:
- operators (C++), hierarchy
- operator precedence
- precedence, operators
- operators (C++), associativity
- multiple operators [C++]
- associativity of operators [C++]
- operators [C++], precedence
- evaluation order
- hierarchy, operator
ms.assetid: 95c1f0ba-dad8-4034-b039-f79a904f112f
ms.openlocfilehash: 0b560913deb57393a8547f0831e0d987eed41ab7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392346"
---
# <a name="c-built-in-operators-precedence-and-associativity"></a>Integrované operátory C++, Priorita a asociativita

Jazyk C++ obsahuje všechny operátory jazyka C a přidává několik nových operátorů. Operátory určují vyhodnocení, které má být provedeno na jednom nebo více operandů.

Operátor *prioritu* určuje pořadí operací ve výrazech, které obsahují více než jeden operátor. Operátor *asociativita* Určuje, zda ve výrazu, který obsahuje více operátorů se stejnou prioritou, je operand seskupen s jedním na levé straně nebo jeden napravo. Přednost a asociativita operátorů v jazyce C++ je uvedena v následující tabulce (od nejvyšší priority k nejnižší). Operátory se stejnou prioritou mají stejnou přednost, pokud pomocí závorek není explicitně vynucen jiný vztah.

### <a name="c-operator-precedence-and-associativity"></a>Přednost a asociativita operátorů v jazyce C++

|Popis operátoru|Operátor|
|--------------------------|--------------|
|**Skupina 1 prioritu, žádné asociativita**|
|[Řešení rozsahu](../cpp/scope-resolution-operator.md)|[::](../cpp/scope-resolution-operator.md)|
|**2. skupina prioritu, zleva doprava asociativita**|
|[Výběr členů (objekt nebo ukazatel)](../cpp/member-access-operators-dot-and.md)|[. nebo ->](../cpp/member-access-operators-dot-and.md)|
|[Dolní index pole](../cpp/subscript-operator.md)|[&#91;&#93;](../cpp/subscript-operator.md)|
|[Volání funkce](../cpp/function-call-operator-parens.md)|[()](../cpp/function-call-operator-parens.md)|
|[Zvýšení příponového operátora](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|[++](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|
|[Snížení příponového operátora](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|[--](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|
|[Název typu](../cpp/typeid-operator.md)|[typeid](../cpp/typeid-operator.md)|
|[Konstantní typ převodu](../cpp/const-cast-operator.md)|[const_cast](../cpp/const-cast-operator.md)|
|[Dynamický typ převodu](../cpp/dynamic-cast-operator.md)|[dynamic_cast](../cpp/dynamic-cast-operator.md)|
|[Znovu interpretovaný typ převodu](../cpp/reinterpret-cast-operator.md)|[reinterpret_cast](../cpp/reinterpret-cast-operator.md)|
|[Statický typ převodu](../cpp/static-cast-operator.md)|[static_cast](../cpp/static-cast-operator.md)|
|**Priorita skupiny 3 zprava asociativitu**|
|[Velikost objektu nebo typu](../cpp/sizeof-operator.md)|[sizeof](../cpp/sizeof-operator.md)|
|[Předponového](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|[++](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|
|[Snížení předpony](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|[--](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|
|[Doplněk](../cpp/one-s-complement-operator-tilde.md)|[~](../cpp/one-s-complement-operator-tilde.md)|
|[Logický operátor not](../cpp/logical-negation-operator-exclpt.md)|[\!](../cpp/logical-negation-operator-exclpt.md)|
|[Unární negace](../cpp/unary-plus-and-negation-operators-plus-and.md)|[-](../cpp/unary-plus-and-negation-operators-plus-and.md)|
|[Unární plus](../cpp/unary-plus-and-negation-operators-plus-and.md)|[+](../cpp/unary-plus-and-negation-operators-plus-and.md)|
|[Adresa](../cpp/address-of-operator-amp.md)|[&amp;](../cpp/address-of-operator-amp.md)|
|[Indirekce](../cpp/indirection-operator-star.md)|[&#42;](../cpp/indirection-operator-star.md)|
|[Vytvoření objektu](../cpp/new-operator-cpp.md)|[new](../cpp/new-operator-cpp.md)|
|[Zničit objekt](../cpp/delete-operator-cpp.md)|[delete](../cpp/delete-operator-cpp.md)|
|[Přetypování](../cpp/cast-operator-parens.md)|[()](../cpp/cast-operator-parens.md)|
|**Priorita skupiny 4, zleva doprava asociativita**|
|[Pointer-to-member (objekty nebo ukazatele)](../cpp/pointer-to-member-operators-dot-star-and-star.md)|[. &#42; nebo ->&#42;](../cpp/pointer-to-member-operators-dot-star-and-star.md)|
|**Priorita skupiny 5, zleva doprava asociativita**|
|[Násobení](../cpp/multiplicative-operators-and-the-modulus-operator.md)|[&#42;](../cpp/multiplicative-operators-and-the-modulus-operator.md)|
|[Dělení](../cpp/multiplicative-operators-and-the-modulus-operator.md)|[/](../cpp/multiplicative-operators-and-the-modulus-operator.md)|
|[Modulus](../cpp/multiplicative-operators-and-the-modulus-operator.md)|[%](../cpp/multiplicative-operators-and-the-modulus-operator.md)|
|**Priorita skupiny 6, zleva doprava asociativita**|
|[Přidání](../cpp/additive-operators-plus-and.md)|[+](../cpp/additive-operators-plus-and.md)|
|[Odčítání](../cpp/additive-operators-plus-and.md)|[-](../cpp/additive-operators-plus-and.md)|
|**Priorita skupiny 7, zleva doprava asociativita**|
|[Operátor posunu vlevo](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|[<<](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|
|[Posunutí doprava](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|[>>](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|
|**Skupiny 8 prioritu, zleva doprava asociativita**|
|[Menší než](../cpp/relational-operators-equal-and-equal.md)|[<](../cpp/relational-operators-equal-and-equal.md)|
|[Větší než](../cpp/relational-operators-equal-and-equal.md)|[>](../cpp/relational-operators-equal-and-equal.md)|
|[Menší než nebo rovno](../cpp/relational-operators-equal-and-equal.md)|[<=](../cpp/relational-operators-equal-and-equal.md)|
|[Větší než nebo rovno](../cpp/relational-operators-equal-and-equal.md)|[>=](../cpp/relational-operators-equal-and-equal.md)|
|**Priorita skupiny 9, zleva doprava asociativita**|
|[Rovnost](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|[==](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|
|[Nerovnost](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|[\!=](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|
|**Priorita skupiny 10 zleva doprava asociativita**|
|[Bitový operátor AND](../cpp/bitwise-and-operator-amp.md)|[&amp;](../cpp/bitwise-and-operator-amp.md)|
|**Priorita skupiny 11, zleva doprava asociativita**|
|[Bitový exkluzivní operátor OR](../cpp/bitwise-exclusive-or-operator-hat.md)|[^](../cpp/bitwise-exclusive-or-operator-hat.md)|
|**Priorita skupiny 12, zleva doprava asociativita**|
|[Bitový inkluzivní OR](../cpp/bitwise-inclusive-or-operator-pipe.md)|[&#124;](../cpp/bitwise-inclusive-or-operator-pipe.md)|
|**Priorita skupiny 13, zleva doprava asociativita**|
|[Logický operátor AND](../cpp/logical-and-operator-amp-amp.md)|[&amp;&amp;](../cpp/logical-and-operator-amp-amp.md)|
|**Skupina 14 prioritu, zleva doprava asociativita**|
|[Logický operátor OR](../cpp/logical-or-operator-pipe-pipe.md)|[&#124;&#124;](../cpp/logical-or-operator-pipe-pipe.md)|
|**Priorita skupiny 15 zprava asociativitu**|
|[Podmíněné](../cpp/conditional-operator-q.md)|[? :](../cpp/conditional-operator-q.md)|
|**Priorita skupiny 16 zprava asociativitu**|
|[Přiřazení](../cpp/assignment-operators.md)|[=](../cpp/assignment-operators.md)|
|[Přiřazení násobení](../cpp/assignment-operators.md)|[&#42;=](../cpp/assignment-operators.md)|
|[Přiřazení dělení](../cpp/assignment-operators.md)|[/=](../cpp/assignment-operators.md)|
|[Přiřazení MODULUS](../cpp/assignment-operators.md)|[%=](../cpp/assignment-operators.md)|
|[Přiřazení sčítání](../cpp/assignment-operators.md)|[+=](../cpp/assignment-operators.md)|
|[Přiřazení odčítání](../cpp/assignment-operators.md)|[-=](../cpp/assignment-operators.md)|
|[Přiřazení posunutí doleva](../cpp/assignment-operators.md)|[<<=](../cpp/assignment-operators.md)|
|[Přiřazení posunutí doprava](../cpp/assignment-operators.md)|[>>=](../cpp/assignment-operators.md)|
|[Přiřazení bitového operátoru AND](../cpp/assignment-operators.md)|[&amp;=](../cpp/assignment-operators.md)|
|[Bitový inkluzivní OR přiřazení](../cpp/assignment-operators.md)|[&#124;=](../cpp/assignment-operators.md)|
|[Bitový exkluzivní OR přiřazení](../cpp/assignment-operators.md)|[^=](../cpp/assignment-operators.md)|
|**Priorita skupiny 17 zprava asociativitu**|
|[výraz throw](../cpp/try-throw-and-catch-statements-cpp.md)|[throw](../cpp/try-throw-and-catch-statements-cpp.md)|
|**Skupiny 18 prioritu, zleva doprava asociativita**|
|[Čárka](../cpp/comma-operator.md)|[,](../cpp/comma-operator.md)|

## <a name="see-also"></a>Viz také:

[Přetížení operátoru](operator-overloading.md)