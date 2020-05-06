---
title: Specifikace osmičkových a šestnáctkových znaků
ms.date: 11/04/2016
helpviewer_keywords:
- octal characters
- hexadecimal characters
ms.assetid: 9264f3ec-46b8-41a5-b21a-8f7ed0a11871
ms.openlocfilehash: df4d0666a220961f64238bf95dca9e0a08d4dae6
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "64343370"
---
# <a name="octal-and-hexadecimal-character-specifications"></a>Specifikace osmičkových a šestnáctkových znaků

Sekvence **\\** <em>OOO</em> znamená, že můžete zadat libovolný znak ve znakové sadě ASCII jako třímístný osmičkový kód znaku. Číselná hodnota osmičkového čísla určuje hodnotu požadovaného znaku nebo širokého znaku.

Podobně sekvence **\x**<em>HHH</em> umožňuje určit libovolný znak ASCII jako kód hexadecimálního znaku. Například můžete zadat znak Backspace ASCII jako normální řídicí sekvenci jazyka C (**\b**), nebo ho můžete kódovat jako **\ 010** (osmičková) nebo **\x008** (šestnáctkově).

V osmičkové řídicí sekvenci lze použít pouze číslice 0 až 7. Osmičkové řídicí sekvence nemohou být nikdy delší než tři číslice a jsou ukončeny prvním znakem, který není osmičkovou číslicí. Přestože není nutné použít všechny tři číslice, je třeba použít nejméně jednu. Například osmičková reprezentace je **\ 10** pro znak Backspace ASCII a **\ 101** pro písmeno a, jak je uvedeno v grafu ASCII.

Podobně je třeba použít alespoň jednu číslici šestnáctkové řídicí sekvence, ale lze vynechat druhou a třetí číslici. Proto můžete zadat hexadecimální sekvenci Escape pro znak Backspace buď jako **\x8**, **\x08**nebo **\x008**.

Hodnota osmičkové nebo šestnáctkové řídicí sekvence musí být v rozsahu reprezentovatelné hodnoty pro typ znaku **bez znaménka** pro znaková konstanta a typ `wchar_t` pro konstantu širokého znaku. Informace o konstantách s velkým znakem naleznete v tématu [vícebajtové a velké znaky](../c-language/multibyte-and-wide-characters.md) .

Na rozdíl od osmičkové řídicí konstanty není počet šestnáctkových číslic v řídicí sekvenci nijak omezen. Šestnáctková řídicí sekvence se ukončí na prvním znaku, který není šestnáctkovou číslicí. Vzhledem k tomu, že hexadecimální číslice obsahují písmena **a** až **f**, je nutné se ujistit, že řídicí sekvence končí zamýšlenou číslicí. Aby nedocházelo k záměně, lze znak šestnáctkové nebo osmičkové definice umístit do definice makra:

```
#define Bell '\x07'
```

U šestnáctkových hodnot je možné řetězec přerušit pro zřetelné zobrazení správné hodnoty:

```
"\xabc"    /* one character  */
"\xab" "c" /* two characters */
```

## <a name="see-also"></a>Viz také

[Konstanty znaků jazyka C](../c-language/c-character-constants.md)
