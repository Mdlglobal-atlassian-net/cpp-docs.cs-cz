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

Aditivní operátory provádějí sčítání (**+**) a odčítání (**-**).

## <a name="syntax"></a>Syntaxe

*výraz doplňkového výrazu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*multiplikativní – výraz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;výraz *doplňkového výrazu* **+** *multiplikativní-Expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;výraz *doplňkového výrazu* **-** *multiplikativní-Expression*

> [!NOTE]
> I když syntaxe *doplňkového výrazu* zahrnuje *multiplikativní-Expression*, neznamená to, že se vyžadují výrazy, které používají násobení. Podívejte se na syntaxi v [souhrnu syntaxe jazyka C](../c-language/c-language-syntax-summary.md)pro *multiplikativní-Expression*, *cast-expression*a *unární-Expression*.

Operandy mohou být celočíselné nebo plovoucí hodnoty. Některé operace s doplňkovou operací lze také provést na hodnotách ukazatele, jak je uvedeno pod diskusí každého operátoru.

Přídavné operátory provádějí obvyklé aritmetické převody na celočíselných a plovoucích operandech. Typ výsledku je typ operandů po převodu. Vzhledem k tomu, že převody prováděné pomocí operátorů sčítání neposkytují podmínky přetečení nebo podtečení, mohou být informace ztraceny, pokud výsledek operace sčítání nelze reprezentovat v typu operandů po převodu.

## <a name="see-also"></a>Viz také

[Operátory sčítání: + a-](../cpp/additive-operators-plus-and.md)
