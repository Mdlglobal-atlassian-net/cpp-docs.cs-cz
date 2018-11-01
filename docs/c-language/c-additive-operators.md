---
title: Operátory sčítání jazyka C
ms.date: 10/18/2018
helpviewer_keywords:
- usual arithmetic conversions
- operators [C], addition
- + operator, additive operators
- additive operators
- arithmetic operators [C++], additive operators
ms.assetid: bb8ac205-b061-41fc-8dd4-dab87c8b900c
ms.openlocfilehash: af7302adaafc3a91287f6d15a11c8e784f35c33d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50650672"
---
# <a name="c-additive-operators"></a>Operátory sčítání jazyka C

Operátory sčítání provedení sčítání (**+**) a odčítání (**-**).

## <a name="syntax"></a>Syntaxe

*Additive-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*multiplikativní výraz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Additive-expression* **+** *násobení výraz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Additive-expression* **-** *násobení výraz*

> [!NOTE]
> I když syntaxe *additive-expression* zahrnuje *násobení výraz*, to nutně neznamená, že se vyžadují výrazů pomocí násobení. Zobrazit syntaxi v [souhrn syntaxe jazyka C](../c-language/c-language-syntax-summary.md), pro *násobení výraz*, *výrazem přetypování*, a *unární výraz*.

Operandy mohou být integrální hodnoty s plovoucí desetinnou čárkou. Některé operace sčítání lze také provést na hodnoty ukazatele, jak je uvedeno v části diskuzi o každý operátor.

Operátory sčítání provádět běžné aritmetické převody s plovoucí desetinnou čárkou a celočíselné operandy. Typ výsledku je typ operandu po převodu. Vzhledem k tomu, že převody prováděné operátory sčítání se neposkytuje přetečení nebo podtečení podmínky, informace mohou být ztraceny, pokud výsledek operace sčítání nelze reprezentovat v typu operandu po převodu.

## <a name="see-also"></a>Viz také

[Operátory sčítání: + a -](../cpp/additive-operators-plus-and.md)