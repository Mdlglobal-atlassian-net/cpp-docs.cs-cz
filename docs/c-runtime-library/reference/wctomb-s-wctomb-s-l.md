---
title: "wctomb_s –, _wctomb_s_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _wctomb_s_l
- wctomb_s
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- wctomb_s
- _wctomb_s_l
dev_langs:
- C++
helpviewer_keywords:
- wctomb_s function
- wctomb_s_l function
- string conversion, wide characters
- wide characters, converting
- _wctomb_s_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 7e94a888-deed-4dbd-b5e9-d4a0455538b8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3025340d4af81f20fd086d07058ac820828dda75
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="wctombs-wctombsl"></a>wctomb_s, _wctomb_s_l
Široká znaková převede na odpovídající vícebajtových znaků. Verzi [wctomb –, _wctomb_l –](../../c-runtime-library/reference/wctomb-wctomb-l.md) vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
errno_t wctomb_s(  
   int *pRetValue,  
   char *mbchar,  
   size_t sizeInBytes,  
   wchar_t wchar   
);  
errno_t _wctomb_s_l(  
   int *pRetValue,  
   char *mbchar,  
   size_t sizeInBytes,  
   wchar_t wchar,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [out] `pRetValue`  
 Počet bajtů nebo kód udávající výsledek.  
  
 [out] `mbchar`  
 Adresa vícebajtových znaků.  
  
 [in] `sizeInBytes`  
 Velikost vyrovnávací paměti `mbchar`.  
  
 [in] `wchar`  
 Široká znaková.  
  
 [in] `locale`  
 Národní prostředí, které se má použít  
  
## <a name="return-value"></a>Návratová hodnota  
 Nula v případě úspěchu, kód chyby při selhání.  
  
 Chybové stavy  
  
|`mbchar`|`sizeInBytes`|Návratová hodnota|`pRetValue`|  
|--------------|-------------------|------------------|-----------------|  
|`NULL`|>0|`EINVAL`|nedojde ke změně|  
|všechny|>`INT_MAX`|`EINVAL`|nedojde ke změně|  
|všechny|příliš malá|`EINVAL`|nedojde ke změně|  
  
 Pokud dojde k některé z výše uvedených podmínek chyba, je obslužná rutina neplatný parametr vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění `wctomb` vrátí `EINVAL` a nastaví `errno` k `EINVAL`.  
  
## <a name="remarks"></a>Poznámky  
 `wctomb_s` Funkce převede jeho `wchar` argument odpovídající vícebajtových znaků a ukládá výsledek v `mbchar`. Funkce můžete volat z libovolného bodu v libovolné aplikaci.  
  
 Pokud `wctomb_s` převede široká znaková k vícebajtových znaků, uloží je počet bajtů (které se nikdy větší než `MB_CUR_MAX`) v široká znaková do celé číslo, na kterou odkazuje `pRetValue`. Pokud `wchar` je znak hodnoty null široká charakterová (L '\0'), `wctomb_s` doplní `pRetValue` s 1. Pokud cílový ukazatel `mbchar` má hodnotu NULL, `wctomb_s` vloží 0 `pRetValue`. Pokud převod není pro aktuální prostředí `wctomb_s` převádí na hodnotu -1 `pRetValue`.  
  
 `wctomb_s` používá aktuální národní prostředí informace závislých na národním prostředí; `_wctomb_s_l` se shoduje s tím rozdílem, že používá národní prostředí předaná místo. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`wctomb_s`|\<stdlib.h>|  
|`_wctomb_s_l`|\<stdlib.h>|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
 Tento program znázorňuje chování `wctomb` funkce.  
  
```  
// crt_wctomb_s.cpp  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
    int i;  
    wchar_t wc = L'a';  
    char *pmb = (char *)malloc( MB_CUR_MAX );  
  
    printf_s( "Convert a wide character:\n" );  
    wctomb_s( &i, pmb, MB_CUR_MAX, wc );  
    printf_s( "   Characters converted: %u\n", i );  
    printf_s( "   Multibyte character: %.1s\n\n", pmb );  
}  
```  
  
```Output  
Convert a wide character:  
   Characters converted: 1  
   Multibyte character: a  
```  
  
## <a name="see-also"></a>Viz také  
 [Převod dat](../../c-runtime-library/data-conversion.md)   
 [Národní prostředí](../../c-runtime-library/locale.md)   
 [_mbclen, mblen, _mblen_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
 [mbstowcs, _mbstowcs_l](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)   
 [mbtowc, _mbtowc_l](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [wcstombs, _wcstombs_l](../../c-runtime-library/reference/wcstombs-wcstombs-l.md)   
 [WideCharToMultiByte](http://msdn.microsoft.com/library/windows/desktop/dd374130)