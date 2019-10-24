---
title: Typ int
ms.date: 11/04/2016
helpviewer_keywords:
- int data type
- type int
- portability [C++], type int
- signed integers
ms.assetid: 0067ce9a-281e-491a-ae63-632952981e13
ms.openlocfilehash: c69d2308abe2ee3d7e6b392f5a9e78a004791501
ms.sourcegitcommit: ea9d78dbb93bf3f8841dde93dbc12bd66f6f32ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72778363"
---
# <a name="type-int"></a>Typ int

Velikost položky typu `int` se znaménkem nebo bez něj je standardní velikostí celého čísla na daném počítači. Například v 16bitových operačních systémech má typ `int` obvykle 16 bitů, tedy 2 bajty. Ve 32bitových operačních systémech má typ `int` obvykle 32 bitů, tedy 4 bajty. Proto je typ `int` ekvivalentní `short int` nebo typu **Long int** a typ `unsigned int` je ekvivalentem typu **unsigned short** nebo `unsigned long`, v závislosti na cílovém prostředí. Všechny typy `int` představují hodnoty se znaménkem, není-li zadáno jinak.

Specifikátory typu `int` a `unsigned int` (nebo jednoduše `unsigned`) definují určité funkce jazyka C (například typ `enum`). V těchto případech určují skutečnou velikost úložiště definice typu `int` a unsigned int pro danou implementaci.

**Specifické pro společnost Microsoft**

Celá čísla se znaménkem jsou reprezentována ve tvaru dvojkového doplňku. Nejvýznamnější bit uchovává znaménko: 1 pro záporné, 0 pro kladné a nulu. Rozsah hodnot je uveden v [omezeních jazyka C C++ a celých čísel](../c-language/cpp-integer-limits.md), která je přijímána z omezení. Soubor hlaviček H

**Specifické pro konec Microsoftu**

> [!NOTE]
>  Specifikátory typu int a unsigned int se v programech jazyka C hojně používají, protože umožňují konkrétnímu počítači zpracovat celočíselné hodnoty způsobem pro daný počítač nejefektivnějším. Jelikož se však velikosti typů int a unsigned int liší, programy, které závisí na konkrétní velikosti celého čísla, mohou být nepřenositelné na jiné počítače. Aby byly programy lépe přenosné, můžete použít výrazy s operátorem sizeof (jak je popsáno v [operátoru sizeof](../c-language/sizeof-operator-c.md)) namísto pevně kódovaných velikostí dat.

## <a name="see-also"></a>Viz také:

[Úložiště základních typů](../c-language/storage-of-basic-types.md)
