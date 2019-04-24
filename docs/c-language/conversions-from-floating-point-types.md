---
title: Převody z typů s plovoucí desetinnou čárkou
ms.date: 01/29/2018
helpviewer_keywords:
- converting floating point
- floating-point conversion
ms.assetid: 96804c8e-fa3b-4742-9006-0082ed9e57f2
ms.openlocfilehash: 87e1554897326039649829539443795cbc0fabab
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62312521"
---
# <a name="conversions-from-floating-point-types"></a>Převody z typů s plovoucí desetinnou čárkou

A **float** převedeny na hodnotu **double** nebo **long double**, nebo **double** převést na **dlouho dvakrát**, prochází nezměnila hodnota. A **double** převedeny na hodnotu **float** hodnota je reprezentován přesně, pokud je to možné. Pokud hodnota se nedá přesně prezentovat, může dojít ke ztrátě přesnosti. Pokud výsledek je mimo rozsah, není chování definováno. Zobrazit [omezení konstant s plovoucí desetinné čárky s](../c-language/limits-on-floating-point-constants.md) pro řadu typů s plovoucí desetinnou čárkou.

Hodnotu s plovoucí desetinnou čárkou je převeden na celočíselnou hodnotu prvního přejdete k **dlouhé**, pak z **dlouhé** hodnotu na konkrétní celočíselnou hodnotu. Desetinnou část hodnoty s plovoucí desetinnou čárkou je zahozena v převod na **dlouhé**. Pokud výsledek je stále se nevešla do **dlouhé**, výsledek převod není definován.

**Microsoft Specific**

Při převodu **double** nebo **long double** číslo s plovoucí desetinnou čárkou na menší s plovoucí desetinnou čárkou číslo, hodnotu proměnné s plovoucí desetinnou čárkou je zkrácena směrem k nule, když dojde k podtečení. Přetečení způsobí chybu za běhu. Všimněte si, že kompilátor Microsoft C mapuje **long double** na typ **double**.

**Specifické pro END Microsoft**

Následující tabulka shrnuje převody z typů s plovoucí desetinnou čárkou.

## <a name="conversions-from-floating-point-types"></a>Převody z typů s plovoucí desetinnou čárkou

|From|Chcete-li|Metoda|
|----------|--------|------------|
|**float**|**char**|Převést na **dlouhé**; převod **dlouhé** k **char**|
|**float**|**short**|Převést na **dlouhé**; převod **dlouhé** k **krátké**|
|**float**|**long**|Zkraťte na desetinné čárky. Pokud je výsledek příliš velký, aby se dala vyjádřit jako **dlouhé**, výsledek není definován.|
|**float**|**short bez znaménka**|Převést na **dlouhé**; převod **dlouhé** k **unsigned short**|
|**float**|**unsigned long**|Převést na **dlouhé**; převod **dlouhé** k **unsigned long**|
|**float**|**double**|Změnit vnitřní reprezentaci|
|**float**|**typ long double**|Změnit vnitřní reprezentaci|
|**double**|**char**|Převést na **float**; převod **float** k **char**|
|**double**|**short**|Převést na **float**; převod **float** k **krátké**|
|**double**|**long**|Zkraťte na desetinné čárky. Pokud je výsledek příliš velký, aby se dala vyjádřit jako **dlouhé**, výsledek není definován.|
|**double**|**short bez znaménka**|Převést na **dlouhé**; převod **dlouhé** k **unsigned short**|
|**double**|**unsigned long**|Převést na **dlouhé**; převod **dlouhé** k **unsigned long**|
|**double**|**float**|Znázornění jako **float**. Pokud **double** hodnota nemůže být reprezentován přesně jako **float**, dojde ke ztrátě přesnosti. Pokud hodnota je moc velká, aby se dala vyjádřit jako **float**, výsledek nedefinován.|
|**typ long double**|**char**|Převést na **float**; převod **float** k **char**|
|**typ long double**|**short**|Převést na **float**; převod **float** k **krátké**|
|**typ long double**|**long**|Zkraťte na desetinné čárky. Pokud je výsledek příliš velký, aby se dala vyjádřit jako **dlouhé**, výsledek není definován.|
|**typ long double**|**short bez znaménka**|Převést na **dlouhé**; převod **dlouhé** k **unsigned short**|
|**typ long double**|**unsigned long**|Převést na **dlouhé**; převod **dlouhé** k **unsigned long**|
|**typ long double**|**float**|Znázornění jako **float**. Pokud **double** hodnota nemůže být reprezentován přesně jako **float**, dojde ke ztrátě přesnosti. Pokud hodnota je moc velká, aby se dala vyjádřit jako **float**, výsledek nedefinován.|
|**typ long double**|**double**|**Long double** je považován za hodnotu **double**.|

Převody z **float**, **double**, nebo **long double** hodnoty **unsigned long** nejsou přesné, pokud je převáděná hodnota větší než maximální pozitivní **dlouhé** hodnotu.

## <a name="see-also"></a>Viz také:

[Převody přiřazení](../c-language/assignment-conversions.md)
