---
title: 'Relační operátory: &lt;, &gt;, &lt;= a &gt;='
ms.date: 11/04/2016
f1_keywords:
- <
- '>'
helpviewer_keywords:
- '> operator'
- less than operator
- relational operators [C++], syntax
- '>= operator'
- greater than or equal to operators [C++]
- greater than operators [C++]
- < operator
- less than or equal to operator
- <= operator
ms.assetid: d346b53d-f14d-4962-984f-89d39a17ca0f
ms.openlocfilehash: 38e05b78d334ca690d9523797f7ca1813834c5d3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179117"
---
# <a name="relational-operators-lt-gt-lt-and-gt"></a>Relační operátory: &lt;, &gt;, &lt;= a &gt;=

## <a name="syntax"></a>Syntaxe

```
expression < expression
expression > expression
expression <= expression
expression >= expression
```

## <a name="remarks"></a>Poznámky

Binární relační operátory určují následující vztahy:

- Menší než ( **\<** )

- Větší než ( **>** )

- Menší než nebo rovno ( **\<=** )

- Větší než nebo rovno ( **>=** )

Relační operátory mají asociativitu operátorů zleva doprava. Oba operandy relačních operátorů musejí mít aritmetický typ nebo typ ukazatele. Poskytují hodnoty typu **bool**. Vrácená hodnota je **false** (0), pokud je relace ve výrazu false; v opačném případě je vrácená hodnota **true** (1).

## <a name="example"></a>Příklad

```cpp
// expre_Relational_Operators.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;

int main() {
   cout  << "The true expression 3 > 2 yields: "
         << (3 > 2) << endl
         << "The false expression 20 < 10 yields: "
         << (20 < 10) << endl;
}
```

Výrazy v předchozím příkladu musí být uzavřeny v závorkách, protože operátor vložení datového proudu ( **<<** ) má vyšší prioritu než relační operátory. První výraz bez závorek by tedy byl vyhodnocen jako:

```cpp
(cout << "The true expression 3 > 2 yields: " << 3) < (2 << "\n");
```

Obvyklé aritmetické převody, které jsou pokryty [standardními](standard-conversions.md) převody, jsou aplikovány na operandy aritmetických typů.

## <a name="comparing-pointers"></a>Porovnávání ukazatelů

Při porovnání dvou ukazatelů s objekty stejného typu je výsledek určen umístěním objektů, na které je odkazováno v adresním prostoru programu. Ukazatele lze také porovnat s konstantním výrazem, který je vyhodnocen na hodnotu 0 nebo na ukazatel typu `void *`. Pokud je porovnání ukazatelů provedeno na ukazatel typu `void *`, druhý ukazatel je implicitně převeden na typ `void *`. Poté je provedeno porovnání.

Dva ukazatele na různé typy nelze srovnávat, pokud:

- jeden typ není typem třídy odvozeným z jiného typu,

- Nejméně jeden z ukazatelů je explicitně převeden (přetypování) na typ `void *`. (Druhý ukazatel je implicitně převeden na typ `void *` pro převod.)

není zaručeno, že dva odkazy stejného typu, které odkazují na stejný objekt, budou při porovnávání stejné. Pokud jsou porovnány dva ukazatele na nestatické členy objektu, platí následující pravidla:

- Pokud typ třídy není **sjednocení**a pokud dva členy nejsou odděleny *specifikátorem přístupu*, jako je například **Public**, **Protected**nebo **Private**, ukazatel na člen deklarovaný jako poslední bude porovnávat větší hodnotu než ukazatel na dříve deklarovaný člen.

- Pokud jsou dva členy odděleny *specifikátorem přístupu*, výsledky nejsou definovány.

- Pokud je typem třídy **sjednocení**, ukazatelé na různé datové členy v tomto **sjednocení** se rovnají.

Pokud dva ukazatele odkazují na prvky stejného pole nebo na prvek, který je za koncem tohoto pole, ukazatel na objekt s vyšším dolním indexem bude při porovnávání větší. Porovnání ukazatelů je zaručeno pouze v případě, že ukazatele odkazují na objekty stejného pole nebo na umístění za koncem pole.

## <a name="see-also"></a>Viz také

[Výrazy s binárními operátory](../cpp/expressions-with-binary-operators.md)<br/>
[Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Relační operátory a operátory rovnosti jazyka C](../c-language/c-relational-and-equality-operators.md)
