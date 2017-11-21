---
title: "_strncoll –, _wcsncoll –, _mbsncoll –, _strncoll_l –, _wcsncoll_l –, _mbsncoll_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _strncoll
- _mbsncoll_l
- _wcsncoll
- _wcsncoll_l
- _mbsncoll
- _strncoll_l
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
- mbsncoll_l
- strncoll
- _wcsncoll
- _tcsnccoll
- _ftcsnccoll
- wcsncoll
- _mbsncoll
- wcsncoll_l
- strncoll_l
- _ftcsncoll
- _strncoll
- _tcsncoll
- mbsncoll
dev_langs: C++
helpviewer_keywords:
- _strncoll_l function
- code pages, using for string comparisons
- _strncoll function
- _mbsncoll function
- ftcsncoll function
- strncoll function
- _ftcsncoll function
- strncoll_l function
- wcsncoll function
- mbsncoll function
- _tcsncoll function
- _tcsnccoll function
- wcsncoll_l function
- tcsnccoll function
- mbsncoll_l function
- _mbsncoll_l function
- tcsncoll function
- _wcsncoll function
- strings [C++], comparing by code page
- _ftcsnccoll function
- ftcsnccoll function
- _wcsncoll_l function
ms.assetid: e659a5a4-8afe-4033-8e72-17ffd4bdd8e9
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 36c802c5406d4f142e4902ad75a7621f5a23ed70
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="strncoll-wcsncoll-mbsncoll-strncolll-wcsncolll-mbsncolll"></a>_strncoll, _wcsncoll, _mbsncoll, _strncoll_l, _wcsncoll_l, _mbsncoll_l
Porovnání řetězců pomocí informace specifické pro národní prostředí.  
  
> [!IMPORTANT]
>  `_mbsncoll`a `_mbsncoll_l` nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _strncoll(  
   const char *string1,  
   const char *string2,  
   size_t count   
);  
int _wcsncoll(  
   const wchar_t *string1,  
   const wchar_t *string2,  
   size_t count   
);  
int _mbsncoll(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   size_t count   
);  
int _strncoll_l(  
   const char *string1,  
   const char *string2,  
   size_t count,  
   _locale_t locale  
);  
int _wcsncoll_l(  
   const wchar_t *string1,  
   const wchar_t *string2,  
   size_t count,  
   _locale_t locale  
);  
int _mbsncoll_l(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   size_t count,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `string1, string2`  
 Řetězce ukončené hodnotou Null pro porovnání.  
  
 `count`  
 Počet znaků k porovnání.  
  
 `locale`  
 Národní prostředí, které se má použít  
  
## <a name="return-value"></a>Návratová hodnota  
 Každá z těchto funkcí vrátí hodnotu, která určuje vztah podřetězce `string1` a `string2`, a to takto.  
  
|Návratová hodnota|Relace řetězec1 k řetězec2|  
|------------------|----------------------------------------|  
|< 0|`string1`je menší než `string2`.|  
|0|Funkce `string1` je shodná s funkcí `string2`.|  
|> 0|`string1`je větší než `string2`.|  
  
 Každá z těchto funkcí vrátí `_NLSCMPERROR`. Chcete-li použít `_NLSCMPERROR`, zahrnout STRING.h nebo MBSTRING.h. `_wcsncoll`může selhat, pokud buď `string1` nebo `string2` obsahuje široká charakterová kódy, které jsou mimo doménu pořadí řazení. Když dojde k chybě, `_wcsncoll` může nastavit `errno` k `EINVAL`. Zkontrolujte chybu na volání `_wcsncoll`, nastavte `errno` na hodnotu 0 a poté zkontrolujte `errno` po zavolání metody `_wcsncoll`.  
  
## <a name="remarks"></a>Poznámky  
 Každá z těchto funkcí provede malá a velká písmena porovnání první `count` znaky v `string1` a `string2`, podle znakové stránky, která je aktuálně používán. Pomocí těchto funkcí jenom v případě, že je rozdíl mezi pořadí sady znaků a pořadí lexicographic znaků v znakové stránky, a pokud tento rozdíl je určen pro porovnání řetězců. Znakové sady pořadí je závislých na národním prostředí. Verze tyto funkce, které nemají `_l` použijte příponu aktuální národní prostředí, ale verze, které mají `_l` národní prostředí, je předaná používat příponu. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).  
  
 Všechny tyto funkce ověřit jejich parametrů. Pokud má jedna `string1` nebo `string2` je ukazatel s hodnotou null, nebo `count` je větší než `INT_MAX`, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění chcete-li pokračovat, tyto funkce vracejí `_NLSCMPERROR` a nastavte `errno` k `EINVAL`.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcsnccoll`|`_strncoll`|`_mbsncoll`|`_wcsncoll`|  
|`_tcsncoll`|`_strncoll`|[_mbsnbcoll –](../../c-runtime-library/reference/mbsnbcoll-mbsnbcoll-l-mbsnbicoll-mbsnbicoll-l.md)|`_wcsncoll`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_strncoll`, `_strncoll_l`|\<String.h >|  
|`_wcsncoll`, `_wcsncoll_l`|\<wchar.h > nebo \<string.h >|  
|`_mbsncoll`, `_mbsncoll_l`|\<Mbstring.h >|  
  
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