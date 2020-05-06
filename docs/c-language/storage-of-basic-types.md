---
title: Úložiště základních typů
ms.date: 10/02/2019
helpviewer_keywords:
- specifiers [C++], type
- integral types, storage
- storage [C++], types
- floating-point numbers, storage
- type specifiers [C++], sizes
- arithmetic operations [C++], types
- int data type
- short data type
- signed types [C++], storage
- long double keyword [C], storage
- long keyword [C]
- double data type, storage
- types [C], arithmetic
- integral types
- data types [C], specifiers
- storing types [C++]
- unsigned types [C++], storage
- data types [C], storage
ms.assetid: bd1f33c1-c6b9-4558-8a72-afb21aef3318
ms.openlocfilehash: 64c642df4dd85e4aa09f90a143b8aa67c28b7dc2
ms.sourcegitcommit: c51b2c665849479fa995bc3323a22ebe79d9d7ce
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "71998762"
---
# <a name="storage-of-basic-types"></a>Úložiště základních typů

Následující tabulka shrnuje úložiště přidružená ke každému základnímu typu.

## <a name="sizes-of-fundamental-types"></a>Velikosti základních typů

|Typ|Storage|
|----------|-------------|
|**char**, **unsigned char**, **signed char**|1 bajt|
|**krátký**, **unsigned short**|2 bajty|
|**int**, **unsigned int**|4 bajty|
|**Long**, **bez znaménka**|4 bajty|
|**Long Long**, **bez znaménka Long Long**|8 bajtů|
|**Plovák**|4 bajty|
|**double**|8 bajtů|
|**Long Double**|8 bajtů|

Datové typy jazyka C spadají do hlavních kategorií. *Integrální typy* zahrnují **int**, **char**, **short**, **Long**a **Long Long**. Tyto typy mohou být kvalifikovány **se znaménkem nebo** **bez**znaménka **a samotné samotný podpis lze** použít jako zkratku pro **unsigned int**. Výčtové typy (**Enum**) jsou také považovány za integrální typy pro většinu účelů. *Typy s plovoucí desetinnou* čárkou zahrnují **float**, **Double**a **Long Double**. *Aritmetické typy* zahrnují všechny plovoucí a integrální typy.

## <a name="see-also"></a>Viz také

[Deklarace a typy](../c-language/declarations-and-types.md)
