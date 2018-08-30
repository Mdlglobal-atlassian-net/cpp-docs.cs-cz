---
title: Převod na a z typů ukazatele | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- pointers, converting
- conversions, pointer
- type casts, involving pointers
- void pointers
ms.assetid: 3facc56f-06d3-4570-b1a2-7d4927b83086
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c8ddcaa55e3b88e715428ea8fa44c897ab5f8b4f
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43216095"
---
# <a name="conversions-to-and-from-pointer-types"></a>Převod na a z typů ukazatele
Ukazatel na jeden typ hodnoty lze převést na ukazatel na jiný typ. Výsledek však může být nedefinovaný z důvodu požadavků na přiřazení a velikostí různých typů v úložišti. Ukazatel na objekt lze převést na ukazatel na objekt, jehož typ vyžaduje méně nebo stejně striktní zarovnání úložiště, a beze změny také zpět.  
  
 Ukazatel na typ `void` lze převést na libovolný typ a zpět bez omezení či ztráty informací. Je-li výsledek převeden zpět na původní typ, je původní ukazatel obnoven.  
  
 Je-li ukazatel převeden na jiný ukazatel stejného typu, ale s jinými dodatečnými kvalifikátory, je nový ukazatel stejný jako původní kromě omezení zavedených novým kvalifikátorem.  
  
 Hodnotu ukazatele lze také převést na celočíselnou hodnotu. Cesta převodu závisí na velikosti ukazatele a celočíselného typu dle následujících pravidel:  
  
-   Je-li velikost ukazatele větší nebo rovna velikosti celočíselného typu, chová se ukazatel při převodu jako hodnota bez znaménka kromě skutečnosti, že jej nelze převést na hodnotu s plovoucí desetinnou čárkou.  
  
-   Je-li ukazatel menší než celočíselný typ, je ukazatel nejprve převeden na ukazatel velikosti shodné s celočíselným typem a poté na celočíselný typ.  
  
 Celočíselný typ lze naopak převést na typ ukazatele dle následujících pravidel:  
  
-   Je-li celočíselný typ stejné velikosti jako typ ukazatele, převod pouze zajistí, že je celočíselný typ považován za ukazatel (celé číslo bez znaménka).  
  
-   Je-li velikost celočíselného typu se liší od velikosti typu ukazatele, celočíselný typ nejprve převeden na velikost ukazatele pomocí cest převodu dle tabulek [převod z celočíselných typů se znaménkem](../c-language/conversions-from-signed-integral-types.md) a [ Převod z celočíselných typů bez znaménka](../c-language/conversions-from-unsigned-integral-types.md). Poté je považován za hodnotu ukazatele.  
  
 Celočíselný konstantní výraz s hodnotou 0 nebo takový výraz přetypovaný na typ **void** <strong>\*</strong> lze převést přetypováním, přiřazením nebo porovnáním ukazatelem libovolného typu. Tím dojde k vytvoření nulového ukazatele, který je roven jinému nulovému ukazateli stejného typu, avšak tento nulový ukazatel není roven jinému ukazateli na funkci nebo objekt. Celá čísla jiná než konstantní 0 lze převést na typ ukazatele, ale výsledek není přenosný.  
  
## <a name="see-also"></a>Viz také  
 [Převody přiřazení](../c-language/assignment-conversions.md)