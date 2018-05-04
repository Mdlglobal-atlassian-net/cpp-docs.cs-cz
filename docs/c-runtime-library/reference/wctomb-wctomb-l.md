---
title: wctomb –, _wctomb_l – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e756ea23e32ffc9b164ccbe1a68b9fc987fe7b59
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="wctomb-wctombl"></a>wctomb, _wctomb_l

Široká znaková převeďte na odpovídající vícebajtových znaků. Bezpečnější verze tyto funkce jsou k dispozici. v tématu [wctomb_s –, _wctomb_s_l –](wctomb-s-wctomb-s-l.md).

## <a name="syntax"></a>Syntaxe

```C
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

### <a name="parameters"></a>Parametry

*mbchar*<br/>
Adresa vícebajtových znaků.

*wchar*<br/>
Široká znaková.

## <a name="return-value"></a>Návratová hodnota

Pokud **wctomb –** převede široká znaková k vícebajtových znaků, vrátí počet bajtů (které se nikdy větší než **mb_cur_max –**) široké znakem. Pokud *wchar* je znak hodnoty null široká charakterová (L '\0'), **wctomb –** vrátí hodnotu 1. Pokud cílový ukazatel *mbchar* má hodnotu NULL, **wctomb –** vrátí hodnotu 0. Pokud převod není pro aktuální prostředí **wctomb –** vrátí hodnotu -1 a **errno** je nastaven na **eilseq –**.

## <a name="remarks"></a>Poznámky

**Wctomb –** funkce převede jeho *wchar* argument odpovídající vícebajtových znaků a ukládá výsledek v *mbchar*. Funkce můžete volat z libovolného bodu v libovolné aplikaci. **wctomb –** používá aktuální národní prostředí pro chování všech závislých na národním prostředí; **_wctomb_l –** je stejný jako **wctomb –** s tím rozdílem, že používá národní prostředí předaná místo. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).

**wctomb –** ověří jeho parametry. Pokud *mbchar* je **NULL**, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění **errno** je nastaven na **einval –** a funkce vrátí hodnotu -1.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**wctomb –**|\<stdlib.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Tento program znázorňuje chování wctomb – funkce.

```cpp
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

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[WideCharToMultiByte](http://msdn.microsoft.com/library/windows/desktop/dd374130)<br/>
