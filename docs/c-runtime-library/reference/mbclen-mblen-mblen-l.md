---
title: _mbclen, mblen, _mblen_l, _mbclen_l
description: Popisuje funkce _mbclen, mblen, _mblen_l a _mbclen_l knihovny C (Microsoft C Runtime Library).
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 76e8771898d8baa65f275304a9aefdcaeeb5b3bd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341126"
---
# <a name="_mbclen-mblen-_mblen_l-_mbclen_l"></a>_mbclen, mblen, _mblen_l, _mbclen_l

Získá délku a určuje platnost vícebajtového znaku.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime. Další informace naleznete v tématu [funkce CRT, které nejsou podporovány v aplikacích univerzální platformy Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*C*\
Vícebajtový znak.

*mbstr*\
Adresa vícebajtové bajtové sekvence.

*Počet*\
Počet bajtů ke kontrole.

*Národní prostředí*\
Národní prostředí použít.

## <a name="return-value"></a>Návratová hodnota

**_mbclen** a **_mbclen_l** vrátí 1 nebo 2 podle délky vícebajtového znaku *c*. Funkce vždy vrátí 1 pro UTF-8, zda *c* je vícebajt nebo ne. Neexistuje žádná chyba vrátit **_mbclen**.

Pokud *mbstr* není **NULL**, **mblen** a **_mblen_l** vrátí délku vícebajtového znaku v bajtů. **Funkce mblen** a **_mblen_l** fungují správně na UTF-8 a mohou vrátit hodnotu mezi 1 a 3. Pokud *mbstr* je **NULL** (nebo odkazuje na znak null široký znak), **mblen** a **_mblen_l** vrátí 0. Objekt, na který *mbstr* odkazuje, musí tvořit platný vícebajtový znak v rámci znaků *prvního počtu* nebo **mblen** a **_mblen_l** vrátí -1.

## <a name="remarks"></a>Poznámky

Funkce **_mbclen** vrátí délku vícebajtového znaku *c*v bajtech . Pokud *c* neukazuje na úvodní bajt vícebajtového znaku (jak je určeno implicitním voláním [_ismbblead](ismbblead-ismbblead-l.md), výsledek **_mbclen** je nepředvídatelný.

**Mblen** vrátí délku v bajtů *mbstr,* pokud se jedná o platný vícebajtový znak. Určuje také platnost vícebajtového znaku přidruženého ke znakové stránce. **mblen** zkoumá *počet* nebo méně bajtů obsažených v *mbstr*, ale ne více než **MB_CUR_MAX** bajtů.

Výstupní hodnota je ovlivněna nastavením **kategorie LC_CTYPE** národního prostředí. Verze těchto funkcí bez **přípony _l** pro toto chování závislé na národním prostředí používají aktuální národní prostředí. **_l** suffixed verze se chovají stejně, ale místo toho používají parametr národního prostředí. Další informace naleznete [v tématu setlocale](setlocale-wsetlocale.md) a [Locale](../../c-runtime-library/locale.md).

**_mbclen**, **_mblen_l**a **_mbclen_l** jsou specifické pro společnost Microsoft, nikoli součástí knihovny Standard C. Nedoporučujeme je používat tam, kde chcete přenosný kód. Pro kompatibilitu se standardem C použijte **mblen** nebo **mbrlen.**

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tclen**|Mapuje na makro nebo vsazenou funkci.|**_mbclen**|Mapuje na makro nebo vsazenou funkci.|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_mbclen**|\<mbstring.h>|
|**mblen**|\<stdlib.h>|
|**_mblen_l**|\<stdlib.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

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
[Národní prostředí](../../c-runtime-library/locale.md)\
[Interpretace vícebajtových sekvencí](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)\
[_mbccpy, _mbccpy_l](mbccpy-mbccpy-l.md)\
[mbrlen (Mbrlen)](mbrlen.md)\
[strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)
