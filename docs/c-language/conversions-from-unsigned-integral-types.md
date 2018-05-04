---
title: Převody z nepodepsaných integrálních typů | Microsoft Docs
ms.custom: ''
ms.date: 01/29/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- integers, converting
- type casts, involving integers
- data type conversion [C++], signed and unsigned integers
- type conversion [C++], signed and unsigned integers
- integral conversions, from unsigned
ms.assetid: 60fb7e10-bff9-4a13-8a48-e19f25a36a02
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6a8a77e898feb6676487c557b8e96d54dc793ace
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="conversions-from-unsigned-integral-types"></a>Převody z nepodepsaných integrálních typů

Celé číslo bez znaménka jsou převedeny na kratší číslo bez znaménka nebo podepsaný zkrácením nejvyšších bitů, nebo již nepodepsaný nebo podepsaný celočíselná a tím, že rozšíří nula (viz [převody z nepodepsaných integrálních typů](#_clang_table_4..3) tabulky).

Pokud hodnotu s integrální typ převeden na znaménkem s menší velikostí, nebo celé číslo bez znaménka jsou převedeny na jeho odpovídající číslo se znaménkem, hodnota je beze změny, pokud může být reprezentován v nového typu. Ale hodnota představuje změny, pokud je bit přihlašovací nastavený, jako v následujícím příkladu.

```C
int j;
unsigned short k = 65533;

j = k;
printf_s( "%hd\n", j );   // Prints -3
```

Pokud není možné vyjádřit, výsledkem je, definované implementací. V tématu [převody přetypování](../c-language/type-cast-conversions.md) informace o zpracování kompilátoru Microsoft C degradace celých čísel. Stejné výsledky chování z převod celé číslo nebo přetypování na celé číslo.

Nepodepsané hodnoty se převedou způsobem, který zachovává jejich hodnota a není reprezentovat přímo C. Jedinou výjimkou je převod z **nepodepsané dlouho** k **float**, který ztratí maximálně nejnižší bits. Jinak je zachovaná hodnotu, podepsaný držitelem nebo bez znaménka. Pokud se hodnota typu integrální jsou převedeny na plovoucí a hodnota je mimo rozsah reprezentovat, výsledkem je definovaný. (Viz [úložiště základních typů](../c-language/storage-of-basic-types.md) informace o rozsahu pro typy s plovoucí desetinnou čárkou a integrální.)

Následující tabulka shrnuje převody z nepodepsaných integrálních typů.

## <a name="conversions-from-unsigned-integral-types"></a>Převody z nepodepsaných integrálních typů

|From|Chcete-li|Metoda|
|----------|--------|------------|
|**unsigned char**|**char**|Zachovat bitový; bit horní stane přihlašovací bit|
|**unsigned char**|**short**|Rozšíření nula.|
|**unsigned char**|**long**|Rozšíření nula.|
|**unsigned char**|**short bez znaménka**|Rozšíření nula.|
|**unsigned char**|**dlouho bez znaménka**|Rozšíření nula.|
|**unsigned char**|**float**|Převést na **dlouho**; převést **dlouho** k **float**|
|**unsigned char**|**double**|Převést na **dlouho**; převést **dlouho** k **double**|
|**unsigned char**|**dlouhé double**|Převést na **dlouho**; převést **dlouho** k **double**|
|**short bez znaménka**|**char**|Zachovat nejnižší bajtů|
|**short bez znaménka**|**short**|Zachovat bitový; bit horní stane přihlašovací bit|
|**short bez znaménka**|**long**|Rozšíření nula.|
|**short bez znaménka**|**unsigned char**|Zachovat nejnižší bajtů|
|**short bez znaménka**|**dlouho bez znaménka**|Rozšíření nula.|
|**short bez znaménka**|**float**|Převést na **dlouho**; převést **dlouho** k **float**|
|**short bez znaménka**|**double**|Převést na **dlouho**; převést **dlouho** k **double**|
|**short bez znaménka**|**dlouhé double**|Převést na **dlouho**; převést **dlouho** k **double**|
|**dlouho bez znaménka**|**char**|Zachovat nejnižší bajtů|
|**dlouho bez znaménka**|**short**|Zachovat nejnižší aplikace word|
|**dlouho bez znaménka**|**long**|Zachovat bitový; bit horní stane přihlašovací bit|
|**dlouho bez znaménka**|**unsigned char**|Zachovat nejnižší bajtů|
|**dlouho bez znaménka**|**short bez znaménka**|Zachovat nejnižší aplikace word|
|**dlouho bez znaménka**|**float**|Převést na **dlouho**; převést **dlouho** k **float**|
|**dlouho bez znaménka**|**double**|Převést přímo na **double**|
|**dlouho bez znaménka**|**dlouhé double**|Převést na **dlouho**; převést **dlouho** k **double**|

**Konkrétní Microsoft**

Pro kompilátor Microsoft C **nepodepsané int** typ je ekvivalentní **nepodepsané dlouho** typu. Převod **nepodepsané int** hodnotu pokračuje stejným způsobem jako převod **nepodepsané dlouho**. Převody z **nepodepsané dlouho** hodnoty k **float** nejsou přesné, pokud je hodnota převáděné větší než maximální kladnou podepsané **dlouho** hodnotu.

**Konkrétní Microsoft END**

## <a name="see-also"></a>Viz také

[Převody přiřazení](../c-language/assignment-conversions.md)  
