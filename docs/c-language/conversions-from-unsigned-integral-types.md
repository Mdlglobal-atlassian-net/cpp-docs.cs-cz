---
title: Převody z nepodepsaných integrálních typů
ms.date: 03/27/2019
helpviewer_keywords:
- integers, converting
- type casts, involving integers
- data type conversion [C++], signed and unsigned integers
- type conversion [C++], signed and unsigned integers
- integral conversions, from unsigned
ms.assetid: 60fb7e10-bff9-4a13-8a48-e19f25a36a02
ms.openlocfilehash: 3f6136a721f84332451184baa648ebc7c909d5d7
ms.sourcegitcommit: 309dc532f13242854b47759cef846de59bb807f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/28/2019
ms.locfileid: "58565019"
---
# <a name="conversions-from-unsigned-integral-types"></a>Převody z nepodepsaných integrálních typů

Celé číslo bez znaménka je rozšířením nula převést na kratší celé číslo bez znaménka nebo podepsaný zkrácením nejvyšších bitů nebo na již bez znaménka nebo podepsané celé číslo. Další informace najdete v tématu [převody z celočíselných typů bez znaménka tabulky](#conversions-from-unsigned-integral-types-table).

Pokud hodnoty celočíselného typu převeden na celé číslo se znaménkem s menší velikostí, nebo celé číslo bez znaménka, je převedena na jeho odpovídající celé číslo se znaménkem, hodnota je beze změny, pokud můžou být vyjádřeny v novém typu. Nicméně hodnota představuje změny, pokud je bit znaménka nastavená jako v následujícím příkladu.

```C
int j;
unsigned short k = 65533;

j = k;
printf_s( "%hd\n", j );   // Prints -3
```

Pokud nemůže být reprezentovaná, výsledkem je definován implementací. Zobrazit [převody přetypování](../c-language/type-cast-conversions.md) informace o zpracování kompilátor Microsoft C degradace celých čísel. Stejné výsledky chování z převodu celého čísla nebo z typu přetypování na celé číslo.

Nepodepsané hodnoty se převedou tak, aby zachovává jejich hodnota a není reprezentovatelné přímo v jazyce C. Jedinou výjimkou je převod z **unsigned long** k **float**, který ztratí maximálně bity nižšího řádu. V opačném případě hodnota se zachová pro účely, nebo bez znaménka. Pokud hodnota typu celé číslo je převedena na číslo s plovoucí čárkou a hodnota je mimo rozsah reprezentovatelný, výsledek nedefinován. (Viz [úložiště základních typů](../c-language/storage-of-basic-types.md) informace o rozsahu u typů s plovoucí desetinnou čárkou a integrální.)

Následující tabulka shrnuje převody z nepodepsaných integrálních typů.

## <a name="conversions-from-unsigned-integral-types-table"></a>Převody z celočíselných typů bez znaménka tabulky

|From|Chcete-li|Metoda|
|----------|--------|------------|
|**unsigned char**|**char**|Zachovat bitový vzor; bit vyššího řádu stane bitu znaménka|
|**unsigned char**|**short**|Rozšíření nula|
|**unsigned char**|**long**|Rozšíření nula|
|**unsigned char**|**short bez znaménka**|Rozšíření nula|
|**unsigned char**|**unsigned long**|Rozšíření nula|
|**unsigned char**|**float**|Převést na **dlouhé**; převod **dlouhé** k **plovoucí desetinnou čárkou**|
|**unsigned char**|**double**|Převést na **dlouhé**; převod **dlouhé** k **double**|
|**unsigned char**|**typ long double**|Převést na **dlouhé**; převod **dlouhé** k **double**|
|**short bez znaménka**|**char**|Zachovat dolní bajty.|
|**short bez znaménka**|**short**|Zachovat bitový vzor; bit vyššího řádu stane bitu znaménka|
|**short bez znaménka**|**long**|Rozšíření nula|
|**short bez znaménka**|**unsigned char**|Zachovat dolní bajty.|
|**short bez znaménka**|**unsigned long**|Rozšíření nula|
|**short bez znaménka**|**float**|Převést na **dlouhé**; převod **dlouhé** k **plovoucí desetinnou čárkou**|
|**short bez znaménka**|**double**|Převést na **dlouhé**; převod **dlouhé** k **double**|
|**short bez znaménka**|**typ long double**|Převést na **dlouhé**; převod **dlouhé** k **double**|
|**unsigned long**|**char**|Zachovat dolní bajty.|
|**unsigned long**|**short**|Zachovat nižší řád slova|
|**unsigned long**|**long**|Zachovat bitový vzor; bit vyššího řádu stane bitu znaménka|
|**unsigned long**|**unsigned char**|Zachovat dolní bajty.|
|**unsigned long**|**short bez znaménka**|Zachovat nižší řád slova|
|**unsigned long**|**float**|Převést na **dlouhé**; převod **dlouhé** k **plovoucí desetinnou čárkou**|
|**unsigned long**|**double**|Převést přímo na **double**|
|**unsigned long**|**typ long double**|Převést na **dlouhé**; převod **dlouhé** k **double**|

**Microsoft Specific**

Kompilátor Microsoft C **unsigned int** je ekvivalentem typu **unsigned long** typu. Převod **unsigned int** hodnotu pokračuje stejným způsobem jako převod **unsigned long**. Převody z **unsigned long** hodnoty **float** nejsou přesné, pokud je převáděná hodnota větší než maximální pozitivní podepsané **dlouhé** hodnotu.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Převody přiřazení](../c-language/assignment-conversions.md)
