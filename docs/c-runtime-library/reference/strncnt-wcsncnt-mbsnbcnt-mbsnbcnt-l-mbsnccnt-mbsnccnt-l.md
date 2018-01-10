---
title: "_strncnt –, _wcsncnt –, _mbsnbcnt –, _mbsnbcnt_l –, _mbsnccnt –, _mbsnccnt_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mbsnbcnt_l
- _mbsnccnt
- _wcsncnt
- _strncnt
- _mbsnccnt_l
- _mbsnbcnt
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
- _mbsnbcnt
- wcsncnt
- _tcsnbcnt
- _mbsnccnt
- _ftcsnbcnt
- mbsnbcnt
- strncnt
- mbsnbcnt_l
- mbsnccnt_l
- mbsnccnt
- _strncnt
- _wcsncnt
dev_langs: C++
helpviewer_keywords:
- _strncnt function
- _mbsnbcnt function
- _mbsnbcnt_l function
- _mbsnccnt_l function
- mbsnbcnt_l function
- mbsnbcnt function
- tcsnbcnt function
- mbsnccnt_l function
- strncnt function
- _tcsnbcnt function
- mbsnccnt function
- wcsncnt function
- _mbsnccnt function
- _wcsncnt function
ms.assetid: 2a022e9e-a307-4acb-a66b-e56e5357f848
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 27c2d107da6c937705cacac770a50d912cadda84
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="strncnt-wcsncnt-mbsnbcnt-mbsnbcntl-mbsnccnt-mbsnccntl"></a>_strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l
Vrátí počet znaků nebo bajtů v rámci zadaného počtu.  
  
> [!IMPORTANT]
>  `_mbsnbcnt`, `_mbsnbcnt_l`, `_mbsnccnt`, a `_mbsnccnt_l` nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
size_t _strncnt(  
   const char *str,  
   size_t count  
);  
size_t _wcsncnt(  
   const wchar_t *str,  
   size_t count  
);  
size_t _mbsnbcnt(  
   const unsigned char *str,  
   size_t count   
);  
size_t _mbsnbcnt_l(  
   const unsigned char *str,  
   size_t count,  
   _locale_t locale  
);  
size_t _mbsnccnt(  
   const unsigned char *str,  
   size_t count  
);  
size_t _mbsnccnt_l(  
   const unsigned char *str,  
   size_t count,  
   _locale_t locale  
);  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `str`  
 Řetězec prověřit.  
  
 `count`  
 Počet znaků nebo bajtů v `str`.  
  
 `locale`  
 Národní prostředí použít.  
  
## <a name="return-value"></a>Návratová hodnota  
 `_mbsnbcnt`a `_mbsnbcnt_l` vrátí počet bajtů najít v prvním `count` vícebajtové znaky z `str`. `_mbsnccnt`a `_mbsnccnt_l` vrátí počet znaků, najít v prvním `count` bajtů `str`. Pokud je znak hodnoty NULL došlo před zkoumání `str` má dokončení vrátí počet bajtů nebo znaků, nalezeno před znak hodnoty NULL. Pokud `str` se skládá z méně než `count` znaků nebo bajtů, vrátí počet znaků nebo bajtů v řetězci. Pokud `count` je menší než nula, že budou vracet 0. V předchozích verzích se tyto funkce měl návratovou hodnotu typu `int` místo `size_t`.  
  
 `_strncnt`Vrátí počet znaků v prvním `count` bajtů řetězce jednobajtové `str`. `_wcsncnt`Vrátí počet znaků v prvním `count` široké znaky řetězce široká charakterová `str`.  
  
## <a name="remarks"></a>Poznámky  
 `_mbsnbcnt`a `_mbsnbcnt_l` počet bajtů najít v prvním `count` vícebajtové znaky z `str`. `_mbsnbcnt`a `_mbsnbcnt_l` nahradit `mtob` a mělo by se místě `mtob`.  
  
 `_mbsnccnt`a `_mbsnccnt_l` určený počet znaků najít v prvním `count` bajtů `str`. Pokud `_mbsnccnt` a `_mbsnccnt_l` stane s hodnotou NULL v druhé bajt dvoubajtové znakové, první bajt také se považuje za hodnotu NULL a není zahrnuta hodnota vrácená počtu. `_mbsnccnt`a `_mbsnccnt_l` nahradit `btom` a mělo by se místě `btom`.  
  
 Pokud `str` ukazatele null nebo je `count` je 0, tyto funkce vyvolat obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md), `errno` je nastaven na `EINVAL`, a funkce vrátí hodnotu 0.  
  
 Výstupní hodnota je ovlivňován nastavením `LC_CTYPE` kategorie nastavení národního prostředí; viz [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) Další informace. Verze tyto funkce bez `_l` příponu využívání aktuální národní prostředí pro toto chování závislých na národním prostředí, verze s `_l` příponu jsou shodné s tím rozdílem, že používají předaný v místo toho parametr národního prostředí. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|  
|-------------|--------------------------------------|--------------------|-----------------------|  
|`_tcsnbcnt`|`_strncnt`|`_mbsnbcnt`|`_wcsncnt`|  
|`_tcsnccnt`|`_strncnt`|`_mbsnbcnt`|`n/a`|  
|`_wcsncnt`|`n/a`|`n/a`|`_mbsnbcnt`|  
|`_wcsncnt`|`n/a`|`n/a`|`_mbsnccnt`|  
|`n/a`|`n/a`|`_mbsnbcnt_l`|`_mbsnccnt_l`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_mbsnbcnt`|\<Mbstring.h >|  
|`_mbsnbcnt_l`|\<Mbstring.h >|  
|`_mbsnccnt`|\<Mbstring.h >|  
|`_mbsnccnt_l`|\<Mbstring.h >|  
|`_strncnt`|\<Tchar.h >|  
|`_wcsncnt`|\<Tchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_mbsnbcnt.c  
  
#include  <mbstring.h>  
#include  <stdio.h>  
  
int main( void )  
{  
   unsigned char str[] = "This is a multibyte-character string.";  
   unsigned int char_count, byte_count;  
   char_count = _mbsnccnt( str, 10 );  
   byte_count = _mbsnbcnt( str, 10 );  
   if ( byte_count - char_count )  
      printf( "The first 10 characters contain %d multibyte characters\n", char_count );  
   else  
      printf( "The first 10 characters are single-byte.\n");  
}  
```  
  
## <a name="output"></a>Výstup  
  
```  
The first 10 characters are single-byte.  
```  
  
## <a name="see-also"></a>Viz také  
 [Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)   
 [Národní prostředí](../../c-runtime-library/locale.md)   
 [Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [_mbsnbcat, _mbsnbcat_l](../../c-runtime-library/reference/mbsnbcat-mbsnbcat-l.md)