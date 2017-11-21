---
title: "strcoll – funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apilocation:
- msvcr120.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr80.dll
- msvcr100.dll
- msvcr110.dll
apitype: DLLExport
f1_keywords: strcoll
dev_langs: C++
helpviewer_keywords:
- code pages, using for string comparisons
- string comparison [C++], culture-specific
- strcoll functions
- strings [C++], comparing by code page
ms.assetid: c09eeff3-8aba-4cfb-a524-752436d85573
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 224c30dfbc79ab91e60f7f55f4835d3f627c454c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="strcoll-functions"></a>strcoll – funkce
Každý z `strcoll` a `wcscoll` funkce porovnává dva řetězce podle požadavků `LC_COLLATE` kategorie nastavení znaková stránka národního prostředí aktuálně používán. Každý z `_mbscoll` funkce porovnává dva řetězce podle vícebajtové znakové stránky aktuálně používán. Použití `coll` funkce pro porovnání řetězců, když je rozdíl mezi pořadí sady znaků a pořadí lexicographic znaků na aktuální stránce kódu a tento rozdíl je určen pro porovnání. Použijte odpovídající `cmp` funkce otestovat jenom pro řetězec rovnosti.  
  
### <a name="strcoll-functions"></a>strcoll – funkce  
  
|SBCS|Kódování Unicode|MBCS|Popis|  
|----------|-------------|----------|-----------------|  
|[strcoll –](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|[wcscoll –](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|[_mbscoll –](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|COLLATE dva řetězce|  
|[_stricoll –](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|[_wcsicoll –](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|[_mbsicoll –](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|COLLATE dva řetězce (rozlišuje velká a malá písmena)|  
|[_strncoll –](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|[_wcsncoll –](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|[_mbsncoll –](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|COLLATE nejprve `count` znaky ze dvou řetězců|  
|[_strnicoll –](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|[_wcsnicoll –](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|[_mbsnicoll –](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|COLLATE nejprve `count` znaky ze dvou řetězců (velká a malá písmena)|  
  
## <a name="remarks"></a>Poznámky  
 Tyto funkce verze znakovou (SBCS) (`strcoll`, `stricoll`, `_strncoll`, a `_strnicoll`) porovnat `string1` a `string2` podle požadavků `LC_COLLATE` kategorie nastavení aktuální národní prostředí. Tyto funkce se liší od odpovídající `strcmp` funkce v tom, že `strcoll` funkce použijte národního prostředí kódu stránky, které poskytuje pořadí řazení. Pro porovnání řetězců v národní prostředí, ve kterých znaková sada pořadí a pořadí lexicographic znaků liší `strcoll` funkce by měly používat místo odpovídající `strcmp` funkce. Další informace o `LC_COLLATE`, najdete v části [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md).  
  
 Pro některé znakové stránky a odpovídající znakových sad může na pořadí znaků ve znakové sadě liší od pořadí lexicographic znaků. V národním prostředí "C", to tak není: pořadí znaků ve znakové sadě ASCII je stejný jako lexicographic pořadí znaky. Ale v některých evropských znakové stránky, například znak "a" (hodnota 0x61) předchází znak 'č. (hodnota 0xE4) v znak nastavit, ale znak 'č' předchází znak "a" lexicographically. Pokud chcete provést lexicographic porovnání v takové instanci, použijte `strcoll` místo `strcmp`. Alternativně můžete použít `strxfrm` na původní řetězce, potom použijte `strcmp` výsledné řetězce.  
  
 `strcoll`, `stricoll`, `_strncoll`, a `_strnicoll` automaticky zpracování řetězců vícebajtových znaků podle znaková stránka národního prostředí právě využívá, stejně jako jejich protějšky široká charakterová (Unicode). Vícebajtových znaků (MBCS) verze tyto funkce a collate však řetězce na základě znak podle vícebajtové znakové stránky aktuálně používán.  
  
 Protože `coll` funkce collate řetězce lexicographically pro porovnání, zatímco `cmp` funkce jednoduše testování rovnosti řetězec, `coll` funkce jsou mnohem nižší než odpovídající `cmp` verze. Proto `coll` funkce by měly používat jenom v případě, že je rozdíl mezi pořadí sady znaků a pořadí lexicographic znaků na aktuální stránce kódu a tento rozdíl je určen pro porovnání řetězců.  
  
## <a name="see-also"></a>Viz také  
 [Národní prostředí](../c-runtime-library/locale.md)   
 [Zacházení s řetězci](../c-runtime-library/string-manipulation-crt.md)   
 [localeconv –](../c-runtime-library/reference/localeconv.md)   
 [_mbsnbcoll –, _mbsnbcoll_l –, _mbsnbicoll –, _mbsnbicoll_l –](../c-runtime-library/reference/mbsnbcoll-mbsnbcoll-l-mbsnbicoll-mbsnbicoll-l.md)   
 [setlocale –, _wsetlocale –](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [strcmp – wcscmp –, _mbscmp –](../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strncmp –, wcsncmp –, _mbsncmp –, _mbsncmp_l –](../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [_strnicmp –, _wcsnicmp –, _mbsnicmp –, _strnicmp_l –, _wcsnicmp_l –, _mbsnicmp_l –](../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strxfrm –, wcsxfrm –, _strxfrm_l –, _wcsxfrm_l –](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)