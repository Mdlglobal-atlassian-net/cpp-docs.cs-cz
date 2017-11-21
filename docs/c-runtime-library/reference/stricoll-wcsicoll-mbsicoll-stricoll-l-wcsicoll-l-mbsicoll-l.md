---
title: "_stricoll –, _wcsicoll –, _mbsicoll –, _stricoll_l –, _wcsicoll_l, _mbsicoll_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mbsicoll_l
- _stricoll_l
- _mbsicoll
- _wcsicoll_l
- _wcsicoll
- _stricoll
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- stricoll
- _stricoll
- _wcsicoll
- mbsicoll_l
- _mbsicoll
- _ftcsicoll
- wcsicoll_l
- _tcsicoll
- mbsicoll
- stricoll_l
dev_langs: C++
helpviewer_keywords:
- code pages, using for string comparisons
- _ftcsicoll function
- _mbsicoll_l function
- _mbsicoll function
- mbsicoll function
- stricoll function
- tcsicoll function
- string comparison [C++], culture-specific
- _tcsicoll function
- _stricoll function
- _stricoll_l function
- _wcsicoll function
- mbsicoll_l function
- stricoll_l function
- strings [C++], comparing by code page
- ftcsicoll function
ms.assetid: 8ec93016-5a49-49d2-930f-721566661d82
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9508eacf1e361f3e87353f7ceb6dc00270982212
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="stricoll-wcsicoll-mbsicoll-stricolll-wcsicolll-mbsicolll"></a>_stricoll, _wcsicoll, _mbsicoll, _stricoll_l, _wcsicoll_l, _mbsicoll_l
Porovnání řetězců pomocí informace specifické pro národní prostředí.  
  
> [!IMPORTANT]
>  `_mbsicoll`a `_mbsicoll_l` nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _stricoll(  
   const char *string1,  
   const char *string2   
);  
int _wcsicoll(  
   const wchar_t *string1,  
   const wchar_t *string2   
);  
int _mbsicoll(  
   const unsigned char *string1,  
   const unsigned char *string2   
);  
int _stricoll_l(  
   const char *string1,  
   const char *string2,  
   _locale_t locale  
);  
int _wcsicoll_l(  
   const wchar_t *string1,  
   const wchar_t *string2,  
   _locale_t locale  
);  
int _mbsicoll_l(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `string1, string2`  
 Řetězce ukončené hodnotou Null pro porovnání.  
  
 `locale`  
 Národní prostředí, které se má použít  
  
## <a name="return-value"></a>Návratová hodnota  
 Každá z těchto funkcí vrátí hodnotu, která určuje vztah `string1` k `string2`, a to takto.  
  
|Návratová hodnota|Relace řetězec1 k řetězec2|  
|------------------|----------------------------------------|  
|< 0|`string1`menší než`string2`|  
|0|`string1`stejný jako`string2`|  
|> 0|`string1`větší než`string2`|  
|`_NLSCMPERROR`|Došlo k chybě.|  
  
 Každá z těchto funkcí vrátí `_NLSCMPERROR`. Chcete-li použít `_NLSCMPERROR`, zahrnout buď `STRING.H` nebo `MBSTRING.H`. `_wcsicoll`může selhat, pokud buď `string1` nebo `string2` obsahuje kódy široká charakterová mimo doménu pořadí řazení. Když dojde k chybě, `_wcsicoll` může nastavit `errno` k `EINVAL`. Zkontrolujte chybu na volání `_wcsicoll`, nastavte `errno` na hodnotu 0 a poté zkontrolujte `errno` po volání `_wcsicoll`.  
  
## <a name="remarks"></a>Poznámky  
 Každá z těchto funkcí provede velká a malá písmena porovnání `string1` a `string2` podle znakové stránky aktuálně používán. Tyto funkce by měly používat jenom v případě, že je rozdíl mezi znak nastavte pořadí a pořadí lexicographic znaků na aktuální stránce kódu a tento rozdíl je určen pro porovnání řetězců.  
  
 `_stricmp`se liší od `_stricoll` v tom, že `_stricmp` je ovlivňován porovnání `LC_CTYPE`, zatímco `_stricoll` na základě porovnání `LC_CTYPE` a `LC_COLLATE` kategorie národního prostředí. Další informace o `LC_COLLATE` kategorie, najdete v části [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) a [kategorie národního prostředí](../../c-runtime-library/locale-categories.md). Verze tyto funkce bez `_l` přípona použití aktuální národní prostředí; verze s `_l` příponu jsou shodné s tím rozdílem, že používají místo předaná národní prostředí. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).  
  
 Všechny tyto funkce ověřit jejich parametrů. Pokud má jedna `string1` nebo `string2` jsou `NULL` ukazatele, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění chcete-li pokračovat, tyto funkce vracejí `_NLSCMPERROR` a nastavte `errno` k `EINVAL`.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcsicoll`|`_stricoll`|`_mbsicoll`|`_wcsicoll`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_stricoll`, `_stricoll_l`|\<String.h >|  
|`_wcsicoll`, `_wcsicoll_l`|\<wchar.h >, \<string.h >|  
|`_mbsicoll`, `_mbsicoll_l`|\<Mbstring.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Národní prostředí](../../c-runtime-library/locale.md)   
 [Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)   
 [strcoll – funkce](../../c-runtime-library/strcoll-functions.md)   
 [localeconv –](../../c-runtime-library/reference/localeconv.md)   
 [_mbsnbcoll –, _mbsnbcoll_l –, _mbsnbicoll –, _mbsnbicoll_l –](../../c-runtime-library/reference/mbsnbcoll-mbsnbcoll-l-mbsnbicoll-mbsnbicoll-l.md)   
 [setlocale –, _wsetlocale –](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [strcmp – wcscmp –, _mbscmp –](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [_stricmp –, _wcsicmp –, _mbsicmp –, _stricmp_l –, _wcsicmp_l –, _mbsicmp_l –](../../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)   
 [strncmp –, wcsncmp –, _mbsncmp –, _mbsncmp_l –](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [_strnicmp –, _wcsnicmp –, _mbsnicmp –, _strnicmp_l –, _wcsnicmp_l –, _mbsnicmp_l –](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strxfrm –, wcsxfrm –, _strxfrm_l –, _wcsxfrm_l –](../../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)