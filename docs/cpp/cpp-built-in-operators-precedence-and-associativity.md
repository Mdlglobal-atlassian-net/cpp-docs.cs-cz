---
title: Předdefinované C++ operátory, prioritu a Asociativnost | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d4d2bb339d4147e6ea82c713d83a046e0e9780bb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32418426"
---
# <a name="c-built-in-operators-precedence-and-associativity"></a>Předdefinované C++ operátory, prioritu a Asociativnost

Jazyk C++ obsahuje všechny operátory jazyka C a přidává několik nových operátorů. Operátory určují vyhodnocení, které má být provedeno na jednom nebo více operandů.

Operátor *přednost* určuje pořadí operací ve výrazech, které obsahují více než jeden operátor. Operátor *asociativnost* Určuje, zda ve výrazu, který obsahuje více operátorů se stejnou prioritou, operand seskupené s jedním na levé straně, nebo byl na záhlavím vpravo. Přednost a asociativita operátorů v jazyce C++ je uvedena v následující tabulce (od nejvyšší priority k nejnižší). Operátory se stejnou prioritou mají stejnou přednost, pokud pomocí závorek není explicitně vynucen jiný vztah.

### <a name="c-operator-precedence-and-associativity"></a>Přednost a asociativita operátorů v jazyce C++

|Popis operátoru|Operátor|
|--------------------------|--------------|
|**Skupina 1 přednost, žádné asociativnost**|
|[Řešení rozsahu](../cpp/scope-resolution-operator.md)|[::](../cpp/scope-resolution-operator.md)|
|**Skupina 2 přednost, zleva doprava asociativnost**|
|[Výběr členů (objekt nebo ukazatele)](../cpp/member-access-operators-dot-and.md)|[. nebo ->](../cpp/member-access-operators-dot-and.md)|
|[Dolní index pole](../cpp/subscript-operator.md)|[&#91;&#93;](../cpp/subscript-operator.md)|
|[Volání funkce](../cpp/function-call-operator-parens.md)|[()](../cpp/function-call-operator-parens.md)|
|[Operátory přírůstku](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|[++](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|
|[Operátory snížení](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|[--](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|
|[Název typu](../cpp/typeid-operator.md)|[typeid](../cpp/typeid-operator.md)|
|[Převod typu konstanty.](../cpp/const-cast-operator.md)|[const_cast –](../cpp/const-cast-operator.md)|
|[Dynamický typ převodu](../cpp/dynamic-cast-operator.md)|[dynamic_cast –](../cpp/dynamic-cast-operator.md)|
|[Převod reinterpreted typů](../cpp/reinterpret-cast-operator.md)|[reinterpret_cast –](../cpp/reinterpret-cast-operator.md)|
|[Převod typu statické](../cpp/static-cast-operator.md)|[static_cast –](../cpp/static-cast-operator.md)|
|**Skupina 3 přednost právo na levém asociativnost**|
|[Velikost objektu nebo typ](../cpp/sizeof-operator.md)|[sizeof](../cpp/sizeof-operator.md)|
|[Předpona přírůstku](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|[++](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|
|[Snížení předpony](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|[--](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|
|[Jednu pro doplňku](../cpp/one-s-complement-operator-tilde.md)|[~](../cpp/one-s-complement-operator-tilde.md)|
|[Logická negace](../cpp/logical-negation-operator-exclpt.md)|[\!](../cpp/logical-negation-operator-exclpt.md)|
|[Unární negace](../cpp/unary-plus-and-negation-operators-plus-and.md)|[-](../cpp/unary-plus-and-negation-operators-plus-and.md)|
|[Unární plus](../cpp/unary-plus-and-negation-operators-plus-and.md)|[+](../cpp/unary-plus-and-negation-operators-plus-and.md)|
|[Adresa](../cpp/address-of-operator-amp.md)|[&amp;](../cpp/address-of-operator-amp.md)|
|[Indirection](../cpp/indirection-operator-star.md)|[&#42;](../cpp/indirection-operator-star.md)|
|[Vytvoření objektu](../cpp/new-operator-cpp.md)|[new](../cpp/new-operator-cpp.md)|
|[Destroy – objekt](../cpp/delete-operator-cpp.md)|[delete](../cpp/delete-operator-cpp.md)|
|[Přetypování](../cpp/cast-operator-parens.md)|[()](../cpp/cast-operator-parens.md)|
|**Skupina 4 přednost, zleva doprava asociativnost**|
|[Ukazatele na člena (objekty nebo ukazatele)](../cpp/pointer-to-member-operators-dot-star-and-star.md)|[. &#42; nebo ->&#42;](../cpp/pointer-to-member-operators-dot-star-and-star.md)|
|**Skupiny 5 přednost, zleva doprava asociativnost**|
|[Násobení](../cpp/multiplicative-operators-and-the-modulus-operator.md)|[&#42;](../cpp/multiplicative-operators-and-the-modulus-operator.md)|
|[dělení](../cpp/multiplicative-operators-and-the-modulus-operator.md)|[/](../cpp/multiplicative-operators-and-the-modulus-operator.md)|
|[numerického zbytku](../cpp/multiplicative-operators-and-the-modulus-operator.md)|[%](../cpp/multiplicative-operators-and-the-modulus-operator.md)|
|**Skupiny 6 přednost, zleva doprava asociativnost**|
|[Přidání](../cpp/additive-operators-plus-and.md)|[+](../cpp/additive-operators-plus-and.md)|
|[Odčítání](../cpp/additive-operators-plus-and.md)|[-](../cpp/additive-operators-plus-and.md)|
|**Skupiny 7 přednost, zleva doprava asociativnost**|
|[Posunutí doleva](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|[<<](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|
|[Posunutí doprava](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|[>>](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|
|**Skupiny 8 přednost, zleva doprava asociativnost**|
|[Menší než](../cpp/relational-operators-equal-and-equal.md)|[<](../cpp/relational-operators-equal-and-equal.md)|
|[Větší než](../cpp/relational-operators-equal-and-equal.md)|[>](../cpp/relational-operators-equal-and-equal.md)|
|[Menší než nebo rovno](../cpp/relational-operators-equal-and-equal.md)|[<=](../cpp/relational-operators-equal-and-equal.md)|
|[Větší než nebo rovno](../cpp/relational-operators-equal-and-equal.md)|[>=](../cpp/relational-operators-equal-and-equal.md)|
|**Priorita skupiny 9, zleva doprava asociativnost**|
|[Rovnosti](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|[==](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|
|[Nerovnosti](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|[\!=](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|
|**Priorita skupiny 10 zleva doprava asociativnost**|
|[Bitový operátor AND](../cpp/bitwise-and-operator-amp.md)|[&amp;](../cpp/bitwise-and-operator-amp.md)|
|**Priorita skupiny 11, zleva doprava asociativnost**|
|[Bitový exkluzivní nebo](../cpp/bitwise-exclusive-or-operator-hat.md)|[^](../cpp/bitwise-exclusive-or-operator-hat.md)|
|**Skupina 12 přednost, zleva doprava asociativnost**|
|[Bitový inkluzivní nebo](../cpp/bitwise-inclusive-or-operator-pipe.md)|[&#124;](../cpp/bitwise-inclusive-or-operator-pipe.md)|
|**Skupiny 13 přednost, zleva doprava asociativnost**|
|[Logické a](../cpp/logical-and-operator-amp-amp.md)|[&amp;&amp;](../cpp/logical-and-operator-amp-amp.md)|
|**Skupina 14 přednost, zleva doprava asociativnost**|
|[Logické nebo](../cpp/logical-or-operator-pipe-pipe.md)|[&#124;&#124;](../cpp/logical-or-operator-pipe-pipe.md)|
|**Skupiny přednost před 15 právo na levém asociativnost**|
|[Podmíněné](../cpp/conditional-operator-q.md)|[? :](../cpp/conditional-operator-q.md)|
|**Priorita skupiny 16 právo na levém asociativnost**|
|[Přiřazení](../cpp/assignment-operators.md)|[=](../cpp/assignment-operators.md)|
|[Přiřazení násobení](../cpp/assignment-operators.md)|[&#42;=](../cpp/assignment-operators.md)|
|[Přiřazení dělení](../cpp/assignment-operators.md)|[/=](../cpp/assignment-operators.md)|
|[Přiřazení numerického zbytku](../cpp/assignment-operators.md)|[%=](../cpp/assignment-operators.md)|
|[Přidání přiřazení](../cpp/assignment-operators.md)|[+=](../cpp/assignment-operators.md)|
|[Přiřazení odčítání](../cpp/assignment-operators.md)|[-=](../cpp/assignment-operators.md)|
|[Přiřazení posunutí doleva](../cpp/assignment-operators.md)|[<<=](../cpp/assignment-operators.md)|
|[Přiřazení posunutí doprava](../cpp/assignment-operators.md)|[>>=](../cpp/assignment-operators.md)|
|[Přiřazení bitové operace AND](../cpp/assignment-operators.md)|[&amp;=](../cpp/assignment-operators.md)|
|[Bitový inkluzivní nebo přiřazení](../cpp/assignment-operators.md)|[&#124;=](../cpp/assignment-operators.md)|
|[Bitový exkluzivní OR přiřazení](../cpp/assignment-operators.md)|[^=](../cpp/assignment-operators.md)|
|**Priorita skupiny 17 právo na levém asociativnost**|
|[throw – výraz](../cpp/try-throw-and-catch-statements-cpp.md)|[throw](../cpp/try-throw-and-catch-statements-cpp.md)|
|**Skupiny 18 přednost, zleva doprava asociativnost**|
|[Čárkami](../cpp/comma-operator.md)|[,](../cpp/comma-operator.md)|

## <a name="see-also"></a>Viz také

[Přetížení operátoru](operator-overloading.md)


