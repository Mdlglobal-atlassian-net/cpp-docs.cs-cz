---
title: Typ int
ms.date: 11/04/2016
helpviewer_keywords:
- int data type
- type int
- portability [C++], type int
- signed integers
ms.assetid: 0067ce9a-281e-491a-ae63-632952981e13
ms.openlocfilehash: 6391e167ad214bb793b8d6b3b62637a113039afc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50437190"
---
# <a name="type-int"></a>Typ int

Velikost položky typu `int` se znaménkem nebo bez něj je standardní velikostí celého čísla na daném počítači. Například v 16bitových operačních systémech má typ `int` obvykle 16 bitů, tedy 2 bajty. Ve 32bitových operačních systémech má typ `int` obvykle 32 bitů, tedy 4 bajty. Proto `int` je ekvivalentem typu `short int` nebo **long int** typ a `unsigned int` je ekvivalentem typu **unsigned short** nebo `unsigned long` typ, v závislosti na cílové prostředí. Všechny typy `int` představují hodnoty se znaménkem, není-li zadáno jinak.

Specifikátory typu `int` a `unsigned int` (nebo jednoduše `unsigned`) definují určité funkce jazyka C (například typ `enum`). V těchto případech určují skutečnou velikost úložiště definice typu `int` a unsigned int pro danou implementaci.

**Specifické pro Microsoft**

Celá čísla se znaménkem jsou reprezentována ve tvaru dvojkového doplňku. Nejvýznamnější bit uchovává znaménko: 1 pro záporné, 0 pro kladné a nulu. Rozsah hodnot je uveden v [omezení typu Integer jazyka C++](../c-language/cpp-integer-limits.md), které je převzato ze omezení. Soubor hlaviček H.

**Specifické pro END Microsoft**

> [!NOTE]
>  Specifikátory typu int a unsigned int se v programech jazyka C hojně používají, protože umožňují konkrétnímu počítači zpracovat celočíselné hodnoty způsobem pro daný počítač nejefektivnějším. Jelikož se však velikosti typů int a unsigned int liší, programy, které závisí na konkrétní velikosti celého čísla, mohou být nepřenositelné na jiné počítače. Chcete-li zajistit větší přenositelnost programů, můžete použít výrazy s operátorem sizeof (jak je popsáno v [operátor sizeof](../c-language/sizeof-operator-c.md)) namísto pevně zakódované data velikosti.

## <a name="see-also"></a>Viz také

[Úložiště základních typů](../c-language/storage-of-basic-types.md)