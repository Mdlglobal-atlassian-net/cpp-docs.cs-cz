---
title: Jednorozměrná pole | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- brackets [ ]
- brackets [ ], arrays
- one-dimensional arrays
- arrays [C++], one-dimensional
- square brackets [ ]
- square brackets [ ], arrays
- subscript expressions
ms.assetid: e28536e5-3b77-46b5-97fd-9b938c771816
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cde6bfbdf7ec72a9c1db6a7cb77613163400d737
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46087887"
---
# <a name="one-dimensional-arrays"></a>Jednorozměrná pole

Výraz přípony následovaný výraz v hranatých závorkách (**[] č.**) je zkratkou reprezentace elementu objektu array. Výraz dolního indexu představuje hodnotu na adrese, která je *výraz* umístí nad rámec *postfix-expression* při vyjádřený jako

```
postfix-expression [ expression ]
```

Obvykle hodnota reprezentovaná *postfix-expression* je hodnota ukazatele, jako je například identifikátor pole a *výraz* je celé číslo. Všechny možnosti, které je však vyžaduje syntakticky je jeden z výrazů být typu ukazatele a druhý být celočíselného typu. Proto může být celočíselná hodnota v *postfix-expression* pozice a hodnota ukazatele může být v závorkách v *výraz*, nebo "dolního indexu," pozici. Například tento kód je platný:

```
// one_dimensional_arrays.c
int sum, *ptr, a[10];
int main() {
   ptr = a;
   sum = 4[ptr];
}
```

Výrazy dolního indexu se obecně používají k odkazování na prvky pole, ale index můžete použít na jakýkoli ukazatel. Bez ohledu pořadí hodnot, *výraz* musí být uzavřen v závorkách (**[] č.**).

Výraz dolního indexu je vyhodnocován přidáním celočíselné hodnoty na hodnotu ukazatele a použití indirection – operátor (<strong>\**</strong>) na výsledek. (Viz [dereference a Address-of operátory](../c-language/indirection-and-address-of-operators.md) diskuzi o operátoru dereference.) V důsledku toho pro jednorozměrné pole, následující čtyři výrazy jsou ekvivalentní, za předpokladu, že `a` ukazatel a `b` je celé číslo:

```
a[b]
*(a + b)
*(b + a)
b[a]
```

Podle pravidla převodu pro operátor sčítání (v daném [operátory součtu](../c-language/c-additive-operators.md)), celočíselné hodnoty je převedena na posun adresy vynásobením délka typ adresovaný ukazatelem.

Předpokládejme například, identifikátor `line` odkazuje na pole `int` hodnoty. Následující postup slouží k vyhodnocení výrazu dolního indexu `line[ i ]`:

1. Celočíselná hodnota `i` se násobí hodnotou počet bajtů, které jsou definované jako délku `int` položky. Převedená hodnota `i` představuje `i` `int` pozic.

1. Tato hodnota převedená se přidá k hodnotě původního ukazatele (`line`) pozastavit adresu, která je `i` `int` umístí z `line`.

1. Operátor dereference je použit na novou adresu. Výsledkem je hodnota prvku pole na této pozici (intuitivně, `line [ i ]`).

Výraz dolního indexu `line[0]` představuje hodnotu elementu první řádek, od posun od adrese reprezentované výrazem `line` je 0. Obdobně výrazu, jako `line[5]` odkazuje na element pozice posun pět z řádku nebo šestého prvku v poli.

## <a name="see-also"></a>Viz také

[Operátor dolního indexu: []](../cpp/subscript-operator.md)