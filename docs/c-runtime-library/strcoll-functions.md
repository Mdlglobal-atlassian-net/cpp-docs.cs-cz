---
title: strcoll – funkce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apilocation:
- msvcr120.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr80.dll
- msvcr100.dll
- msvcr110.dll
apitype: DLLExport
f1_keywords:
- strcoll
dev_langs:
- C++
helpviewer_keywords:
- code pages, using for string comparisons
- string comparison [C++], culture-specific
- strcoll functions
- strings [C++], comparing by code page
ms.assetid: c09eeff3-8aba-4cfb-a524-752436d85573
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c207bc94dbadf5e346c74d314e13df3530368fb9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46080477"
---
# <a name="strcoll-functions"></a>strcoll – funkce

Každá z `strcoll` a `wcscoll` funkce porovná dva řetězce podle `LC_COLLATE` nastavením kategorie znaková stránka národního prostředí nevyužívají. Každá z `_mbscoll` funkce porovná dva řetězce podle vícebajtové znakové stránky, která aktuálně používán. Použití `coll` funkce pro porovnávání řetězců, když je rozdíl mezi znakové sady a lexikografickým pořadím znaků v aktuální znakové stránce a tento rozdíl je relevantní pro porovnání. Použít odpovídající `cmp` funkce pro testování pouze pro řetězcový rovnosti.

### <a name="strcoll-functions"></a>strcoll – funkce

|SBCS|Kódování Unicode|MBCS|Popis|
|----------|-------------|----------|-----------------|
|[strcoll –](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|[wcscoll –](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|[_mbscoll –](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|Kompletují dva řetězce|
|[_stricoll](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|[_wcsicoll](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|[_mbsicoll –](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|Kompletují dva řetězce (malých písmen)|
|[_strncoll](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|[_wcsncoll](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|[_mbsncoll –](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|COLLATE – první `count` znaky ze dvou řetězců|
|[_strnicoll](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|[_wcsnicoll](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|[_mbsnicoll –](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|COLLATE – první `count` znaky ze dvou řetězců (velká a malá písmena)|

## <a name="remarks"></a>Poznámky

Jednobajtový znak (SBCS) verze těchto funkcí (`strcoll`, `stricoll`, `_strncoll`, a `_strnicoll`) porovnání `string1` a `string2` podle `LC_COLLATE` kategorie nastavení aktuálního národního prostředí. Tyto funkce se liší od odpovídajícího `strcmp` funkce v, který `strcoll` funkce pomocí kódu stránky informací o národním prostředí, která poskytuje pořadí řazení. Pro porovnávání řetězců v národních prostředí, ve kterých znakové sady, pořadí a lexikografickým pořadím znaků se liší `strcoll` funkce by měla používat místo odpovídající `strcmp` funkce. Další informace o `LC_COLLATE`, naleznete v tématu [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md).

Pro některé kódové stránky a příslušné znakové sady se pořadí znaků ve znakové sadě může lišit od pořadí lexikografických znaků. V národním prostředí "C", to není případ: pořadí znaků ve znakové sadě ASCII je stejné jako lexikografické pořadí znaků. Ale v některých evropských znakových stránek, například znak "a" (hodnota 0x61) předchází znakové "č. (hodnota 0xE4) v znakové sady, ale znak"č' předchází znak "a" lexicographically. K provedení lexikografického porovnání v takové situaci, použijte `strcoll` spíše než `strcmp`. Alternativně můžete použít `strxfrm` na původním řetězců, pak použijte `strcmp` na výsledného řetězce.

`strcoll`, `stricoll`, `_strncoll`, a `_strnicoll` automaticky zpracovává vícebajtové znakové řetězce podle kódové stránky aktuálně používané národní prostředí, stejně jako jejich protějšky širokého znaku (Unicode). Vícebajtové (znakové sady MBCS) verze těchto funkcí, ale kompletují řetězce na základě znak podle vícebajtové znakové stránky, která aktuálně používán.

Protože `coll` funkce kompletují řetězce lexikograficky pro porovnávání, zatímco `cmp` funkce jednoduše testují rovnost řetězců, `coll` jsou mnohem pomalejší než odpovídající funkce `cmp` verze. Proto `coll` funkce by měly být používány pouze v případě, že existuje rozdíl mezi znakové sady a lexikografickým pořadím znaků v aktuální znakové stránce a tento rozdíl je relevantní pro porovnání řetězců.

## <a name="see-also"></a>Viz také

[Národní prostředí](../c-runtime-library/locale.md)<br/>
[Zacházení s řetězci](../c-runtime-library/string-manipulation-crt.md)<br/>
[localeconv](../c-runtime-library/reference/localeconv.md)<br/>
[_mbsnbcoll, _mbsnbcoll_l, _mbsnbicoll, _mbsnbicoll_l](../c-runtime-library/reference/mbsnbcoll-mbsnbcoll-l-mbsnbicoll-mbsnbicoll-l.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[strcmp, wcscmp, _mbscmp](../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)