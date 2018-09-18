---
title: Úložiště základních typů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 14c8483671e806adb9170429f2e17d4487de0cfd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46090487"
---
# <a name="storage-of-basic-types"></a>Úložiště základních typů

Následující tabulka shrnuje úložiště přidružená ke každému základnímu typu.

### <a name="sizes-of-fundamental-types"></a>Velikosti základních typů

|Typ|Úložiště|
|----------|-------------|
|`char`, `unsigned char`, **podepsané char**|1 bajt|
|**krátký**, **unsigned short**|2 bajty|
|`int`, `unsigned int`|4 bajty|
|**dlouhé**, `unsigned long`|4 bajty|
|**float**|4 bajty|
|**double**|8 bajtů|
|`long double`|8 bajtů|

Datové typy jazyka C spadají do hlavních kategorií. "Celočíselné typy" zahrnují `char`, `int`, **krátký**, **dlouhé**, **podepsané**, `unsigned`, a `enum`. "Typy s plovoucí desetinnou čárkou" zahrnují **float**, **double**, a `long double`. „Aritmetické typy“ zahrnují všechny typy s plovoucí desetinnou čárkou a celočíselné typy.

## <a name="see-also"></a>Viz také

[Deklarace a typy](../c-language/declarations-and-types.md)