---
title: C++Předdefinované operátory, priority a asociativita
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
ms.openlocfilehash: 36e7ce77e24366be10b75f5bb4f8830363594301
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180404"
---
# <a name="c-built-in-operators-precedence-and-associativity"></a>C++Předdefinované operátory, priority a asociativita

Jazyk C++ obsahuje všechny operátory jazyka C a přidává několik nových operátorů. Operátory určují vyhodnocení, které má být provedeno na jednom nebo více operandů.

*Priorita* operátora určuje pořadí operací ve výrazech, které obsahují více než jeden operátor. *Asociativita* operátor určuje, zda ve výrazu, který obsahuje více operátorů se stejnou prioritou, je operand seskupen s jednou nebo na jeho pravé straně. Přednost a asociativita operátorů v jazyce C++ je uvedena v následující tabulce (od nejvyšší priority k nejnižší). Operátory se stejnou prioritou mají stejnou přednost, pokud pomocí závorek není explicitně vynucen jiný vztah.

### <a name="c-operator-precedence-and-associativity"></a>Přednost a asociativita operátorů v jazyce C++

|Popis operátoru|Operátor|
|--------------------------|--------------|
|**Priorita skupiny 1, žádné asociativita**|
|[Rozlišení rozsahu](../cpp/scope-resolution-operator.md)|[::](../cpp/scope-resolution-operator.md)|
|**Priorita skupiny 2, zleva doprava asociativita**|
|[Výběr členů (objekt nebo ukazatel)](../cpp/member-access-operators-dot-and.md)|[. nebo >](../cpp/member-access-operators-dot-and.md)|
|[Dolní index pole](../cpp/subscript-operator.md)|[&#91;&#93;](../cpp/subscript-operator.md)|
|[Volání funkce](../cpp/function-call-operator-parens.md)|[()](../cpp/function-call-operator-parens.md)|
|[Přírůstek přípony](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|[++](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|
|[Snížení přípony](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|[--](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|
|[Název typu](../cpp/typeid-operator.md)|[typeid](../cpp/typeid-operator.md)|
|[Převod typu konstanty](../cpp/const-cast-operator.md)|[const_cast](../cpp/const-cast-operator.md)|
|[Dynamický převod typu](../cpp/dynamic-cast-operator.md)|[dynamic_cast](../cpp/dynamic-cast-operator.md)|
|[Přeinterpretovaný převod typu](../cpp/reinterpret-cast-operator.md)|[reinterpret_cast](../cpp/reinterpret-cast-operator.md)|
|[Statický typ převodu](../cpp/static-cast-operator.md)|[static_cast](../cpp/static-cast-operator.md)|
|**Priorita skupiny 3, zprava doleva asociativita**|
|[Velikost objektu nebo typu](../cpp/sizeof-operator.md)|[sizeof](../cpp/sizeof-operator.md)|
|[Přírůstek předpony](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|[++](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|
|[Snížení předpony](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|[--](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|
|[Doplněk 1](../cpp/one-s-complement-operator-tilde.md)|[~](../cpp/one-s-complement-operator-tilde.md)|
|[Logický operátor NOT](../cpp/logical-negation-operator-exclpt.md)|[!](../cpp/logical-negation-operator-exclpt.md)|
|[Unární negace](../cpp/unary-plus-and-negation-operators-plus-and.md)|[-](../cpp/unary-plus-and-negation-operators-plus-and.md)|
|[Unární plus](../cpp/unary-plus-and-negation-operators-plus-and.md)|[+](../cpp/unary-plus-and-negation-operators-plus-and.md)|
|[Adresa](../cpp/address-of-operator-amp.md)|[&amp;](../cpp/address-of-operator-amp.md)|
|[Dereference](../cpp/indirection-operator-star.md)|[&#42;](../cpp/indirection-operator-star.md)|
|[Vytvořit objekt](../cpp/new-operator-cpp.md)|[new](../cpp/new-operator-cpp.md)|
|[Zničit objekt](../cpp/delete-operator-cpp.md)|[odstranění](../cpp/delete-operator-cpp.md)|
|[Využívají](../cpp/cast-operator-parens.md)|[()](../cpp/cast-operator-parens.md)|
|**Priorita skupiny 4, zleva doprava asociativita**|
|[Ukazatel na člena (objekty nebo ukazatele)](../cpp/pointer-to-member-operators-dot-star-and-star.md)|[. &#42; nebo >&#42;](../cpp/pointer-to-member-operators-dot-star-and-star.md)|
|**Priorita skupiny 5, zleva doprava asociativita**|
|[Násobení](../cpp/multiplicative-operators-and-the-modulus-operator.md)|[&#42;](../cpp/multiplicative-operators-and-the-modulus-operator.md)|
|[Dělení](../cpp/multiplicative-operators-and-the-modulus-operator.md)|[/](../cpp/multiplicative-operators-and-the-modulus-operator.md)|
|[Modulus](../cpp/multiplicative-operators-and-the-modulus-operator.md)|[%](../cpp/multiplicative-operators-and-the-modulus-operator.md)|
|**Priorita skupiny 6, zleva doprava asociativita**|
|[Sčítání](../cpp/additive-operators-plus-and.md)|[+](../cpp/additive-operators-plus-and.md)|
|[Odčítání](../cpp/additive-operators-plus-and.md)|[-](../cpp/additive-operators-plus-and.md)|
|**Priorita skupiny 7, zleva doprava asociativita**|
|[Posun doleva](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|[<<](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|
|[Posun doprava](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|[>>](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|
|**Skupina 8 s prioritou, zleva doprava asociativita**|
|[Je menší než](../cpp/relational-operators-equal-and-equal.md)|[<](../cpp/relational-operators-equal-and-equal.md)|
|[Větší než](../cpp/relational-operators-equal-and-equal.md)|[>](../cpp/relational-operators-equal-and-equal.md)|
|[Je menší než nebo rovno](../cpp/relational-operators-equal-and-equal.md)|[<=](../cpp/relational-operators-equal-and-equal.md)|
|[Je větší než nebo rovno](../cpp/relational-operators-equal-and-equal.md)|[>=](../cpp/relational-operators-equal-and-equal.md)|
|**Priorita skupiny 9, zleva doprava asociativita**|
|[Porovnávání](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|[==](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|
|[Nerovnost](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|[!=](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|
|**Levá asociativitaá priorita skupiny 10 vpravo**|
|[Bitový operátor AND](../cpp/bitwise-and-operator-amp.md)|[&amp;](../cpp/bitwise-and-operator-amp.md)|
|**Priorita skupiny 11, zleva doprava asociativita**|
|[Bitový exkluzivní operátor OR](../cpp/bitwise-exclusive-or-operator-hat.md)|[^](../cpp/bitwise-exclusive-or-operator-hat.md)|
|**Skupina 12 – priorita, zleva doprava asociativita**|
|[Bitový operátor OR](../cpp/bitwise-inclusive-or-operator-pipe.md)|[&#124;](../cpp/bitwise-inclusive-or-operator-pipe.md)|
|**Priorita skupiny 13, zleva doprava asociativita**|
|[Logický operátor AND](../cpp/logical-and-operator-amp-amp.md)|[&amp;&amp;](../cpp/logical-and-operator-amp-amp.md)|
|**Priorita skupiny 14, zleva doprava asociativita**|
|[Logický operátor OR](../cpp/logical-or-operator-pipe-pipe.md)|[&#124;&#124;](../cpp/logical-or-operator-pipe-pipe.md)|
|**Skupina 15 – priorita, zprava doleva asociativita**|
|[Podmíněného](../cpp/conditional-operator-q.md)|[? :](../cpp/conditional-operator-q.md)|
|**16. Priorita skupiny, zprava doleva asociativita**|
|[Přiřazení](../cpp/assignment-operators.md)|[=](../cpp/assignment-operators.md)|
|[Přiřazení násobení](../cpp/assignment-operators.md)|[&#42;=](../cpp/assignment-operators.md)|
|[Přiřazení divize](../cpp/assignment-operators.md)|[/=](../cpp/assignment-operators.md)|
|[Přiřazení modulu](../cpp/assignment-operators.md)|[%=](../cpp/assignment-operators.md)|
|[Přiřazení sčítání](../cpp/assignment-operators.md)|[+=](../cpp/assignment-operators.md)|
|[Přiřazení odčítání](../cpp/assignment-operators.md)|[-=](../cpp/assignment-operators.md)|
|[Přiřazení posunutí doleva](../cpp/assignment-operators.md)|[<<=](../cpp/assignment-operators.md)|
|[Přiřazení posunutí doprava](../cpp/assignment-operators.md)|[>>=](../cpp/assignment-operators.md)|
|[Bitový operátor AND přiřazení](../cpp/assignment-operators.md)|[&amp;=](../cpp/assignment-operators.md)|
|[Přiřazení s bitovým operátorem OR](../cpp/assignment-operators.md)|[&#124;=](../cpp/assignment-operators.md)|
|[Bitové exkluzivní přiřazení OR](../cpp/assignment-operators.md)|[^=](../cpp/assignment-operators.md)|
|**Skupina 17 – priorita zprava doleva asociativita**|
|[Výraz throw](../cpp/try-throw-and-catch-statements-cpp.md)|[throw](../cpp/try-throw-and-catch-statements-cpp.md)|
|**Skupina 18 – priorita, zleva doprava asociativita**|
|[Tečkou](../cpp/comma-operator.md)|[,](../cpp/comma-operator.md)|

## <a name="see-also"></a>Viz také

[Přetížení operátoru](operator-overloading.md)
