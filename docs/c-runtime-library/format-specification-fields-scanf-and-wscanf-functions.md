---
title: 'Pole specifikace formátu: funkce scanf a wscanf'
ms.date: 11/04/2016
helpviewer_keywords:
- width, specifications in scanf function
- scanf format specifications
- scanf width specifications
- scanf type field characters
- type fields, scanf function
- format specification fields for scanf function
- type fields
ms.assetid: 7e95de1b-0b71-4de3-9f81-c9560c78e039
ms.openlocfilehash: 025d4c164d3afe1ca6b05c1c8e76441109cbc4ae
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438361"
---
# <a name="format-specification-fields-scanf-and-wscanf-functions"></a>Pole specifikace formátu: funkce scanf a wscanf

Zde uvedené informace platí pro celou `scanf`ou rodinu funkcí, včetně zabezpečených verzí a popisuje symboly používané k určení `scanf` funkcí, jak analyzovat vstupní datový proud, jako je vstupní datový proud `stdin` pro `scanf`, do hodnot, které jsou vloženy do proměnných programu.

Specifikace formátu má následující formát:

`%`[`*`] [[Width](../c-runtime-library/scanf-width-specification.md)] [{[h &#124; l &#124; šechny &#124; I64 &#124; l](../c-runtime-library/scanf-width-specification.md)}][typ](../c-runtime-library/scanf-type-field-characters.md)

Argument `format` určuje výklad vstupu a může obsahovat jednu nebo více následujících možností:

- Prázdné znaky: prázdné (' '); TAB (' \t '); nebo nový řádek (' \n '). Prázdný znak způsobí, že `scanf` číst, ale ne ukládat, všechny po sobě jdoucí prázdné znaky ve vstupu až k dalšímu neprázdnému znaku. Jeden prázdný znak ve formátu odpovídá libovolnému číslu (včetně 0) a kombinaci prázdných znaků ve vstupu.

- Jiné než prázdné znaky, s výjimkou znaku procenta (`%`). Neprázdný znak způsobí, že `scanf` číst, ale nikoli uložit, odpovídá neprázdný znak. Pokud se další znak ve vstupním datovém proudu neshoduje, `scanf` ukončí.

- Specifikace formátu zavedené znakem procenta (`%`) Specifikace formátu způsobí, že `scanf` čte a převádí znaky ve vstupu na hodnoty zadaného typu. Hodnota je přiřazena k argumentu v seznamu argumentů.

Formát je čten zleva doprava. Očekává se, že znaky mimo specifikace formátu budou odpovídat sekvenci znaků ve vstupním proudu; vyhovující znaky ve vstupním datovém proudu jsou prohledávány, ale nejsou uloženy. Pokud znak ve vstupním datovém proudu koliduje se specifikací formátu, `scanf` ukončí a znak zůstane ve vstupním proudu, jako by nebyl přečten.

Při zjištění prvního formátu je hodnota prvního vstupního pole převedena podle této specifikace a uložena v umístění, které je určeno prvním `argument`. Druhá specifikace formátu způsobí, že druhé vstupní pole bude převedeno a Uloženo v druhém `argument`a tak dále až po konci řetězce formátu.

Vstupní pole je definováno jako všechny znaky až do prvního prázdného znaku (mezerník, TAB nebo nového znaku) nebo až po první znak, který nelze převést podle specifikace formátu, nebo dokud není dosaženo šířky pole (Pokud je zadáno). Pokud je pro dané specifikace příliš mnoho argumentů, jsou vyhodnoceny nadbytečné argumenty, ale budou ignorovány. Výsledky jsou nepředvídatelné, pokud není dostatek argumentů pro specifikaci formátu.

Každé pole specifikace formátu je jeden znak nebo číslo značící konkrétní možnost formátu. `type` znak, který se zobrazí po posledním volitelném poli formátu, určuje, zda je vstupní pole interpretováno jako znak, řetězec nebo číslo.

Specifikace nejjednoduššího formátu obsahuje pouze znak procenta a `type` (například `%s`). Pokud je znak procenta (`%`) následován znakem, který nemá žádný význam jako znak pro řízení formátu, považuje se tento znak a následující znaky (až k dalšímu znaku procenta) jako běžná sekvence znaků, tj. sekvence znaků, které musí odpovídat vstupu. Například chcete-li určit, že znak procenta-znaménka bude vstup, použijte `%%`.

Hvězdička (`*`) následující po znaménku procenta potlačuje přiřazení dalšího vstupního pole, které je interpretováno jako pole zadaného typu. Pole je prohledáváno, ale není uloženo.

Zabezpečené verze (s příponou `_s`) `scanf` rodina funkcí vyžadují, aby byl parametr velikosti vyrovnávací paměti předán Hned za každým parametrem typu `c`, `C`, `s`, `S` nebo `[`. Další informace o zabezpečených verzích `scanf` řady funkcí najdete v tématu [scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md).

## <a name="see-also"></a>Viz také

[scanf – specifikace šířky](../c-runtime-library/scanf-width-specification.md)<br/>
[scanf – znaky pole typu](../c-runtime-library/scanf-type-field-characters.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)
