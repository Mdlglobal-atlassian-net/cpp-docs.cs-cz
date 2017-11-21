---
title: "_strninc –, _wcsninc –, _mbsninc –, _mbsninc_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mbsninc
- _mbsninc_l
- _wcsninc
- _strninc
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
apitype: DLLExport
f1_keywords:
- strninc
- wcsninc
- mbsninc_l
- _strninc
- _tcsninc
- mbsninc
- _mbsninc_l
- _ftcsninc
- _wcsninc
- _mbsninc
dev_langs: C++
helpviewer_keywords:
- _mbsninc_l function
- mbsninc function
- _strninc function
- tcsninc function
- wcsninc function
- _mbsninc function
- strninc function
- _wcsninc function
- mbsninc_l function
- _tcsninc function
ms.assetid: 6caace64-f9e4-48c0-afa8-ea51824ad723
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 37bf361f9be420f2f2d54ae073a37afb1016f700
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="strninc-wcsninc-mbsninc-mbsnincl"></a>_strninc, _wcsninc, _mbsninc, _mbsninc_l
Posune ukazatel řetězec podle `n` znaků.  
  
> [!IMPORTANT]
>  `_mbsninc`a `_mbsninc_l` nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
char *_strninc(  
   const char *str,  
   size_t count   
);  
wchar_t *_wcsninc(  
   const wchar_t *str,  
   size_t count   
);  
unsigned char *_mbsninc(  
   const unsigned char *str,  
   size_t count   
);  
unsigned char *_mbsninc(  
   const unsigned char *str,  
   size_t count,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `str`  
 Zdrojový řetězec.  
  
 `count`  
 Počet znaků se zvýší ukazatel řetězec.  
  
 `locale`  
 Národní prostředí použít.  
  
## <a name="return-value"></a>Návratová hodnota  
 Všechny tyto rutiny vrátí ukazatel na `str` po `str` byla zvýšena pomocí `count` znaků nebo `NULL` Pokud je zadaný ukazatel `NULL`. Pokud `count` je větší než nebo rovno počet znaků v `str`, výsledkem nedefinovaný.  
  
## <a name="remarks"></a>Poznámky  
 `_mbsninc` Funkce přírůstcích `str` podle `count` více-bajtové znaky. `_mbsninc`rozpozná vícebajtových znaků pořadí podle [vícebajtové znakové stránky](../../c-runtime-library/code-pages.md) aktuálně používán.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tcsninc`|`_strninc`|`_mbsninc`|`_wcsninc`|  
  
 `_strninc`a `_wcsninc` jsou jedním znaková řetězec a verze široká charakterová řetězec `_mbsninc`. `_wcsninc`a `_strninc` jsou k dispozici pouze pro toto mapování a v opačném případě by se neměla používat. Další informace najdete v tématu [použití mapování obecného textu](../../c-runtime-library/using-generic-text-mappings.md) a [mapování obecného textu](../../c-runtime-library/generic-text-mappings.md).  
  
 `_mbsninc_l`se shoduje s tím rozdílem, že používá parametr národního prostředí předaná místo. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_mbsninc`|\<Mbstring.h >|  
|`_mbsninc_l`|\<Mbstring.h >|  
|`_strninc`|\<Tchar.h >|  
|`_wcsninc`|\<Tchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)   
 [Národní prostředí](../../c-runtime-library/locale.md)   
 [Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [_strdec –, _wcsdec –, _mbsdec, _mbsdec_l –](../../c-runtime-library/reference/strdec-wcsdec-mbsdec-mbsdec-l.md)   
 [_strinc –, _wcsinc –, _mbsinc, _mbsinc_l –](../../c-runtime-library/reference/strinc-wcsinc-mbsinc-mbsinc-l.md)   
 [_strnextc –, _wcsnextc –, _mbsnextc –, _mbsnextc_l –](../../c-runtime-library/reference/strnextc-wcsnextc-mbsnextc-mbsnextc-l.md)