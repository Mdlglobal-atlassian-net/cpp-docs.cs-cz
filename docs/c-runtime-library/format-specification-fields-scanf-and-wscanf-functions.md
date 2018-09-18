---
title: 'Pole Specifikace formátu: funkce scanf a wscanf | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apilocation:
- msvcr80.dll
- msvcr110.dll
- msvcr90.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- wscanf
- scanf
dev_langs:
- C++
helpviewer_keywords:
- width, specifications in scanf function
- scanf format specifications
- scanf width specifications
- scanf type field characters
- type fields, scanf function
- format specification fields for scanf function
- type fields
ms.assetid: 7e95de1b-0b71-4de3-9f81-c9560c78e039
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0f99d7dac7878f46fceea4435703a55f2199f374
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46094504"
---
# <a name="format-specification-fields-scanf-and-wscanf-functions"></a>Pole specifikace formátu: funkce scanf a wscanf

Zde uvedené informace platí pro celý `scanf` řadu funkcí, včetně bezpečné verze a popisuje symboly pozná `scanf` funguje jak parsovat vstupní datový proud, jako je například vstupního datového proudu `stdin` pro `scanf`, na hodnoty, které jsou vloženy do programu proměnné.

Specifikace formátu má následující formát:

`%`[`*`] [[šířka](../c-runtime-library/scanf-width-specification.md)] [{[h &#124; l &#124; ll &#124; I64 &#124; L](../c-runtime-library/scanf-width-specification.md)}][typu](../c-runtime-library/scanf-type-field-characters.md)

`format` Určuje interpretují vstupní argument a může obsahovat jednu nebo více z následujících akcí:

- Prázdné znaky: prázdné (""); Karta ('\t'); nebo znaku nového řádku ('\n'). Prázdný znak způsobí, že `scanf` číst, ale ne ukládat všechny po sobě jdoucích prázdných znaků ve vstupním až do další znak prázdné znaky. Jeden prázdný znak ve formátu odpovídá jakékoli číslo (včetně 0) a kombinace prázdné znaky ve vstupu.

- Bez prázdných znaků, s výjimkou znak procent (`%`). Způsobí, že znaku prázdný znak `scanf` pro čtení, ale ne ukládat odpovídající znaku prázdný znak. Pokud následující znak ve vstupním datovém proudu neodpovídá, `scanf` ukončí.

- Specifikace zavedené znak procent formátu (`%`). Specifikace formátu způsobí, že `scanf` ke čtení a převod znaků ve vstupním do zadaného typu hodnoty. Hodnota je přiřazená k argumentu v seznam argumentů.

Formát je pro čtení zleva doprava. Znaky mimo specifikace formátu se očekává tak, aby odpovídala pořadí znaků ve vstupním datovém proudu; odpovídající znaky ve vstupním datovém proudu jsou zkontrolovány, ale nebyly uloženy. Pokud se znakem ve vstupním datovém proudu je v konfliktu s specifikace formátu `scanf` ukončí, a znak, který zůstane v vstupního datového proudu jako v případě, kdyby byl načten.

Vyskytne první specifikaci formátu hodnota první vstupní pole je převeden podle téhle specifikaci a uložen v umístění, která je zadána první `argument`. Druhá specifikace formátu způsobí, že druhé vstupní pole bude převeden a uložen do druhého `argument`, a tak dále až do konce řetězce formátu.

Vstupní pole je definován jako všechny znaky až po první znak prázdným (místo, tabulátor nebo nový řádek), nebo až po první znak, který nelze převést podle specifikace formátu, nebo dokud šířku pole (Pokud je zadaný) dostupný. Pokud existuje příliš mnoho argumentů pro danou specifikací, další argumenty jsou vyhodnoceny ale ignorována. Výsledky nepředvídatelné, pokud nejsou k dispozici dostatečný počet argumentů pro specifikace formátu.

Každé pole Specifikace formátu je znak nebo číslo značící danou formátovací volbu. `type` Znak, který se zobrazí za poslední formátu volitelné pole, určuje, zda vstupní pole je interpretován jako znak, řetězec nebo číslo.

Nejjednodušší specifikace formátu obsahuje pouze znak procent a `type` znaku (například `%s`). Pokud znak procent (`%`) je následován znakem, nemá žádný význam jako formát řídicí znak, znak a následující znaky (až do další znak procent) považovány za běžné posloupnost znaků, to znamená, posloupnost znaky, které musí odpovídat vstupu. Například, chcete-li určit, že má být vstupní znak procent, použít `%%`.

Hvězdičku (`*`) následující znak procent potlačí přiřazení další vstupní pole, které je interpretován jako pole určeného typu. Pole je zkontrolovány, ale nebyly uloženy.

Bezpečné verze (ty, které mají `_s` přípony) z `scanf` řady funkcí vyžadují, aby ihned po každého parametru typu předat parametr velikosti vyrovnávací paměti `c`, `C`, `s`, `S`nebo `[`. Další informace o bezpečné verze `scanf` řadu funkcí, naleznete v tématu [scanf_s _scanf_s_l –, wscanf_s – _wscanf_s_l –](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md).

## <a name="see-also"></a>Viz také

[scanf – specifikace šířky](../c-runtime-library/scanf-width-specification.md)<br/>
[scanf – znaky pole typu](../c-runtime-library/scanf-type-field-characters.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)