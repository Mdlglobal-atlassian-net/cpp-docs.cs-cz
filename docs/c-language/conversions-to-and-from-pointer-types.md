---
title: Převod na a z typů ukazatele
ms.date: 11/04/2016
helpviewer_keywords:
- pointers, converting
- conversions, pointer
- type casts, involving pointers
- void pointers
ms.assetid: 3facc56f-06d3-4570-b1a2-7d4927b83086
ms.openlocfilehash: 2d907dbcf4f826d364fb68ce65f7d44c6cfe97cd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62312405"
---
# <a name="conversions-to-and-from-pointer-types"></a>Převod na a z typů ukazatele

Ukazatel na jeden typ hodnoty lze převést na ukazatel na jiný typ. Výsledek však může být nedefinovaný z důvodu požadavků na přiřazení a velikostí různých typů v úložišti. Ukazatel na objekt lze převést na ukazatel na objekt, jehož typ vyžaduje méně nebo stejně striktní zarovnání úložiště, a beze změny také zpět.

Ukazatel na typ `void` lze převést na libovolný typ a zpět bez omezení či ztráty informací. Je-li výsledek převeden zpět na původní typ, je původní ukazatel obnoven.

Je-li ukazatel převeden na jiný ukazatel stejného typu, ale s jinými dodatečnými kvalifikátory, je nový ukazatel stejný jako původní kromě omezení zavedených novým kvalifikátorem.

Hodnotu ukazatele lze také převést na celočíselnou hodnotu. Cesta převodu závisí na velikosti ukazatele a celočíselného typu dle následujících pravidel:

- Je-li velikost ukazatele větší nebo rovna velikosti celočíselného typu, chová se ukazatel při převodu jako hodnota bez znaménka kromě skutečnosti, že jej nelze převést na hodnotu s plovoucí desetinnou čárkou.

- Je-li ukazatel menší než celočíselný typ, je ukazatel nejprve převeden na ukazatel velikosti shodné s celočíselným typem a poté na celočíselný typ.

Celočíselný typ lze naopak převést na typ ukazatele dle následujících pravidel:

- Je-li celočíselný typ stejné velikosti jako typ ukazatele, převod pouze zajistí, že je celočíselný typ považován za ukazatel (celé číslo bez znaménka).

- Pokud je velikost integrálního typu odlišná od velikosti typu ukazatele, je celočíselný typ nejprve převeden na velikost ukazatele pomocí cest převodu předaných v tabulkách v rámci převodů [z](../c-language/conversions-from-signed-integral-types.md) celočíselných typů a [převodů z nepodepsaných integrálních typů](../c-language/conversions-from-unsigned-integral-types.md). Poté je považován za hodnotu ukazatele.

Celočíselný konstantní výraz s hodnotou 0 nebo přetypování výrazu na typ **void** <strong>\*</strong> lze převést pomocí přetypování typu, přiřazením nebo porovnáním s ukazatelem libovolného typu. Tím dojde k vytvoření nulového ukazatele, který je roven jinému nulovému ukazateli stejného typu, avšak tento nulový ukazatel není roven jinému ukazateli na funkci nebo objekt. Celá čísla jiná než konstantní 0 lze převést na typ ukazatele, ale výsledek není přenosný.

## <a name="see-also"></a>Viz také

[Převody přiřazení](../c-language/assignment-conversions.md)
