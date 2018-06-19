---
title: Převody z typů s plovoucí desetinnou čárkou | Microsoft Docs
ms.custom: ''
ms.date: 01/29/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- converting floating point
- floating-point conversion
ms.assetid: 96804c8e-fa3b-4742-9006-0082ed9e57f2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ce86a9ceffaa5d9dacfe56e6b89b677b3abb1517
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32392481"
---
# <a name="conversions-from-floating-point-types"></a>Převody z typů s plovoucí desetinnou čárkou

A **float** převést na hodnotu **dvojité** nebo **long double**, nebo **dvojité** převést na **dlouho dvakrát**, zde nevyskytlo žádná změna v poli hodnota. A **dvojité** převést na hodnotu **float** hodnota je reprezentována přesně, pokud je to možné. Přesnost může dojít ke ztrátě, pokud hodnota není možné vyjádřit přesně. Pokud je výsledek mimo rozsah, chování nedefinovaný. V tématu [omezení Floating-Point konstanty](../c-language/limits-on-floating-point-constants.md) pro rozsah typů s plovoucí desetinnou čárkou.

Je převést hodnotu plovoucí celočíselné hodnoty podle první převod na **dlouho**, pak z **dlouho** hodnotu s konkrétní hodnotou integrální. Za desetinnou hodnotu s plovoucí se zahodí v převod na **dlouho**. Pokud je stále výsledek příliš velký pro uložení do **dlouho**, výsledek převodu není definován.

**Konkrétní Microsoft**

Při převodu **dvojité** nebo **long double** číslo s plovoucí desetinnou čárkou menší na dvě desetinná čísla, hodnota proměnné s plovoucí desetinnou čárkou se zkrátí směrem k nule, když dojde podtečení. Přetečení způsobí, že chyba spuštění. Všimněte si, že mapuje kompilátoru Microsoft C **long double** na typ **dvojité**.

**Konkrétní Microsoft END**

Následující tabulka shrnuje převody z typů s plovoucí čárkou.

## <a name="conversions-from-floating-point-types"></a>Převody z typů s plovoucí desetinnou čárkou

|From|Chcete-li|Metoda|
|----------|--------|------------|
|**float**|**char**|Převést na **dlouho**; převést **dlouho** k **char**|
|**float**|**short**|Převést na **dlouho**; převést **dlouho** k **krátké**|
|**float**|**long**|Zkraťte na desetinné čárky. Pokud je výsledek příliš velký a nelze je jako **dlouho**, výsledkem nedefinovaný.|
|**float**|**short bez znaménka**|Převést na **dlouho**; převést **dlouho** k **prostě bez znaménka**|
|**float**|**dlouho bez znaménka**|Převést na **dlouho**; převést **dlouho** k **dlouho bez znaménka**|
|**float**|**double**|Změnit interního vyjádření|
|**float**|**dlouhé double**|Změnit interního vyjádření|
|**double**|**char**|Převést na **float**; převést **float** k **char**|
|**double**|**short**|Převést na **float**; převést **float** k **krátké**|
|**double**|**long**|Zkraťte na desetinné čárky. Pokud je výsledek příliš velký a nelze je jako **dlouho**, výsledkem nedefinovaný.|
|**double**|**short bez znaménka**|Převést na **dlouho**; převést **dlouho** k **prostě bez znaménka**|
|**double**|**dlouho bez znaménka**|Převést na **dlouho**; převést **dlouho** k **dlouho bez znaménka**|
|**double**|**float**|Představují jako **float**. Pokud **dvojité** hodnotu nelze reprezentovat přesně tak, jak **float**, dojde ke ztrátě přesnosti. Pokud hodnota je příliš velký a nelze je jako **float**, výsledkem nedefinovaný.|
|**dlouhé double**|**char**|Převést na **float**; převést **float** k **char**|
|**dlouhé double**|**short**|Převést na **float**; převést **float** k **krátké**|
|**dlouhé double**|**long**|Zkraťte na desetinné čárky. Pokud je výsledek příliš velký a nelze je jako **dlouho**, výsledkem nedefinovaný.|
|**dlouhé double**|**short bez znaménka**|Převést na **dlouho**; převést **dlouho** k **prostě bez znaménka**|
|**dlouhé double**|**dlouho bez znaménka**|Převést na **dlouho**; převést **dlouho** k **dlouho bez znaménka**|
|**dlouhé double**|**float**|Představují jako **float**. Pokud **dvojité** hodnotu nelze reprezentovat přesně tak, jak **float**, dojde ke ztrátě přesnosti. Pokud hodnota je příliš velký a nelze je jako **float**, výsledkem nedefinovaný.|
|**dlouhé double**|**double**|**Long double** hodnota je považována za **dvojité**.|

Převody z **float**, **dvojité**, nebo **long double** hodnoty k **nepodepsané dlouho** nejsou přesné, pokud je hodnota převáděné větší než maximální kladnou **dlouho** hodnotu.

## <a name="see-also"></a>Viz také

[Převody přiřazení](../c-language/assignment-conversions.md)  
