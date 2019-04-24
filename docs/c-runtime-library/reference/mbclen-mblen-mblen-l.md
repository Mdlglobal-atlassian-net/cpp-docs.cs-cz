---
title: _mbclen, mblen –, _mblen_l –, _mbclen_l
ms.date: 01/22/2019
apiname:
- _mbclen
- mblen
- _mblen_l
- _mbclen_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: b7888b0b8c87a632dcbb63f54ade11080c7a309a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62156782"
---
# <a name="mbclen-mblen-mblenl-mbclenl"></a>_mbclen, mblen –, _mblen_l –, _mbclen_l

Získá délku a určí platnost vícebajtového znaku.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*c*<br/>
Vícebajtový znak.

*mbstr*<br/>
Adresa vícebajtové znakové sekvence.

*Počet*<br/>
Počet bajtů ke kontrole.

*Národní prostředí*<br/>
Národní prostředí.

## <a name="return-value"></a>Návratová hodnota

**_mbclen** vrátí hodnotu 1 nebo 2, podle toho, zda vícebajtový znak *c* je 1 nebo 2 bajty dlouhý. Neexistuje žádná chybová zpráva pro vrácení **_mbclen**. Pokud *mbstr* není **NULL**, **mblen –** vrátí délku v bajtech vícebajtového znaku. Pokud *mbstr* je **NULL** nebo odkazuje na prázdný znak širokého znaku, **mblen –** vrátí hodnotu 0. Pokud objekt, který *mbstr* odkazuje na nemá formu platné vícebajtové znaky v prvních *počet* znaků, **mblen –** vrátí hodnotu -1.

## <a name="remarks"></a>Poznámky

**_Mbclen** funkce vrátí délku v bajtech vícebajtového znaku *c*. Pokud *c* neodkazuje na úvodní bajt vícebajtového znaku, jako je určeno implicitním voláním **_ismbblead**, výsledek **_mbclen** nepředvídatelné.

**mblen –** vrátí délku v bajtech *mbstr* , pokud je platný vícebajtový znak a určuje platnost vícebajtového znaku zakončeného přidružené znakovou stránku. **mblen –** prozkoumá *počet* nebo menší počet bajtů obsažených v *mbstr*, ale ne více než **MB_CUR_MAX** bajtů.

Výstupní hodnota je ovlivněna **LC_CTYPE** nastavením kategorie národního prostředí; viz [setlocale](setlocale-wsetlocale.md) Další informace. Verze těchto funkcí bez **_l** přípona používají aktuální národní prostředí pro toto chování závislé na národním prostředí. **_L** příponami verzích se chová stejně, ale používají Předaný parametr národního prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tclen**|Mapuje se na makro nebo vloženou funkci|**_mbclen**|Mapuje se na makro nebo vloženou funkci|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_mbclen**|\<Mbstring.h >|
|**mblen –**|\<stdlib.h>|
|**_mblen_l**|\<stdlib.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také:

[Klasifikace znaků](../../c-runtime-library/character-classification.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbccpy, _mbccpy_l](mbccpy-mbccpy-l.md)<br/>
[strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)<br/>
