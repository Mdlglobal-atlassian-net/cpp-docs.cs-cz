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
ms.openlocfilehash: 29bea87e56aa90a8deab7ad7280b3fbdfb45c82b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62326897"
---
# <a name="c-additive-operators"></a>Operátory sčítání jazyka C

Operátory sčítání provedení sčítání (**+**) a odčítání (**-**).

## <a name="syntax"></a>Syntaxe

*additive-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*multiplikativní výraz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*additive-expression* **+** *multiplicative-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*additive-expression* **-** *multiplicative-expression*

> [!NOTE]
> I když syntaxe *additive-expression* zahrnuje *násobení výraz*, to nutně neznamená, že se vyžadují výrazů pomocí násobení. Zobrazit syntaxi v [souhrn syntaxe jazyka C](../c-language/c-language-syntax-summary.md), pro *násobení výraz*, *výrazem přetypování*, a *unární výraz*.

Operandy mohou být integrální hodnoty s plovoucí desetinnou čárkou. Některé operace sčítání lze také provést na hodnoty ukazatele, jak je uvedeno v části diskuzi o každý operátor.

Operátory sčítání provádět běžné aritmetické převody s plovoucí desetinnou čárkou a celočíselné operandy. Typ výsledku je typ operandu po převodu. Vzhledem k tomu, že převody prováděné operátory sčítání se neposkytuje přetečení nebo podtečení podmínky, informace mohou být ztraceny, pokud výsledek operace sčítání nelze reprezentovat v typu operandu po převodu.

## <a name="see-also"></a>Viz také:

[Operátory sčítání: + a -](../cpp/additive-operators-plus-and.md)
