---
title: wctomb_s, _wctomb_s_l
ms.date: 11/04/2016
api_name:
- _wctomb_s_l
- wctomb_s
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wctomb_s
- _wctomb_s_l
helpviewer_keywords:
- wctomb_s function
- wctomb_s_l function
- string conversion, wide characters
- wide characters, converting
- _wctomb_s_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 7e94a888-deed-4dbd-b5e9-d4a0455538b8
ms.openlocfilehash: 329724ca0196e07397d4f0337a2bf0aa2db05c84
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957894"
---
# <a name="wctomb_s-_wctomb_s_l"></a>wctomb_s, _wctomb_s_l

Převede velký znak na odpovídající vícebajtový znak. Verze [wctomb, _wctomb_l](wctomb-wctomb-l.md) s vylepšeními zabezpečení, jak je popsáno v [části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
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

### <a name="parameters"></a>Parametry

*pRetValue*<br/>
Počet bajtů nebo kód indikující výsledek.

*mbchar*<br/>
Adresa vícebajtového znaku.

*sizeInBytes*<br/>
Velikost *mbchar*vyrovnávací paměti.

*wchar*<br/>
Velký znak.

*jazyka*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu, chybový kód při selhání.

Chybové stavy

|*mbchar*|*sizeInBytes*|Návratová hodnota|*pRetValue*|
|--------------|-------------------|------------------|-----------------|
|**NULL**|>0|**EINVAL**|Neupraveno|
|Jakýmikoli|>**INT_MAX**|**EINVAL**|Neupraveno|
|Jakýmikoli|příliš malý|**EINVAL**|Neupraveno|

Pokud dojde k některé z výše uvedených chybových podmínek, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, **wctomb** vrátí **EINVAL** a nastaví **errno** na **EINVAL**.

## <a name="remarks"></a>Poznámky

Funkce **wctomb_s** převede svůj argument *WCHAR* na odpovídající vícebajtový znak a výsledek uloží na *mbchar*. Funkci lze volat z libovolného bodu v jakémkoli programu.

Pokud **wctomb_s** převede celý znak na vícebajtový znak, vrátí počet bajtů (který není nikdy větší než **MB_CUR_MAX**) v rámci celého znaku na celé číslo, na které odkazuje *pRetValue*. Pokud je *WCHAR* znak nulového znaku (L ' \ 0 '), **Wctomb_s** vyplní *pRetValue* hodnotou 1. Pokud cílový ukazatel *mbchar* má **hodnotu null**, **wctomb_s** vloží 0 v *pRetValue*. Pokud v aktuálním národním prostředí není převod možný, **wctomb_s** vloží-1 do *pRetValue*.

**wctomb_s** používá aktuální národní prostředí pro informace závislé na národním prostředí; **_wctomb_s_l** je totožný s tím rozdílem, že místo toho používá národní prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**wctomb_s**|\<stdlib.h>|
|**_wctomb_s_l**|\<stdlib.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Tento program ilustruje chování funkce **wctomb** .

```cpp
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

## <a name="see-also"></a>Viz také:

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
