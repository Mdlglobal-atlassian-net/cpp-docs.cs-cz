---
title: strcoll – funkce
ms.date: 11/04/2016
api_location:
- msvcr120.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr80.dll
- msvcr100.dll
- msvcr110.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- strcoll
helpviewer_keywords:
- code pages, using for string comparisons
- string comparison [C++], culture-specific
- strcoll functions
- strings [C++], comparing by code page
ms.assetid: c09eeff3-8aba-4cfb-a524-752436d85573
ms.openlocfilehash: c63a130cee6913006fff2ed5568c41cc4fdeac3c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944902"
---
# <a name="strcoll-functions"></a>strcoll – funkce

Každá z `strcoll` funkcí a `wcscoll` porovnává `LC_COLLATE` dva řetězce podle nastavení kategorie aktuálně používané znakové stránky národního prostředí. Každá z `_mbscoll` těchto funkcí Porovná dva řetězce podle vícebajtové kódové stránky, která se právě používá. `coll` Použijte funkce pro porovnávání řetězců, pokud existuje rozdíl mezi pořadím znakové sady a pořadím znaků lexikografickým pořadím na aktuální znakové stránce a tento rozdíl je pro porovnání důležité. Použijte odpovídající `cmp` funkce k otestování pouze pro řetězcovou rovnost.

### <a name="strcoll-functions"></a>strcoll – funkce

|SBCS|Kódování Unicode|MBCS|Popis|
|----------|-------------|----------|-----------------|
|[strcoll](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|[wcscoll](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|[_mbscoll](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|Kompletovat dva řetězce|
|[_stricoll](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|[_wcsicoll](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|[_mbsicoll](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|Kompletuje dva řetězce (nerozlišuje velikost písmen).|
|[_strncoll](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|[_wcsncoll](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|[_mbsncoll](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|Vycollate `count` první znaky dvou řetězců|
|[_strnicoll](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|[_wcsnicoll](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|[_mbsnicoll](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|Vycollate `count` první znaky dvou řetězců (bez rozlišení velkých a malých písmen)|

## <a name="remarks"></a>Poznámky

`strcoll`Verze jednobajtových znaků (,, a) s jednou bajtem (, `stricoll`, `_strncoll`a `_strnicoll`) se porovnávají `string2` `string1` a `LC_COLLATE` odpovídají nastavení kategorie aktuálního národního prostředí. Tyto funkce se liší od odpovídajících `strcmp` funkcí v `strcoll` tom, že funkce používají informace o znakové stránce národního prostředí, které poskytují kolaci sekvence. Pro porovnávání řetězců v národních prostředích, ve kterých se liší pořadí znakových sad a lexikografickým pořadím znaků, `strcoll` by měly být funkce použity spíše než odpovídající `strcmp` funkce. Další informace o `LC_COLLATE`naleznete v tématu [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md).

Pro některé znakové stránky a odpovídající znakové sady se pořadí znaků ve znakové sadě může lišit od pořadí znaků lexikografickým pořadím. V národním prostředí "C" se nejedná o tento případ: pořadí znaků v sadě znaků ASCII je stejné jako lexikografickým pořadím pořadí znaků. V některých evropských kódových stránkách například znak "a" (Value 0x61) předchází znak "ä" (Value 0xE4) ve znakové sadě, ale znak "ä" před znakem "a" lexikograficky. Chcete-li provést porovnání lexikografickým pořadím v takové instanci, použijte `strcoll` spíše než `strcmp`. Alternativně můžete použít `strxfrm` původní řetězce a potom použít `strcmp` na výsledných řetězcích.

`strcoll`, `stricoll`, a`_strnicoll` automaticky zpracovávají vícebajtové znakové řetězce podle aktuálně používané znakové stránky národního prostředí, stejně jako jejich protějšky mezi znaky (Unicode). `_strncoll` Verze vícebajtových znaků (MBCS) těchto funkcí ale sestaví řetězce na základě znaku podle vícebajtové kódové stránky, která se právě používá.

Vzhledem k tomu, že `cmp` `coll` `coll` funkce kompletují řetězce lexikograficky pro porovnání, zatímco funkcejednodušetestujírovnostřetězců,funkcejsoumnohempomalejší`cmp` než odpovídající verze. Proto by měly být funkcepoužitypouzevpřípadě,žejerozdílmezipořadímznakovésadyapořadímlexikografickýmpořadímznakůvaktuálníznakovéstránceatentorozdíljevzájmuporovnánířetězců.`coll`

## <a name="see-also"></a>Viz také:

[Národní prostředí](../c-runtime-library/locale.md)<br/>
[Manipulace s řetězci](../c-runtime-library/string-manipulation-crt.md)<br/>
[localeconv](../c-runtime-library/reference/localeconv.md)<br/>
[_mbsnbcoll, _mbsnbcoll_l, _mbsnbicoll, _mbsnbicoll_l](../c-runtime-library/reference/mbsnbcoll-mbsnbcoll-l-mbsnbicoll-mbsnbicoll-l.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[strcmp, wcscmp, _mbscmp](../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)
