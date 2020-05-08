---
title: _mbclen, mblen, _mblen_l, _mbclen_l
description: Popisuje funkce knihovny CRT (Microsoft C Runtime Library) _mbclen, mblen, _mblen_l a _mbclen_l.
ms.date: 4/2/2020
api_name:
- _mbclen
- mblen
- _mblen_l
- _mbclen_l
- _o__mbclen
- _o__mbclen_l
- _o__mblen_l
- _o_mblen
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mblen
- ftclen
- _mbclen
- _mbclen_l
- tclen
- _ftclen
- _tclen
- mbclen
helpviewer_keywords:
- tclen function
- _mblen_l function
- _tclen function
- mblen_l function
- _mbclen function
- _mbclen_l function
- mbclen function
- mblen function
ms.assetid: d5eb92a0-b7a3-464a-aaf7-9890a8e3ed70
ms.openlocfilehash: b004babc9e7c82d25cd52ec036c3061c99b5f367
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914360"
---
# <a name="_mbclen-mblen-_mblen_l-_mbclen_l"></a>_mbclen, mblen, _mblen_l, _mbclen_l

Získá délku a určí platnost vícebajtového znaku.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
size_t _mbclen(
   const unsigned char *c
);
size_t _mbclen_l(
   unsigned char const* c,
   _locale_t locale
);
int mblen(
   const char *mbstr,
   size_t count
);
int _mblen_l(
   const char *mbstr,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*r*\
Vícebajtový znak.

*mbstr*\
Adresa bajtové sekvence vícebajtových znaků.

*výpočtu*\
Počet bajtů, které mají být zkontrolovány.

*jazyka*\
Národní prostředí, které se má použít.

## <a name="return-value"></a>Návratová hodnota

**_mbclen** a **_mbclen_l** vrací 1 nebo 2 podle délky vícebajtového znaku *c*. Funkce vždycky vrátí 1 pro UTF-8, ať už je *c* vícebajtový nebo ne. Pro **_mbclen**se nevrátila žádná chyba.

Pokud *mbstr* není **null**, **mblen** a **_mblen_l** vrátí délku vícebajtového znaku (v bajtech). Funkce **mblen** a **_mblen_l** fungují správně v kódování UTF-8 a mohou vracet hodnotu mezi 1 a 3. Pokud *mbstr* má Mbstr **hodnotu null** (nebo odkazuje na znak null s velkým znakem), **mblen** a **_mblen_l** vrátí 0. Objekt, na který odkazuje *mbstr* , musí tvořit platný vícebajtový znak v rámci prvních znaků *Count* nebo **mblen** a **_mblen_l** Return-1.

## <a name="remarks"></a>Poznámky

Funkce **_mbclen** vrací délku vícebajtového znaku *c*v bajtech. Pokud *c* neodkazuje na vedoucí bajt vícebajtového znaku (jak je určeno implicitním voláním [_ismbblead](ismbblead-ismbblead-l.md), výsledek **_mbclen** je nepředvídatelné.

**mblen** vrátí délku v bajtech *mbstr* , pokud se jedná o platný vícebajtový znak. Také určuje, že je k znakové stránce přiřazena Vícebajtová znaková doba. **mblen** prověřuje *počet* nebo méně bajtů obsažených v *mbstr*, ale ne více než **MB_CUR_MAX** bajtů.

Výstupní hodnota je ovlivněna nastavením kategorie **LC_CTYPE** národního prostředí. Verze těchto funkcí bez přípony **_l** používají aktuální národní prostředí pro toto chování závislé na národním prostředí. Verze **_l** s příponou se chovají stejně, ale používají předaný parametr národního prostředí. Další informace naleznete v tématu [setlocale](setlocale-wsetlocale.md) and [locale](../../c-runtime-library/locale.md).

**_mbclen**, **_mblen_l**a **_Mbclen_l** jsou specifické pro společnost Microsoft, nikoli součástí standardní knihovny jazyka C. Nedoporučujeme je používat tam, kde chcete použít přenosný kód. V případě kompatibility Standard C použijte místo toho **mblen** nebo **mbrlen** .

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tclen**|Mapuje se na makro nebo vloženou funkci.|**_mbclen**|Mapuje se na makro nebo vloženou funkci.|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_mbclen**|\<Mbstring. h>|
|**mblen**|\<Stdlib. h>|
|**_mblen_l**|\<Stdlib. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_mblen.c
/* illustrates the behavior of the mblen function
*/

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
    int      i;
    char    *pmbc = (char *)malloc( sizeof( char ) );
    wchar_t  wc   = L'a';

    printf( "Convert wide character to multibyte character:\n" );
    wctomb_s( &i, pmbc, sizeof(char), wc );
    printf( "   Characters converted: %u\n", i );
    printf( "   Multibyte character: %x\n\n", *pmbc );

    i = mblen( pmbc, MB_CUR_MAX );
    printf( "Length in bytes of multibyte character %x: %u\n", *pmbc, i );

    pmbc = NULL;
    i = mblen( pmbc, MB_CUR_MAX );
    printf( "Length in bytes of NULL multibyte character %x: %u\n", pmbc, i );
}
```

```Output
Convert wide character to multibyte character:
   Characters converted: 1
   Multibyte character: 61

Length in bytes of multibyte character 61: 1
Length in bytes of NULL multibyte character 0: 0
```

## <a name="see-also"></a>Viz také

[Klasifikace znaků](../../c-runtime-library/character-classification.md)\
[Jazyka](../../c-runtime-library/locale.md)\
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)\
[_mbccpy _mbccpy_l](mbccpy-mbccpy-l.md)\
[mbrlen](mbrlen.md)\
[strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)
