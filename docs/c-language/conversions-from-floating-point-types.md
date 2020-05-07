---
title: Převody z typů s plovoucí desetinnou čárkou
ms.date: 10/02/2019
helpviewer_keywords:
- converting floating point
- floating-point conversion
ms.assetid: 96804c8e-fa3b-4742-9006-0082ed9e57f2
ms.openlocfilehash: c2f7c25015b36545f969796a1f85d355d715427a
ms.sourcegitcommit: c51b2c665849479fa995bc3323a22ebe79d9d7ce
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "71998711"
---
# <a name="conversions-from-floating-point-types"></a>Převody z typů s plovoucí desetinnou čárkou

Hodnota s plovoucí desetinnou čárkou, která je převedena na jiný typ s plovoucí desetinnou čárkou, se nemění v hodnotě, pokud je původní hodnota reprezentována přesně v typu výsledku. Pokud je původní hodnota číselná, ale není k dispozici, je výsledkem buď další větší nebo další nižší hodnota, která je reprezentovatelné. Viz [omezení konstant s plovoucí](../c-language/limits-on-floating-point-constants.md) desetinnou čárkou pro rozsah typů s plovoucí desetinnou čárkou.

Hodnota s plovoucí desetinnou čárkou, která je převedena na celočíselný typ, je nejprve zkrácena zahozením jakékoli desetinné hodnoty. Pokud je tato Zkrácená hodnota reprezentována v typu výsledku, musí být výsledkem tato hodnota. Pokud jej nelze reprezentovat, hodnota výsledku není definována.

**Specifické pro Microsoft**

Kompilátory Microsoftu používají reprezentaci IEEE-754 binary32 pro hodnoty **float** a reprezentaci binary64 pro **Long Double** a **Double**. Vzhledem k tomu, že **Long Double** a **Double** používají stejnou reprezentaci, mají stejný rozsah a přesnost.

Když kompilátor převede dvojité nebo **dlouhé dvojité** číslo s plovoucí desetinnou čárkou na **typ** **float**, zaokrouhlí výsledek podle ovládacích prvků prostředí s plovoucí desetinnou čárkou, což je výchozí nastavení "zaokrouhlit na nejbližší, vazby na sudé". Je-li číselná hodnota příliš vysoká nebo příliš nízká, aby byla reprezentována jako číselná hodnota **float** , je výsledkem převodu kladná nebo záporná nekonečna v závislosti na znaménku původní hodnoty a je vyvolána výjimka přetečení, pokud je povolena.

Při převodu na celočíselné typy je výsledek převodu na typ menší než **Long** výsledkem převodu hodnoty na **Long**a následným převodem na typ výsledku.

Pro převod na celočíselné typy alespoň na velká, **Pokud**je převod hodnoty, která je příliš vysoká nebo příliš nízká pro reprezentaci ve výsledném typu, může vracet některou z následujících hodnot:

- Výsledkem může být *hodnota Sentinel*, což je reprezentovatelné hodnoty nejvíce od nuly. U podepsaných typů je to nejnižší reprezentovatelné číslo (0x800... 0). U typů bez znaménka se jedná o nejvyšší reprezentovatelné hodnoty (0xFF... F).

- Výsledek může být *sytost*, kde hodnoty příliš vysoké pro reprezentaci jsou převedeny na nejvyšší reprezentovatelné hodnoty a hodnoty, které jsou příliš nízké pro reprezentaci, jsou převedeny na nejnižší reprezentovatelné hodnoty. Jedna z těchto dvou hodnot se používá také jako hodnota Sentinel.

- Pro převod na **celé číslo bez znaménka** Long nebo **bez znaménka**, výsledek převodu hodnoty mimo rozsah může být jinou hodnotou než nejvyšší nebo nejnižší reprezentovatelné hodnoty. Zda je výsledkem Sentinel nebo sytost hodnoty, nebo nezávisí na možnostech kompilátoru a cílové architektuře. Budoucí verze kompilátoru můžou místo toho vracet hodnotu sytosti nebo Sentinel.

**Specifické pro konec Microsoftu**

Následující tabulka shrnuje převody z plovoucích typů.

## <a name="table-of-conversions-from-floating-point-types"></a>Tabulka převodů z typů s plovoucí desetinnou čárkou

|From|Akce|Metoda|
|----------|--------|------------|
|**Plovák**|**char**|Převést na **Long**; převod **dlouhé** na **char**|
|**Plovák**|**short**|Převést na **Long**; převést na **krátkou** **dobu**|
|**Plovák**|**int**|Zkrátit na desetinnou čárku Pokud je výsledek příliš velký, aby jej bylo možné znázornit jako **int**, výsledek není definován.|
|**Plovák**|**long**|Zkrátit na desetinnou čárku Pokud je výsledek příliš velký, aby jej bylo možné znázornit jako **Long**, výsledek není definován.|
|**Plovák**|**long long**|Zkrátit na desetinnou čárku Pokud je výsledek příliš velký, aby jej bylo možné znázornit po **dlouhou**dobu, není výsledek definován.|
|**Plovák**|**unsigned char**|Převést na **Long**; převést **dlouhé** na **nepodepsaný znak**|
|**Plovák**|**unsigned short**|Převést na **Long**; převod **Long** na **unsigned short**|
|**Plovák**|**celé**|Zkrátit na desetinnou čárku Pokud je výsledek příliš velký, aby jej bylo možné znázornit jako **unsigned**, výsledek není definován.|
|**Plovák**|**unsigned long**|Zkrátit na desetinnou čárku Pokud je výsledek příliš velký, aby jej bylo možné znázornit jako **unsigned long**, výsledek není definován.|
|**Plovák**|**dlouhý unsigned long**|Zkrátit na desetinnou čárku Pokud je výsledek příliš velký, aby jej bylo možné znázornit jako **unsigned long long**, výsledek není definován.|
|**Plovák**|**double**|Představuje **typ Double**.|
|**Plovák**|**Long Double**|Reprezentuje jako **typ long double**.|
|**double**|**char**|Převést na **float**; převést **float** na **char**|
|**double**|**short**|Převést na **float**; převést **float** na **short**|
|**double**|**int**|Zkrátit na desetinnou čárku Pokud je výsledek příliš velký, aby jej bylo možné znázornit jako **int**, výsledek není definován.|
|**double**|**long**|Zkrátit na desetinnou čárku Pokud je výsledek příliš velký, aby jej bylo možné znázornit jako **Long**, výsledek není definován.|
|**double**|**unsigned char**|Převést na **Long**; převést **dlouhé** na **nepodepsaný znak**|
|**double**|**unsigned short**|Převést na **Long**; převod **Long** na **unsigned short**|
|**double**|**celé**|Zkrátit na desetinnou čárku Pokud je výsledek příliš velký, aby jej bylo možné znázornit jako **unsigned**, výsledek není definován.|
|**double**|**unsigned long**|Zkrátit na desetinnou čárku Pokud je výsledek příliš velký, aby jej bylo možné znázornit jako **unsigned long**, výsledek není definován.|
|**double**|**dlouhý unsigned long**|Zkrátit na desetinnou čárku Pokud je výsledek příliš velký, aby jej bylo možné znázornit jako **unsigned long long**, výsledek není definován.|
|**double**|**Plovák**|Představuje typ **float**. Pokud hodnota typu **Double** nemůže být reprezentována přesně jako **float**, dojde ke ztrátě přesnosti. Je-li hodnota příliš velká, aby byla reprezentována jako **float**, výsledek není definován.|
|**double**|**Long Double**|Hodnota **Long Double** je považována za **dvojitou**hodnotu.|

Převody z **dlouhého typu Double** sledují stejnou metodu jako převody z **Double**.

## <a name="see-also"></a>Viz také

[Převody přiřazení](../c-language/assignment-conversions.md)
