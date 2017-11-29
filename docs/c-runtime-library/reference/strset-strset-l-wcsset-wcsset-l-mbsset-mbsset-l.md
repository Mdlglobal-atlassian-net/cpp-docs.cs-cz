---
title: "_strset –, _strset_l –, _wcsset –, _wcsset_l –, _mbsset –, _mbsset_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wcsset
- _mbsset
- _strset_l
- _strset
- _wcsset_l
- _mbsset_l
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
- mbsset
- _strset_l
- _mbsset
- _strset
- mbsset_l
- strset_l
- _wcsset
- _ftcsset
- wcsset_l
- _tcsset_l
- _mbsset_l
- _wcsset_l
- _fstrset
- _tcsset
dev_langs: C++
helpviewer_keywords:
- _wcsset_l function
- _tcsset function
- wcsset_l function
- _ftcsset function
- characters [C++], setting
- _strset function
- ftcsset function
- strings [C++], setting characters
- mbsset function
- tcsset_l function
- _fstrset function
- mbsset_l function
- strset_l function
- _wcsset function
- _mbsset function
- _mbsset_l function
- tcsset function
- _strset_l function
- fstrset function
- _tcsset_l function
ms.assetid: c42ded42-2ed9-4f06-a0a9-247ba305473a
caps.latest.revision: "31"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1c91c3ef160319db05b7a0bee3bcce55db7d771a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="strset-strsetl-wcsset-wcssetl-mbsset-mbssetl"></a>_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l
Nastaví znaky řetězce z znaku. Bezpečnější verze tyto funkce jsou k dispozici. v tématu [_strset_s –, _strset_s_l –, _wcsset_s –, _wcsset_s_l –, _mbsset_s –, _mbsset_s_l –](../../c-runtime-library/reference/strset-s-strset-s-l-wcsset-s-wcsset-s-l-mbsset-s-mbsset-s-l.md).  
  
> [!IMPORTANT]
>  `_mbsset`a `_mbsset_l` nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
char *_strset(  
   char *str,  
   int c   
);  
char *_strset_l(  
   char *str,  
   int c,  
   locale_t locale  
);  
wchar_t *_wcsset(  
   wchar_t *str,  
   wchar_t c   
);  
wchar_t *_wcsset_l(  
   wchar_t *str,  
   wchar_t c,  
   locale_t locale  
);  
unsigned char *_mbsset(  
   unsigned char *str,  
   unsigned int c   
);  
unsigned char *_mbsset_l(  
   unsigned char *str,  
   unsigned int c,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `str`  
 Řetězce ukončené hodnotou Null nastavit.  
  
 `c`  
 Nastavení znaků.  
  
 `locale`  
 Národní prostředí použít.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrací ukazatel na změněna řetězec.  
  
## <a name="remarks"></a>Poznámky  
 `_strset` Funkce nastaví všechny znaky (s výjimkou ukončující znak hodnoty null) `str` k `c`, převést na `char`. `_wcsset`a `_mbsset_l` jsou široká charakterová a vícebajtových znaků verze `_strset`, a datové typy argumentů a návratové hodnoty se liší podle toho. Tyto funkce chovají stejně jako jinak.  
  
 `_mbsset`ověří jeho parametry. Pokud `str` je ukazatel s hodnotou null, je vyvolána obslužná rutina neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění `_mbsset` vrátí `NULL` a nastaví `errno` k `EINVAL`. `_strset`a `_wcsset` neověřují jejich parametrů.  
  
 Výstupní hodnota je ovlivňován nastavením `LC_CTYPE` kategorie nastavení národního prostředí; viz [setlocale _wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) Další informace. Verze tyto funkce jsou identické, s tím rozdílem, že ty, které nejsou mít `_l` příponu použít aktuální národní prostředí a ty, které mají `_l` příponu, použijte parametr národního prostředí, který se předává v. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).  
  
> [!IMPORTANT]
>  Tato funkce může být zranitelný vůči hrozbám přetečení vyrovnávací paměti. Přetečení vyrovnávací paměti můžete použít pro útoky systému, protože může dojít k tomu bude vyplacena neoprávněně zvýšení úrovně oprávnění. Další informace najdete v tématu [zabraňující způsobí přetečení vyrovnávací paměti](http://msdn.microsoft.com/library/windows/desktop/ms717795).  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcsset`|`_strset`|`_mbsset`|`_wcsset`|  
|`_tcsset_l`|`_strset_l`|`_mbsset_l`|`_wcsset_l`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_strset`|\<String.h >|  
|`_strset_l`|\<Tchar.h >|  
|`_wcsset`|\<String.h > nebo \<wchar.h >|  
|`_wcsset_l`|\<Tchar.h >|  
|`_mbsset`, `_mbsset_l`|\<Mbstring.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_strset.c  
// compile with: /W3  
  
#include <string.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char string[] = "Fill the string with something.";  
   printf( "Before: %s\n", string );  
   _strset( string, '*' ); // C4996  
   // Note: _strset is deprecated; consider using _strset_s instead  
   printf( "After:  %s\n", string );  
}  
```  
  
```Output  
Before: Fill the string with something.  
After:  *******************************  
```  
  
## <a name="see-also"></a>Viz také  
 [Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)   
 [Národní prostředí](../../c-runtime-library/locale.md)   
 [Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [_mbsnbset –, _mbsnbset_l –](../../c-runtime-library/reference/mbsnbset-mbsnbset-l.md)   
 [memset –, wmemset –](../../c-runtime-library/reference/memset-wmemset.md)   
 [strcat – wcscat –, _mbscat –](../../c-runtime-library/reference/strcat-wcscat-mbscat.md)   
 [strcmp – wcscmp –, _mbscmp –](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strcpy – wcscpy –, _mbscpy –](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)   
 [_strnset –, _strnset_l –, _wcsnset –, _wcsnset_l –, _mbsnset –, _mbsnset_l –](../../c-runtime-library/reference/strnset-strnset-l-wcsnset-wcsnset-l-mbsnset-mbsnset-l.md)