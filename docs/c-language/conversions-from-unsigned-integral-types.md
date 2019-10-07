---
title: Převody z integrálních typů bez znaménka
ms.date: 10/02/2019
helpviewer_keywords:
- integers, converting
- type casts, involving integers
- data type conversion [C++], signed and unsigned integers
- type conversion [C++], signed and unsigned integers
- integral conversions, from unsigned
ms.assetid: 60fb7e10-bff9-4a13-8a48-e19f25a36a02
ms.openlocfilehash: 3099f0113103223e392dc20560899b4a6e3ebf20
ms.sourcegitcommit: c51b2c665849479fa995bc3323a22ebe79d9d7ce
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "71998785"
---
# <a name="conversions-from-unsigned-integral-types"></a>Převody z integrálních typů bez znaménka

Pokud je unsigned integer převeden na celé číslo nebo na typ s plovoucí desetinnou čárkou, pokud je původní hodnota reprezentována v typu výsledku, hodnota je beze změny.

Při převodu unsigned integer na celé číslo větší velikosti je hodnota nulová – rozšířená. Při převodu na celé číslo menší velikosti jsou bity vysokého řádu zkráceny. Výsledek je interpretován pomocí typu výsledku, jak je znázorněno v tomto příkladu.

```C
unsigned k = 65533;
short j;

j = k;
printf_s( "%hd\n", j );   // Prints -3
```

Při převodu unsigned integer na typ s plovoucí desetinnou čárkou, pokud původní hodnota nemůže být reprezentována přesně v typu výsledku, výsledek je další nebo nižší reprezentovatelné číslo.

Informace o velikostech typů integrálních a plovoucích bodů naleznete v části [úložiště základních typů](../c-language/storage-of-basic-types.md) .

**Specifické pro společnost Microsoft**

V kompilátoru společnosti Microsoft, **unsigned** (nebo **unsigned int**) a **Long bez znaménka** jsou odlišné, ale ekvivalentní typy. Převod hodnoty typu **int bez znaménka** pokračuje stejným způsobem jako převod typu **Long bez znaménka**.

**Specifické pro konec Microsoftu**

Následující tabulka shrnuje převody z celočíselných typů bez znaménka.

## <a name="table-of-conversions-from-unsigned-integral-types"></a>Tabulka převodů z celočíselných typů bez znaménka

|From|Chcete-li|Metoda|
|----------|--------|------------|
|**znak bez znaménka**|**char**|Zachovat bitový vzor; bit vysokého řádu se změní na bit znaménka.|
|**znak bez znaménka**|**short**|Nulová – rozšiřování|
|**znak bez znaménka**|**long**|Nulová – rozšiřování|
|**znak bez znaménka**|**Long Long**|Nulová – rozšiřování|
|**znak bez znaménka**|**krátký unsigned**|Nulová – rozšiřování|
|**znak bez znaménka**|**unsigned long**|Nulová – rozšiřování|
|**znak bez znaménka**|**dlouhý unsigned long**|Nulová – rozšiřování|
|**znak bez znaménka**|**float**|Převést na **Long**; převést **Long** na **float**|
|**znak bez znaménka**|**double**|Převést na **Long**; převést **Long** na **Double**|
|**znak bez znaménka**|**Long Double**|Převést na **Long**; převést **Long** na **Double**|
|**krátký unsigned**|**char**|Zachovat bajty s nižším pořadím|
|**krátký unsigned**|**short**|Zachovat bitový vzor; bit vysokého řádu se změní na bit znaménka.|
|**krátký unsigned**|**long**|Nulová – rozšiřování|
|**krátký unsigned**|**Long Long**|Nulová – rozšiřování|
|**krátký unsigned**|**znak bez znaménka**|Zachovat bajty s nižším pořadím|
|**krátký unsigned**|**unsigned long**|Nulová – rozšiřování|
|**krátký unsigned**|**dlouhý unsigned long**|Nulová – rozšiřování|
|**krátký unsigned**|**float**|Převést na **Long**; převést **Long** na **float**|
|**krátký unsigned**|**double**|Převést na **Long**; převést **Long** na **Double**|
|**krátký unsigned**|**Long Double**|Převést na **Long**; převést **Long** na **Double**|
|**unsigned long**|**char**|Zachovat bajty s nižším pořadím|
|**unsigned long**|**short**|Zachovat slovo s nižším pořadím|
|**unsigned long**|**long**|Zachovat bitový vzor; bit vysokého řádu se změní na bit znaménka.|
|**unsigned long**|**Long Long**|Nulová – rozšiřování|
|**unsigned long**|**znak bez znaménka**|Zachovat bajty s nižším pořadím|
|**unsigned long**|**krátký unsigned**|Zachovat slovo s nižším pořadím|
|**unsigned long**|**dlouhý unsigned long**|Nulová – rozšiřování|
|**unsigned long**|**float**|Převést na **Long**; převést **Long** na **float**|
|**unsigned long**|**double**|Převést přímo na **dvojitou přesnost**|
|**unsigned long**|**Long Double**|Převést na **Long**; převést **Long** na **Double**|
|**dlouhý unsigned long**|**char**|Zachovat bajty s nižším pořadím|
|**dlouhý unsigned long**|**short**|Zachovat slovo s nižším pořadím|
|**dlouhý unsigned long**|**long**|Zachovat hodnotu DWORD s nižším pořadím|
|**dlouhý unsigned long**|**Long Long**|Zachovat bitový vzor; bit vysokého řádu se změní na bit znaménka.|
|**dlouhý unsigned long**|**znak bez znaménka**|Zachovat bajty s nižším pořadím|
|**dlouhý unsigned long**|**krátký unsigned**|Zachovat slovo s nižším pořadím|
|**dlouhý unsigned long**|**unsigned long**|Zachovat hodnotu DWORD s nižším pořadím|
|**dlouhý unsigned long**|**float**|Převést na **Long**; převést **Long** na **float**|
|**dlouhý unsigned long**|**double**|Převést přímo na **dvojitou přesnost**|
|**dlouhý unsigned long**|**Long Double**|Převést na **Long**; převést **Long** na **Double**|

## <a name="see-also"></a>Viz také:

[Převody přiřazení](../c-language/assignment-conversions.md)
