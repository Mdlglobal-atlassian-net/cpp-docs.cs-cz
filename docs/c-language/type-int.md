---
title: Typ int
ms.date: 11/04/2016
helpviewer_keywords:
- int data type
- type int
- portability [C++], type int
- signed integers
ms.assetid: 0067ce9a-281e-491a-ae63-632952981e13
ms.openlocfilehash: ebce276c8c4efa822601fe36652057b37e922570
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81334439"
---
# <a name="type-int"></a>Typ int

Velikost položky typu `int` se znaménkem nebo bez něj je standardní velikostí celého čísla na daném počítači. Například v 16bitových operačních systémech má typ `int` obvykle 16 bitů, tedy 2 bajty. Ve 32bitových operačních systémech má typ `int` obvykle 32 bitů, tedy 4 bajty. Proto `int` je typ ekvivalentní `short int` buď typu **Long int** , a `unsigned int` typ je ekvivalentní buď k typu **unsigned short** , nebo k `unsigned long` typu, v závislosti na cílovém prostředí. Všechny typy `int` představují hodnoty se znaménkem, není-li zadáno jinak.

Specifikátory typu `int` a `unsigned int` (nebo jednoduše `unsigned`) definují určité funkce jazyka C (například typ `enum`). V těchto případech určují skutečnou velikost úložiště definice typu `int` a unsigned int pro danou implementaci.

**Specifické pro Microsoft**

Celá čísla se znaménkem jsou reprezentována ve tvaru dvojkového doplňku. Nejvýznamnější bit uchovává znaménko: 1 pro záporné, 0 pro kladné a nulu. Rozsah hodnot je uveden v [celočíselných omezeních jazyka C a C++](../c-language/cpp-integer-limits.md), které jsou přijímány z omezení. Soubor hlaviček H

**Specifické pro konec Microsoftu**

> [!NOTE]
> Specifikátory typu int a unsigned int se v programech jazyka C hojně používají, protože umožňují konkrétnímu počítači zpracovat celočíselné hodnoty způsobem pro daný počítač nejefektivnějším. Jelikož se však velikosti typů int a unsigned int liší, programy, které závisí na konkrétní velikosti celého čísla, mohou být nepřenositelné na jiné počítače. Aby byly programy lépe přenosné, můžete použít výrazy s operátorem sizeof (jak je popsáno v [operátoru sizeof](../c-language/sizeof-operator-c.md)) namísto pevně kódovaných velikostí dat.

## <a name="see-also"></a>Viz také

[Úložiště základních typů](../c-language/storage-of-basic-types.md)
