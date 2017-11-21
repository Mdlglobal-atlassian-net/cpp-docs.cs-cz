---
title: "_mbsnbset –, _mbsnbset_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mbsnbset
- _mbsnbset_l
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
- mbsnbset
- mbsnbset_l
- _mbsnbset
- _mbsnbset_l
dev_langs: C++
helpviewer_keywords:
- tcsnset function
- _tcsnset_l function
- _mbsnbset function
- _tcsnset function
- _mbsnbset_l function
- mbsnbset_l function
- tcsnset_l function
- mbsnbset function
ms.assetid: 8e46ef75-9a56-42d2-a522-a08450c67c19
caps.latest.revision: "24"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d1b0fb832c9bcfd254dacaab604de865dac454ba
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="mbsnbset-mbsnbsetl"></a>_mbsnbset, _mbsnbset_l
Nastaví první `n` bajtů řetězce vícebajtových znaků pro zadaný znak. Bezpečnější verze tyto funkce jsou k dispozici. v tématu [_mbsnbset_s –, _mbsnbset_s_l –](../../c-runtime-library/reference/mbsnbset-s-mbsnbset-s-l.md).  
  
> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
unsigned char *_mbsnbset(  
   unsigned char *str,  
   unsigned int c,  
   size_t count   
);  
unsigned char *_mbsnbset_l(  
   unsigned char *str,  
   unsigned int c,  
   size_t count,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `str`  
 Řetězec, který má být změněn.  
  
 `c`  
 Nastavení jednobajtové nebo vícebajtových znaků.  
  
 `count`  
 Počet bajtů, které mají být nastavena.  
  
 `locale`  
 Národní prostředí použít.  
  
## <a name="return-value"></a>Návratová hodnota  
 `_mbsnbset`vrací ukazatel na změněna řetězec.  
  
## <a name="remarks"></a>Poznámky  
 `_mbsnbset` a `_mbsnbset_l` funkce nastavovat maximálně první `count` bajtů `str` k `c`. Pokud `count` je větší než délka `str`, délka `str` se používá místo `count`. Pokud `c` je vícebajtových znaků a nelze ji nastavit zcela do posledního bajtu určeného `count`, poslední bajt doplněno prázdný znak. `_mbsnbset`a `_mbsnbset_l` neumístí ukončující null na konci `str`.  
  
 `_mbsnbset`a `_mbsnbset_l` je podobná `_mbsnset`kromě toho, že nastaví `count` bajtů místo `count` znaků `c`.  
  
 Pokud `str` je `NULL` nebo `count` rovná nule, tato funkce vygeneruje výjimku neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění `errno` je nastaven na `EINVAL` a funkce vrátí hodnotu `NULL`. Navíc pokud `c` není platný vícebajtových znaků `errno` je nastaven na `EINVAL` a místo toho používá mezeru.  
  
 Výstupní hodnota je ovlivňován nastavením `LC_CTYPE` kategorie nastavení národního prostředí; viz [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) Další informace. `_mbsnbset` Verze této funkce používá aktuální národní prostředí pro toto chování závislých na národním prostředí; `_mbsnbset_l` verze je stejná s tím rozdílem, že ji, použijte parametr národního prostředí předaná místo. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).  
  
 **Poznámka k zabezpečení** toto rozhraní API způsobuje potenciální hrozbu způsobené problém přetečení vyrovnávací paměti. Přetečení vyrovnávací paměti problémy jsou často metodu systému útoku, výsledkem bude vyplacena neoprávněně zvýšení úrovně oprávnění. Další informace najdete v tématu [zabraňující způsobí přetečení vyrovnávací paměti](http://msdn.microsoft.com/library/windows/desktop/ms717795).  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tcsnset`|`_strnset`|`_mbsnbset`|`_wcsnset`|  
|`_tcsnset_l`|`_strnset_l`|`_mbsnbset_l`|`_wcsnset_l`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_mbsnbset`|\<Mbstring.h >|  
|`_mbsnbset_l`|\<Mbstring.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_mbsnbset.c  
// compile with: /W3  
#include <mbstring.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char string[15] = "This is a test";  
   /* Set not more than 4 bytes of string to be *'s */  
   printf( "Before: %s\n", string );  
   _mbsnbset( string, '*', 4 ); // C4996  
   // Note; _mbsnbset is deprecated; consider _mbsnbset_s  
   printf( "After:  %s\n", string );  
}  
```  
  
## <a name="output"></a>Výstup  
  
```  
Before: This is a test  
After:  **** is a test  
```  
  
## <a name="see-also"></a>Viz také  
 [Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)   
 [_mbsnbcat –, _mbsnbcat_l –](../../c-runtime-library/reference/mbsnbcat-mbsnbcat-l.md)   
 [_strnset –, _strnset_l –, _wcsnset –, _wcsnset_l –, _mbsnset –, _mbsnset_l –](../../c-runtime-library/reference/strnset-strnset-l-wcsnset-wcsnset-l-mbsnset-mbsnset-l.md)   
 [_strset –, _strset_l –, _wcsset –, _wcsset_l –, _mbsset –, _mbsset_l –](../../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)