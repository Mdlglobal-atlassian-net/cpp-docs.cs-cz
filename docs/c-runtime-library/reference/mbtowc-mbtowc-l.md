---
title: mbtowc _mbtowc_l – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- mbtowc
- _mbtowc_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- mbtowc
dev_langs:
- C++
helpviewer_keywords:
- mbtowc function
- _mbtowc_l function
- mbtowc_l function
ms.assetid: dfd1c8a7-e73a-4307-9353-53b70b45d4d1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b6600706690dea3573f8eb1aa47f68b592b3bff1
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43200304"
---
# <a name="mbtowc-mbtowcl"></a>mbtowc, _mbtowc_l

Převeďte vícebajtový znak na odpovídající širokého znaku.

## <a name="syntax"></a>Syntaxe

```C
int mbtowc(
   wchar_t *wchar,
   const char *mbchar,
   size_t count
);
int _mbtowc_l(
   wchar_t *wchar,
   const char *mbchar,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*wchar*<br/>
Adresa širokého znaku (typ **wchar_t**).

*mbchar*<br/>
Adresa sekvence bajtů (vícebajtového znaku).

*Počet*<br/>
Počet bajtů ke kontrole.

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Pokud **mbchar** není **NULL** a, pokud objekt, který *mbchar* odkazuje na formulářích je platný vícebajtový znak **mbtowc** vrátí délku v bajtech vícebajtového znaku. Pokud *mbchar* je **NULL** nebo objekt, který odkazuje na prázdný znak širokého znaku (L '\0'), funkce vrátí 0. Pokud objekt, který *mbchar* odkazuje na netvoří platné vícebajtové znaky v prvních *počet* znaků, vrátí hodnotu -1.

## <a name="remarks"></a>Poznámky

**Mbtowc** funkce převede *počet* nebo menší počet bajtů, na které odkazuje *mbchar*, pokud *mbchar* není **NULL**, odpovídající široký znak. **mbtowc** uloží výsledný širokého znaku v *wchar,* Pokud *wchar* není **NULL**. **mbtowc** nezkoumá více než **MB_CUR_MAX** bajtů. **mbtowc** používá aktuální národní prostředí pro chování závislé na národním prostředí **_mbtowc_l –** je stejná s tím rozdílem, že používá národní prostředí předané. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**mbtowc**|\<stdlib.h>|
|**_mbtowc_l**|\<stdlib.h>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Příklad

```C
// crt_mbtowc.c
// Illustrates the behavior of the mbtowc function

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
    int      i;
    char    *pmbc    = (char *)malloc( sizeof( char ) );
    wchar_t  wc      = L'a';
    wchar_t *pwcnull = NULL;
    wchar_t *pwc     = (wchar_t *)malloc( sizeof( wchar_t ) );
    printf( "Convert a wide character to multibyte character:\n" );
    wctomb_s( &i, pmbc, sizeof(char), wc );
    printf( "  Characters converted: %u\n", i );
    printf( "  Multibyte character: %x\n\n", *pmbc );

    printf( "Convert multibyte character back to a wide "
            "character:\n" );
    i = mbtowc( pwc, pmbc, MB_CUR_MAX );
    printf( "   Bytes converted: %u\n", i );
    printf( "   Wide character: %x\n\n", *pwc );
    printf( "Attempt to convert when target is NULL\n" );
    printf( "   returns the length of the multibyte character:\n" );
    i = mbtowc( pwcnull, pmbc, MB_CUR_MAX );
    printf( "   Length of multibyte character: %u\n\n", i );

    printf( "Attempt to convert a NULL pointer to a" );
    printf( " wide character:\n" );
    pmbc = NULL;
    i = mbtowc( pwc, pmbc, MB_CUR_MAX );
    printf( "   Bytes converted: %u\n", i );
}
```

```Output
Convert a wide character to multibyte character:
   Characters converted: 1
   Multibyte character: 61

Convert multibyte character back to a wide character:
   Bytes converted: 1
   Wide character: 61

Attempt to convert when target is NULL
   returns the length of the multibyte character:
   Length of multibyte character: 1

Attempt to convert a NULL pointer to a wide character:
   Bytes converted: 0
```

## <a name="see-also"></a>Viz také:

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[MultiByteToWideChar](/windows/desktop/api/stringapiset/nf-stringapiset-multibytetowidechar)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
