---
title: 'operátor sizeof: Operator (C) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- sizeof
dev_langs:
- C++
helpviewer_keywords:
- sizeof operator
ms.assetid: 70826d03-3451-41e4-bebb-a820ae66d53f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fa3c959e4a839521dddc78d97fbf77db2e1c4b99
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46080659"
---
# <a name="sizeof-operator-c"></a>sizeof – operátor (C)

Operátor `sizeof` poskytuje velikost úložiště (v bajtech) potřebného k uložení objektu typu operandu. Tento operátor umožňuje vyhnout zadávání velikosti dat závislé na počítače ve svých programech.

## <a name="syntax"></a>Syntaxe

```
sizeof unary-expression
sizeof ( type-name )
```

## <a name="remarks"></a>Poznámky

Operand je buď identifikátor, který je *unární výraz*, nebo výraz přetypování typu (to znamená typ specifikátoru uzavřený do závorek). *Unární výraz* nemůže reprezentovat bitové pole objektu, neúplný typ ani označení funkce. Výsledkem je celočíselná konstanta bez znaménka. Standardní hlavička STDDEF. H definuje tento typ jako **size_t**.

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

V tomto příkladu je proměnná `strings` pole ukazatelů na typ `char`. Počet ukazatelů je počet prvků v poli, ale není zadán. Chcete-li vypočítat počet prvků v tomto poli, lze počet ukazatelů snadno určit pomocí operátoru `sizeof`. **Const** celočíselnou hodnotu `string_no` je inicializován na toto číslo. Protože se jedná **const** hodnotu, `string_no` nelze upravit.

## <a name="see-also"></a>Viz také

[Operátory jazyka C](c-operators.md)<br/>
[Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
