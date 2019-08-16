---
title: wctomb, _wctomb_l
ms.date: 11/04/2016
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
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- wctomb
helpviewer_keywords:
- string conversion, wide characters
- wide characters, converting
- _wctomb_l function
- wctomb function
- wctomb_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 4a543f0e-5516-4d81-8ff2-3c5206f02ed5
ms.openlocfilehash: 6902ff925e49d894f70b0d7083b99388d5271d1d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500746"
---
# <a name="wctomb-_wctomb_l"></a>wctomb, _wctomb_l

Převést velký znak na odpovídající vícebajtový znak. K dispozici jsou bezpečnější verze těchto funkcí; viz [wctomb_s, _wctomb_s_l](wctomb-s-wctomb-s-l.md).

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
Adresa vícebajtového znaku.

*wchar*<br/>
Velký znak.

## <a name="return-value"></a>Návratová hodnota

Pokud **wctomb** převede velký znak na vícebajtový znak, vrátí počet bajtů (který není nikdy větší než **MB_CUR_MAX**) v rámci stejného znaku. Pokud je *WCHAR* znak nulového znaku (L ' \ 0 '), vrátí **wctomb** hodnotu 1. Pokud cílový ukazatel *mbchar* má **hodnotu null**, **wctomb** vrátí hodnotu 0. Pokud v aktuálním národním prostředí není převod možný, **wctomb** vrátí hodnotu-1 a **errno** je nastaven na **EILSEQ**.

## <a name="remarks"></a>Poznámky

Funkce **wctomb** převede svůj argument *WCHAR* na odpovídající vícebajtový znak a výsledek uloží na *mbchar*. Funkci lze volat z libovolného bodu v jakémkoli programu. **wctomb** používá aktuální národní prostředí pro jakékoli chování závislé na národním prostředí; **_wctomb_l** je shodná s **wctomb** s tím rozdílem, že místo toho používá národní prostředí předané. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

**wctomb** ověří své parametry. Pokud má Mbchar **hodnotu null**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, **errno** je nastaven na **EINVAL** a funkce vrátí-1.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**wctomb**|\<stdlib.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Tento program ilustruje chování funkce wctomb.

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

## <a name="see-also"></a>Viz také:

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
