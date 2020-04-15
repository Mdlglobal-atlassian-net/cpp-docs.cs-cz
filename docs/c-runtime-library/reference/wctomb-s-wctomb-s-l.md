---
title: wctomb_s, _wctomb_s_l
ms.date: 4/2/2020
api_name:
- _wctomb_s_l
- wctomb_s
- _o__wctomb_s_l
- _o_wctomb_s
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 1ddc9a991f28c4a2ea491f3ddd04d78f6345e255
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367253"
---
# <a name="wctomb_s-_wctomb_s_l"></a>wctomb_s, _wctomb_s_l

Převede široký znak na odpovídající vícebajtový znak. Verze [wctomb, _wctomb_l](wctomb-wctomb-l.md) s vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*hodnota pRetValue*<br/>
Počet bajtů nebo kód označující výsledek.

*mbchar*<br/>
Adresa vícebajtového znaku.

*sizeInBytes*<br/>
Velikost vyrovnávací paměti *mbchar*.

*Wchar*<br/>
Široký charakter.

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu, kód chyby při selhání.

Chybové stavy

|*mbchar*|*sizeInBytes*|Návratová hodnota|*hodnota pRetValue*|
|--------------|-------------------|------------------|-----------------|
|**Null**|> 0|**EINVAL**|nezměněno|
|jakékoli|>**INT_MAX**|**EINVAL**|nezměněno|
|jakékoli|příliš malé|**EINVAL**|nezměněno|

Pokud dojde k některéz výše uvedených chybových stavů, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [parametru Validation](../../c-runtime-library/parameter-validation.md). Pokud je provádění povoleno pokračovat, **wctomb** vrátí **EINVAL** a nastaví **errno** na **EINVAL**.

## <a name="remarks"></a>Poznámky

Funkce **wctomb_s** převede svůj argument *wchar* na odpovídající vícebajtový znak a uloží výsledek na *mbchar*. Funkci můžete volat z libovolného místa v libovolném programu.

Pokud **wctomb_s** převede široký znak na vícebajtový znak, umístí počet bajtů (který není nikdy větší než **MB_CUR_MAX**) v širokém znaku do celého čísla, na které je odkazováno *hodnotou pRetValue*. Pokud *wchar* je znak null znak široký znak (L'\0'), **wctomb_s** výplní *pRetValue* s 1. Pokud je *cílový* ukazatel mbchar **null**, **wctomb_s** vloží 0 v *pRetValue*. Pokud převod není možné v aktuálním národním prostředí, **wctomb_s** vloží -1 v *pRetValue*.

**wctomb_s** používá aktuální národní prostředí pro informace závislé na národním prostředí; **_wctomb_s_l** je totožný s tím rozdílem, že místo toho používá národní prostředí předané. Další informace naleznete v [tématu Locale](../../c-runtime-library/locale.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**wctomb_s**|\<stdlib.h>|
|**_wctomb_s_l**|\<stdlib.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Tento program ilustruje chování **funkce wctomb.**

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

## <a name="see-also"></a>Viz také

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
