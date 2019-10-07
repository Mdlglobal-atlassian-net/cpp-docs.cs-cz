---
title: Převody z integrálních typů se znaménkem
ms.date: 10/02/2019
helpviewer_keywords:
- integral conversions, from signed
- integers, converting
- conversions [C++], integral
- data type conversion [C++], signed and unsigned integers
- type conversion [C++], signed and unsigned integers
ms.assetid: 5eea32f8-8b14-413d-acac-c063b3d118d7
ms.openlocfilehash: 79608b5ca4335ee3c30bdab27e7efade5b7e2f54
ms.sourcegitcommit: c51b2c665849479fa995bc3323a22ebe79d9d7ce
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "71998719"
---
# <a name="conversions-from-signed-integral-types"></a>Převody z integrálních typů se znaménkem

Při převodu celého čísla se znaménkem na celé číslo nebo na typ s plovoucí desetinnou čárkou, pokud je původní hodnota reprezentována v typu výsledku, hodnota je beze změny.

Když je celé číslo se znaménkem převedeno na celé číslo větší velikosti, hodnota je znaménko-Extended. Při převodu na celé číslo menší velikosti jsou bity vysokého řádu zkráceny. Výsledek je interpretován pomocí typu výsledku, jak je znázorněno v následujícím příkladu:

```C
int i = -3;
unsigned short u;

u = i;
printf_s( "%hu\n", u );  // Prints 65533
```

Při převodu celého čísla se znaménkem na typ s plovoucí desetinnou čárkou, pokud původní hodnota není reprezentována přesně v typu výsledku, je výsledkem následující vyšší nebo nižší reprezentovatelné hodnoty.

Informace o velikosti integrálních a plovoucích bodů naleznete v tématu [Storage of Basic Types](../c-language/storage-of-basic-types.md).

Následující tabulka shrnuje převody z podepsaných integrálních typů. Předpokládá, že typ **znaku** je ve výchozím nastavení podepsaný. Použijete-li možnost v době kompilace ke změně výchozí hodnoty typu **char** na hodnotu unsigned, místo převodů v této tabulce se použije převod uvedený v tabulce [nepodepsaných integrálních typů](../c-language/conversions-from-unsigned-integral-types.md) pro typ **znaku bez znaménka** .

**Specifické pro společnost Microsoft**

V kompilátoru společnosti Microsoft jsou hodnoty **int** a **Long** jedinečné, ale ekvivalentní typy. Převod hodnoty typu **int** pokračuje stejným způsobem jako převod **dlouhého**typu.

**Specifické pro konec Microsoftu**

## <a name="table-of-conversions-from-signed-integral-types"></a>Tabulka převodů z celočíselných typů se znaménkem

|From|Chcete-li|Metoda|
|----------|--------|------------|
|**znak**<sup>1</sup>|**short**|Znaménko – rozšiřování|
|**char**|**long**|Znaménko – rozšiřování|
|**char**|**Long Long**|Znaménko – rozšiřování|
|**char**|**znak bez znaménka**|Zachovat vzor; bit vysokého řádu ztratí funkci jako bit znaménka.|
|**char**|**krátký unsigned**|Znaménko – zvětšit na **krátké**; převod **krátkých** na **unsigned short**|
|**char**|**unsigned long**|Znaménko – prodloužit na **dlouhou dobu**; převod **Long** na **unsigned long**|
|**char**|**dlouhý unsigned long**|Znaménko – prodloužit na **dlouhou**dobu; převod **dlouhého** dlouhého na **unsigned long long**|
|**char**|**float**|Znaménko – prodloužit na **dlouhou dobu**; převést **Long** na **float**|
|**char**|**double**|Znaménko – prodloužit na **dlouhou dobu**; převést **Long** na **Double**|
|**char**|**Long Double**|Znaménko – prodloužit na **dlouhou dobu**; převést **Long** na **Double**|
|**short**|**char**|Zachovat bajty s nižším pořadím|
|**short**|**long**|Znaménko – rozšiřování|
|**short**|**Long Long**|Znaménko – rozšiřování|
|**short**|**znak bez znaménka**|Zachovat bajty s nižším pořadím|
|**short**|**krátký unsigned**|Zachovat bitový vzor; bit vysokého řádu ztratí funkci jako bit znaménka.|
|**short**|**unsigned long**|Znaménko – prodloužit na **dlouhou dobu**; převod **Long** na **unsigned long**|
|**short**|**dlouhý unsigned long**|Znaménko – prodloužit na **dlouhou**dobu; převod **dlouhého** dlouhého na **unsigned long long**|
|**short**|**float**|Znaménko – prodloužit na **dlouhou dobu**; převést **Long** na **float**|
|**short**|**double**|Znaménko – prodloužit na **dlouhou dobu**; převést **Long** na **Double**|
|**short**|**Long Double**|Znaménko – prodloužit na **dlouhou dobu**; převést **Long** na **Double**|
|**long**|**char**|Zachovat bajty s nižším pořadím|
|**long**|**short**|Zachovat slovo s nižším pořadím|
|**long**|**Long Long**|Znaménko – rozšiřování|
|**long**|**znak bez znaménka**|Zachovat bajty s nižším pořadím|
|**long**|**krátký unsigned**|Zachovat slovo s nižším pořadím|
|**long**|**unsigned long**|Zachovat bitový vzor; bit vysokého řádu ztratí funkci jako bit znaménka.|
|**long**|**dlouhý unsigned long**|Znaménko – prodloužit na **dlouhou**dobu; převod **dlouhého** dlouhého na **unsigned long long**|
|**long**|**float**|Představuje typ **float**. Pokud se **Long** nemůže přesně reprezentovat, dojde ke ztrátě přesnosti.|
|**long**|**double**|Představuje **typ Double**. Pokud **Long** nemůže být reprezentován přesně jako **Dvojitá**přesnost, dojde ke ztrátě určité přesnosti.|
|**long**|**Long Double**|Představuje **typ Double**. Pokud **Long** nemůže být reprezentován přesně jako **Dvojitá**přesnost, dojde ke ztrátě určité přesnosti.|
|**Long Long**|**char**|Zachovat bajty s nižším pořadím|
|**Long Long**|**short**|Zachovat slovo s nižším pořadím|
|**Long Long**|**long**|Zachovat hodnotu DWORD s nižším pořadím|
|**Long Long**|**znak bez znaménka**|Zachovat bajty s nižším pořadím|
|**Long Long**|**krátký unsigned**|Zachovat slovo s nižším pořadím|
|**Long Long**|**unsigned long**|Zachovat hodnotu DWORD s nižším pořadím|
|**Long Long**|**dlouhý unsigned long**|Zachovat bitový vzor; bit vysokého řádu ztratí funkci jako bit znaménka.|
|**Long Long**|**float**|Představuje typ **float**. Pokud se **Long Long** nemůže přesně reprezentovat, dojde ke ztrátě přesnosti.|
|**Long Long**|**double**|Představuje **typ Double**. Pokud **Long Long** nemůže být reprezentován přesně jako **Dvojitá**přesnost, dojde ke ztrátě určité přesnosti.|
|**Long Long**|**Long Double**|Představuje **typ Double**. Pokud **Long Long** nemůže být reprezentován přesně jako **Dvojitá**přesnost, dojde ke ztrátě určité přesnosti.|

<sup>1</sup> všechny položky typu **char** předpokládají, že typ **znaku** je ve výchozím nastavení podepsán.

## <a name="see-also"></a>Viz také:

[Převody přiřazení](../c-language/assignment-conversions.md)
