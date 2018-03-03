---
title: "Jednorozměrná pole | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 033d772a40ddf55474ca845c9c5708423bcf5e90
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="one-dimensional-arrays"></a>Jednorozměrná pole
Výraz operátory následováno výrazem do hranatých závorek (**[]**) je dolního indexu reprezentace elementu objektu array. Výraz dolního indexu představuje hodnotu na adresu, která je *výraz* umisťuje nad rámec *operátory výraz* při vyjádřený jako  
  
```  
  
postfix-expression  
[  
expression  
]  
  
```  
  
 Obvykle hodnota reprezentována *operátory výraz* je hodnota ukazatele, jako je například identifikátorem pole a *výraz* je celočíselné hodnoty. Ale všechny možnosti, které je vyžadován syntakticky jeden z výrazů se ukazatel typu a dalších být integrální typu. Proto integrální hodnotou může být v *operátory výraz* pozice a hodnota ukazatele s hodnotou může být v závorkách v *výraz*, nebo "dolního indexu," pozici. Tento kód je například právní informace:  
  
```  
// one_dimensional_arrays.c  
int sum, *ptr, a[10];  
int main() {  
   ptr = a;  
   sum = 4[ptr];  
}  
```  
  
 Výrazy v dolním indexu se obecně používají k odkazování na elementy pole, ale můžete použít dolní index pro všechny ukazatele. Ať pořadí hodnot, *výraz* musí být uzavřena do hranatých závorek (**[]**).  
  
 Výraz dolního indexu je vyhodnocován přidáním celočíselné hodnoty na hodnotu ukazatele a použití indirection – operátor (**\***) na výsledek. (Viz [Deferenční operátory a operátory adresy](../c-language/indirection-and-address-of-operators.md) diskuzi o deferenční operátor.) Ve skutečnosti pro jednorozměrné pole, následující čtyři výrazy jsou ekvivalentní, za předpokladu, který `a` ukazatel a `b` je celé číslo:  
  
```  
a[b]  
*(a + b)  
*(b + a)  
b[a]  
```  
  
 Podle pravidel převodu pro operátor sčítání (daného v [doplňkové operátory](../c-language/c-additive-operators.md)), celočíselné hodnoty jsou převedeny na adresu posun vynásobením délka typu řešit ukazatel.  
  
 Předpokládejme například, identifikátor `line` odkazuje na pole `int` hodnoty. Následující postup slouží k vyhodnocení výraz dolního indexu `line[ i ]`:  
  
1.  Celočíselná hodnota `i` se násobí hodnotou počet bajtů, které jsou definované jako délka `int` položky. Převedená hodnota `i` představuje `i` `int` pozic.  
  
2.  Tato převedená hodnota se přidá na původní hodnotu ukazatele (`line`) k získání adresu, která je posun `i` `int` umisťuje z `line`.  
  
3.  Deferenční operátor je použita na novou adresu. Výsledkem je hodnota elementu pole na této pozici (intuitivně, `line [ i ]`).  
  
 Výraz dolního indexu `line[0]` představuje hodnotu první prvek řádku, od posun z adresy reprezentována `line` je 0. Podobně výrazem jako `line[5]` odkazuje na pozice posun pět element z řádku nebo element šesté pole.  
  
## <a name="see-also"></a>Viz také  
 [Operátor dolního indexu: []](../cpp/subscript-operator.md)