---
title: wctomb_s, _wctomb_s_l
ms.date: 11/04/2016
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
helpviewer_keywords:
- wctomb_s function
- wctomb_s_l function
- string conversion, wide characters
- wide characters, converting
- _wctomb_s_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 7e94a888-deed-4dbd-b5e9-d4a0455538b8
ms.openlocfilehash: 08e8cb0ddaac342682776600fd0fd8b3d26b8953
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188482"
---
# <a name="wctombs-wctombsl"></a>wctomb_s, _wctomb_s_l

Převede široký znak na odpovídající vícebajtový znak. Verze [wctomb – _wctomb_l –](wctomb-wctomb-l.md) s rozšířeními zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Počet bajtů nebo kód označující výsledek.

*mbchar*<br/>
Adresa vícebajtového znaku.

*sizeInBytes*<br/>
Velikost vyrovnávací paměti *mbchar*.

*wchar*<br/>
Široký znak.

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu, při selhání kód chyby.

Chybové podmínky

|*mbchar*|*sizeInBytes*|Návratová hodnota|*pRetValue*|
|--------------|-------------------|------------------|-----------------|
|**NULL**|>0|**EINVAL**|Nezměněno|
|Všechny|>**INT_MAX**|**EINVAL**|Nezměněno|
|Všechny|příliš malá|**EINVAL**|Nezměněno|

Pokud dojde k některé z výše uvedených chybové stavy, vyvolán obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, **wctomb –** vrátí **EINVAL** a nastaví **errno** k **EINVAL**.

## <a name="remarks"></a>Poznámky

**Wctomb_s –** funkce převede její *wchar* argument odpovídající vícebajtový znak a uloží výsledek v *mbchar*. Funkce můžete volat z libovolného bodu v libovolné aplikaci.

Pokud **wctomb_s –** převede širokého znaku na vícebajtový znak, uloží je počet bajtů (který se nikdy větší než **MB_CUR_MAX**) v širokého znaku do celé číslo, na které odkazuje *pRetValue*. Pokud *wchar* je prázdný znak širokého znaku (L '\0'), **wctomb_s –** vyplní *pRetValue* s 1. Pokud se ukazatel na cílový *mbchar* je **NULL**, **wctomb_s –** umístí 0 *pRetValue*. Pokud převod není v aktuálním národním prostředí, **wctomb_s –** převádí na hodnotu -1 *pRetValue*.

**wctomb_s –** používá aktuální národní prostředí pro informace závislé na národním prostředí. **_wctomb_s_l –** je stejná s tím rozdílem, že používá národní prostředí předané. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**wctomb_s**|\<stdlib.h>|
|**_wctomb_s_l**|\<stdlib.h>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Tento program ukazuje chování **wctomb –** funkce.

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
[WideCharToMultiByte](/windows/desktop/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
