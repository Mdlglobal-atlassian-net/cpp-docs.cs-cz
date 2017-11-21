---
title: "Převod na a z typů ukazatele | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- pointers, converting
- conversions, pointer
- type casts, involving pointers
- void pointers
ms.assetid: 3facc56f-06d3-4570-b1a2-7d4927b83086
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1751c19ba222bbdf9dfc30a290201289db1af850
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
  
-   Pokud je velikost integrální typu liší od velikost je ukazatel typu, integrální typ nejprve převeden na velikost ukazatele, pomocí cesty převod uvedených v tabulkách [převod z podepsané integrálních typů](../c-language/conversions-from-signed-integral-types.md) a [ Převod z nepodepsaných integrálních typů](../c-language/conversions-from-unsigned-integral-types.md). Poté je považován za hodnotu ukazatele.  
  
 Celočíselné konstantní výraz s hodnotou 0 nebo takový výraz přetypovat na typ **void \***  lze převést typ přetypování pomocí přiřazení nebo porovnání se ukazatel libovolného typu. Tím dojde k vytvoření nulového ukazatele, který je roven jinému nulovému ukazateli stejného typu, avšak tento nulový ukazatel není roven jinému ukazateli na funkci nebo objekt. Celá čísla jiná než konstantní 0 lze převést na typ ukazatele, ale výsledek není přenosný.  
  
## <a name="see-also"></a>Viz také  
 [Převody přiřazení](../c-language/assignment-conversions.md)