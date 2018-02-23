---
title: "wctomb –, _wctomb_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _wctomb_l
- wctomb
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
- wctomb
dev_langs:
- C++
helpviewer_keywords:
- string conversion, wide characters
- wide characters, converting
- _wctomb_l function
- wctomb function
- wctomb_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 4a543f0e-5516-4d81-8ff2-3c5206f02ed5
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: adb05340bee89ff86c4ab30a61f32ca53c71519b
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="wctomb-wctombl"></a>wctomb, _wctomb_l
Široká znaková převeďte na odpovídající vícebajtových znaků. Bezpečnější verze tyto funkce jsou k dispozici. v tématu [wctomb_s –, _wctomb_s_l –](../../c-runtime-library/reference/wctomb-s-wctomb-s-l.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int wctomb(  
   char *mbchar,  
   wchar_t wchar   
);  
int _wctomb_l(  
   char *mbchar,  
   wchar_t wchar,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `mbchar`  
 Adresa vícebajtových znaků.  
  
 `wchar`  
 Široká znaková.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud `wctomb` převede široká znaková k vícebajtových znaků, vrátí počet bajtů (které se nikdy větší než `MB_CUR_MAX`) široké znakem. Pokud `wchar` je znak hodnoty null široká charakterová (L '\0'), `wctomb` vrátí hodnotu 1. Pokud cílový ukazatel `mbchar` má hodnotu NULL, `wctomb` vrátí hodnotu 0. Pokud převod není pro aktuální prostředí `wctomb` vrátí hodnotu -1 a `errno` je nastaven na `EILSEQ`.  
  
## <a name="remarks"></a>Poznámky  
 `wctomb` Funkce převede jeho `wchar` argument odpovídající vícebajtových znaků a ukládá výsledek v `mbchar`. Funkce můžete volat z libovolného bodu v libovolné aplikaci. `wctomb` používá aktuální národní prostředí pro chování všech závislých na národním prostředí; `_wctomb_l` je stejný jako `wctomb` s tím rozdílem, že používá národní prostředí předaná místo. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).  
  
 `wctomb` ověří jeho parametry. Pokud `mbchar` je `NULL`, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění `errno` je nastaven na `EINVAL` a funkce vrátí hodnotu -1.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`wctomb`|\<stdlib.h>|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
 Tento program znázorňuje chování wctomb – funkce.  
  
```  
// crt_wctomb.cpp  
// compile with: /W3  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   int i;  
   wchar_t wc = L'a';  
   char *pmb = (char *)malloc( MB_CUR_MAX );  
  
   printf( "Convert a wide character:\n" );  
   i = wctomb( pmb, wc ); // C4996  
   // Note: wctomb is deprecated; consider using wctomb_s  
   printf( "   Characters converted: %u\n", i );  
   printf( "   Multibyte character: %.1s\n\n", pmb );  
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