---
title: 'Pole specifikace formátu: funkce scanf a wscanf'
ms.date: 11/04/2016
api_location:
- msvcr80.dll
- msvcr110.dll
- msvcr90.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr120.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wscanf
- scanf
helpviewer_keywords:
- width, specifications in scanf function
- scanf format specifications
- scanf width specifications
- scanf type field characters
- type fields, scanf function
- format specification fields for scanf function
- type fields
ms.assetid: 7e95de1b-0b71-4de3-9f81-c9560c78e039
ms.openlocfilehash: 78b64ea29aebdfb355525be69dc7a9fdece55367
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944419"
---
# <a name="format-specification-fields-scanf-and-wscanf-functions"></a>Pole specifikace formátu: funkce scanf a wscanf

Zde uvedené informace platí pro celou `scanf` rodinu funkcí, včetně zabezpečených verzí a popisuje symboly, které slouží k `scanf` oznámení funkcím, jak analyzovat vstupní datový proud, jako je vstupní datový proud `stdin` pro `scanf`do hodnot, které jsou vloženy do proměnných programu.

Specifikace formátu má následující formát:

`%`[`*`] [[Width](../c-runtime-library/scanf-width-specification.md)] [{[h &#124; l &#124; šechny &#124; I64 &#124; l](../c-runtime-library/scanf-width-specification.md)}][typ](../c-runtime-library/scanf-type-field-characters.md)

`format` Argument určuje výklad vstupu a může obsahovat jednu nebo více z následujících možností:

- Prázdné znaky: prázdné (' '); TAB (' \t '); nebo nový řádek (' \n '). Prázdný znak má za následek `scanf` čtení, ale ne uložení, všechny po sobě jdoucí prázdné znaky ve vstupu až k dalšímu neprázdnému znaku. Jeden prázdný znak ve formátu odpovídá libovolnému číslu (včetně 0) a kombinaci prázdných znaků ve vstupu.

- Jiné než prázdné znaky, s výjimkou znaku procenta (`%`). Neprázdný znak má za následek `scanf` čtení, ale nikoli uložení, odpovídajícího neprázdného znaku. Pokud se další znak ve vstupním datovém proudu neshoduje, `scanf` ukončí.

- Specifikace formátu zavedené znakem procenta (`%`) Specifikace formátu způsobuje `scanf` čtení a převod znaků ve vstupu na hodnoty zadaného typu. Hodnota je přiřazena k argumentu v seznamu argumentů.

Formát je čten zleva doprava. Očekává se, že znaky mimo specifikace formátu budou odpovídat sekvenci znaků ve vstupním proudu; vyhovující znaky ve vstupním datovém proudu jsou prohledávány, ale nejsou uloženy. Pokud znak ve vstupním datovém proudu koliduje se specifikací formátu `scanf` , končí a znak zůstane ve vstupním proudu, jako by nebyl přečten.

Při zjištění prvního formátu je hodnota prvního vstupního pole převedena podle této specifikace a uložena v umístění, které je určeno prvním `argument`. Druhá specifikace formátu způsobí, že druhé vstupní pole bude převedeno a Uloženo v druhém `argument`a tak dále až na konci formátovacího řetězce.

Vstupní pole je definováno jako všechny znaky až do prvního prázdného znaku (mezerník, TAB nebo nového znaku) nebo až po první znak, který nelze převést podle specifikace formátu, nebo dokud není dosaženo šířky pole (Pokud je zadáno). Pokud je pro dané specifikace příliš mnoho argumentů, jsou vyhodnoceny nadbytečné argumenty, ale budou ignorovány. Výsledky jsou nepředvídatelné, pokud není dostatek argumentů pro specifikaci formátu.

Každé pole specifikace formátu je jeden znak nebo číslo značící konkrétní možnost formátu. `type` Znak, který se zobrazí po posledním volitelném poli formátu, určuje, zda je vstupní pole interpretováno jako znak, řetězec nebo číslo.

Specifikace nejjednoduššího formátu obsahuje pouze znak procenta a `type` znak ( `%s`například). Pokud je znak procenta (`%`) následován znakem, který nemá žádný význam jako znak pro řízení formátu, je tento znak a následující znaky (až k dalšímu znaku procenta) považovány za běžnou sekvenci znaků, tj. sekvence znaky, které musí odpovídat vstupu. Například chcete-li určit, že znak procenta-znaménka má být Input, použijte `%%`.

Hvězdička (`*`) za znakem procenta potlačuje přiřazení dalšího vstupního pole, které je interpretováno jako pole zadaného typu. Pole je prohledáváno, ale není uloženo.

`_s` Zabezpečené verze (s příponou) `scanf` rodiny funkcí vyžadují, aby byl parametr velikosti vyrovnávací paměti předán Hned za každý parametr typu `c`, `C`, `s`, `S` nebo`[`. Další informace o zabezpečených verzích `scanf` řady funkcí naleznete v tématu [scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md).

## <a name="see-also"></a>Viz také:

[scanf – specifikace šířky](../c-runtime-library/scanf-width-specification.md)<br/>
[scanf – znaky pole typu](../c-runtime-library/scanf-type-field-characters.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)
