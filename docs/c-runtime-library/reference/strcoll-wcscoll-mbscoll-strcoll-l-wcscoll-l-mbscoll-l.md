---
title: "strcoll –, wcscoll –, _mbscoll –, _strcoll_l –, _wcscoll_l –, _mbscoll_l | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- wcscoll
- _mbscoll
- _mbscoll_l
- strcoll
- _strcoll_l
- _wcscoll_l
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
- wcscoll
- _mbscoll
- _tcscoll
- _ftcscoll
dev_langs: C++
helpviewer_keywords:
- code pages, using for string comparisons
- mbscoll function
- wcscoll_l function
- ftcscoll function
- wcscoll function
- _strcoll_l function
- tcscoll function
- _ftcscoll function
- _tcscoll function
- _wcscoll_l function
- _mbscoll function
- strcoll_l function
- strcoll functions
- strings [C++], comparing by code page
ms.assetid: 900a7540-c7ec-4c2f-b292-7a85f63e3fe8
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ecb29e00a4baa5bd1ad36fe47bade09a8cc7f56f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="strcoll-wcscoll-mbscoll-strcolll-wcscolll-mbscolll"></a>strcoll, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l, _mbscoll_l
Porovnání řetězců pomocí aktuální národní prostředí nebo zadané kategorii lc_collate – převod stavu.  
  
> [!IMPORTANT]
>  `_mbscoll`a `_mbscoll_l` nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int strcoll(  
   const char *string1,  
   const char *string2   
);  
int wcscoll(  
   const wchar_t *string1,  
   const wchar_t *string2   
);  
int _mbscoll(  
   const unsigned char *string1,  
   const unsigned char *string2   
);  
int _strcoll_l(  
   const char *string1,  
   const char *string2,  
   _locale_t locale   
);  
int wcscoll_l(  
   const wchar_t *string1,  
   const wchar_t *string2,  
   _locale_t locale   
);  
int _mbscoll_l(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   _locale_t locale   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `string1`, `string2`  
 Řetězce ukončené hodnotou Null pro porovnání.  
  
 `locale`  
 Národní prostředí použít.  
  
## <a name="return-value"></a>Návratová hodnota  
 Každá z těchto funkcí vrátí hodnotu, která určuje vztah `string1` k `string2`, a to takto.  
  
|Návratová hodnota|Relace řetězec1 k řetězec2|  
|------------------|----------------------------------------|  
|< 0|`string1`menší než`string2`|  
|0|`string1`stejný jako`string2`|  
|> 0|`string1`větší než`string2`|  
  
 Každá z těchto funkcí vrátí `_NLSCMPERROR` na chybu. Chcete-li použít `_NLSCMPERROR`, zahrnout buď řetězec. H nebo MBSTRING. H. `wcscoll`může selhat, pokud buď `string1` nebo `string2` je NULL nebo obsahuje kódy široká charakterová mimo doménu pořadí řazení. Když dojde k chybě, `wcscoll` může nastavit `errno` k `EINVAL`. Zkontrolujte chybu na volání `wcscoll`, nastavte `errno` na hodnotu 0 a poté zkontrolujte `errno` po volání `wcscoll`.  
  
## <a name="remarks"></a>Poznámky  
 Každá z těchto funkcí provede malá a velká písmena porovnání `string1` a `string2` podle znakové stránky aktuálně používán. Tyto funkce by měly používat jenom v případě, že je rozdíl mezi znak nastavte pořadí a pořadí lexicographic znaků na aktuální stránce kódu a tento rozdíl je určen pro porovnání řetězců.  
  
 Všechny tyto funkce ověřit jejich parametrů. Pokud má jedna `string1` nebo `string2` je ukazatel s hodnotou null, nebo pokud `count` je větší než `INT_MAX`, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md) . Pokud je povoleno spuštění chcete-li pokračovat, tyto funkce vracejí `_NLSCMPERROR` a nastavte `errno` k `EINVAL`.  
  
 Porovnání dvou řetězců je operace závislých na národním prostředí, protože každé národní prostředí má jiná pravidla pro řazení znaků. Verze tyto funkce bez `_l` přípona použití aktuální vlákno národní prostředí pro toto chování závislých na národním prostředí; verze se `_l` příponu jsou stejné jako odpovídající funkce bez přípona s tím rozdílem, že používají národní prostředí předána jako parametr místo aktuální národní prostředí. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcscoll`|`strcoll`|`_mbscoll`|`wcscoll`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`strcoll`|\<String.h >|  
|`wcscoll`|\<wchar.h >, \<string.h >|  
|`_mbscoll`, `_mbscoll_l`|\<Mbstring.h >|  
|`_strcoll_l`|\<String.h >|  
|`_wcscoll_l`|\<wchar.h >, \<string.h >|  
  
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