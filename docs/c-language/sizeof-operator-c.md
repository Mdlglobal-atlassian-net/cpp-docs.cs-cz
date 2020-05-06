---
title: sizeof – operátor (C)
ms.date: 11/04/2016
f1_keywords:
- sizeof
helpviewer_keywords:
- sizeof operator
ms.assetid: 70826d03-3451-41e4-bebb-a820ae66d53f
ms.openlocfilehash: 0bc0de5481cade10f89634d9e4ec78f4ec7b09f6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62158122"
---
# <a name="sizeof-operator-c"></a>sizeof – operátor (C)

Operátor `sizeof` poskytuje velikost úložiště (v bajtech) potřebného k uložení objektu typu operandu. Tento operátor vám umožní vyhnout se zadání velikosti dat závislých na počítači v programech.

## <a name="syntax"></a>Syntaxe

```
sizeof unary-expression
sizeof ( type-name )
```

## <a name="remarks"></a>Poznámky

Operand je identifikátor, který je *unární výraz*, nebo výraz přetypování typu (tj. specifikátor typu uzavřený v závorkách). *Unární výraz* nemůže představovat objekt bitového pole, nekompletního typu nebo označení funkce. Výsledkem je celočíselná konstanta bez znaménka. Standardní hlavičkový STDDEF. H definuje tento typ jako **size_t**.

Při použití operátoru `sizeof` na identifikátor pole bude výsledkem velikost celého pole namísto velikosti ukazatele reprezentovaného tímto identifikátorem pole.

Při použití operátoru `sizeof` na název typu struktury nebo sjednocení nebo na identifikátor typu struktury nebo sjednocení bude výsledkem počet bajtů v této struktuře nebo sjednocení, včetně vnitřního a koncového odsazení. Tato velikost může zahrnovat vnitřní a koncové odsazení použité pro zarovnání členů struktury nebo sjednocení na hranicích paměti. Proto výsledek nemusí nutně odpovídat velikosti vypočítané sečtením požadavků na úložiště jednotlivých členů.

Je-li posledním prvkem struktury pole bez velikosti, operátor `sizeof` vrátí velikost struktury bez tohoto pole.

```
buffer = calloc(100, sizeof (int) );
```

V tomto příkladu je operátor `sizeof` použit pro předání velikosti typu `int`, který se mezi počítači liší, jako argumentu funkce modulu runtime s názvem `calloc`. Hodnota vrácená touto funkcí je uložena v `buffer`.

```
static char *strings[] = {
      "this is string one",
      "this is string two",
      "this is string three",
   };
const int string_no = ( sizeof strings ) / ( sizeof strings[0] );
```

V tomto příkladu je proměnná `strings` pole ukazatelů na typ `char`. Počet ukazatelů je počet prvků v poli, ale není zadán. Chcete-li vypočítat počet prvků v tomto poli, lze počet ukazatelů snadno určit pomocí operátoru `sizeof`. `string_no` Hodnota **const** integer je inicializována na toto číslo. Protože se jedná o **konstantní** hodnotu, `string_no` nelze ji upravit.

## <a name="see-also"></a>Viz také

[Operátory jazyka C](c-operators.md)<br/>
[Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
