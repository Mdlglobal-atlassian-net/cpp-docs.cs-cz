---
title: Jednorozměrná pole
ms.date: 11/04/2016
helpviewer_keywords:
- brackets [ ]
- brackets [ ], arrays
- one-dimensional arrays
- arrays [C++], one-dimensional
- square brackets [ ]
- square brackets [ ], arrays
- subscript expressions
ms.assetid: e28536e5-3b77-46b5-97fd-9b938c771816
ms.openlocfilehash: 7ac57a65d575ba6a9134f3c4474103735411847d
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75299101"
---
# <a name="one-dimensional-arrays"></a>Jednorozměrná pole

Výraz přípony následovaný výrazem v hranatých závorkách (**[]**) je podskriptovaná reprezentace elementu objektu Array. Výraz dolního indexu představuje hodnotu na adrese, která je pozice *výrazu* za *příponový výraz* , pokud je vyjádřena jako

```
postfix-expression [ expression ]
```

Obvykle hodnota reprezentovaná *příponovým výrazem* je hodnota ukazatele, jako je například identifikátor pole a *výraz* je celočíselná hodnota. Nicméně vše vyžadované syntakticky je, že jeden z výrazů je typu ukazatele a druhý je celočíselný typ. Celočíselná hodnota by tedy mohla být na pozici *příponového výrazu* a hodnota ukazatele může být v závorkách ve *výrazu*nebo "dolní index". Například tento kód je platný:

```c
// one_dimensional_arrays.c
int sum, *ptr, a[10];
int main() {
   ptr = a;
   sum = 4[ptr];
}
```

Výrazy dolního indexu se obecně používají pro odkazování na prvky pole, ale můžete použít i dolní index na libovolný ukazatel. Bez ohledu na pořadí hodnot musí být *výraz* uzavřen do hranatých závorek (**[]**).

Výraz dolního indexu je vyhodnocen přidáním celočíselné hodnoty do hodnoty ukazatele a následným použitím operátoru dereference (<strong>\*</strong>) na výsledek. (Viz téma [dereference a operátory adresy](../c-language/indirection-and-address-of-operators.md) pro diskuzi operátoru dereference.) V důsledku toho je pro jednorozměrné pole ekvivalentní následující čtyři výrazy, za předpokladu, že `a` se jedná o ukazatel a `b` je celé číslo:

```
a[b]
*(a + b)
*(b + a)
b[a]
```

V souladu s pravidly převodu pro operátor sčítání (předané v [operátorech](../c-language/c-additive-operators.md)sčítání) je celočíselná hodnota převedena na posun adresy tím, že je vynásobí délkou typu řešeného ukazatelem.

Předpokládejme například, že identifikátor `line` odkazuje na pole `int` hodnot. Následující postup slouží k vyhodnocení výrazu `line[ i ]`dolního indexu:

1. Celočíselná hodnota `i` je vynásobena počtem bajtů definovaných jako délka `int` položky. Převedená hodnota `i` představuje `i` `int` pozice.

1. Tato převedená hodnota se přidá do původní hodnoty ukazatele`line`(), aby se vyrovnala `i` `int` adresa, `line`na které se posunou pozice.

1. Operátor dereference se použije na novou adresu. Výsledkem je hodnota prvku pole na této pozici (intuitivní, `line [ i ]`).

Výraz `line[0]` dolního indexu představuje hodnotu prvního prvku řádku, protože posun z adresy reprezentovaný hodnotou `line` je 0. Podobně výraz, jako je například `line[5]` , odkazuje na posun prvku o pět pozic od řádku nebo šestý prvek pole.

## <a name="see-also"></a>Viz také

[Operátor dolního indexu:](../cpp/subscript-operator.md)
