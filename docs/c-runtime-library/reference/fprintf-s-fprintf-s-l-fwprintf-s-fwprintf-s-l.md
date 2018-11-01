---
title: fprintf_s, _fprintf_s_l, fwprintf_s, _fwprintf_s_l
ms.date: 11/04/2016
apiname:
- _fprintf_s_l
- fwprintf_s
- fprintf_s
- _fwprintf_s_l
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
apitype: DLLExport
f1_keywords:
- _ftprintf_s
- fprintf_s
- fwprintf_s
helpviewer_keywords:
- ftprintf_s_l function
- ftprintf_s function
- _fprintf_s_l function
- _ftprintf_s function
- _ftprintf_s_l function
- fwprintf_s_l function
- fwprintf_s function
- fprintf_s_l function
- fprintf_s function
- _fwprintf_s_l function
- print formatted data to streams
ms.assetid: 16067c3c-69ce-472a-8272-9aadf1f5beed
ms.openlocfilehash: 05886dc4ce7de771749f157913a222b6b01a5c5a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50639423"
---
# <a name="fprintfs-fprintfsl-fwprintfs-fwprintfsl"></a>fprintf_s, _fprintf_s_l, fwprintf_s, _fwprintf_s_l

Tisk formátovaných dat do datového proudu. Jde o verzích [fprintf _fprintf_l –, fwprintf – _fwprintf_l –](fprintf-fprintf-l-fwprintf-fwprintf-l.md) s rozšířeními zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
int fprintf_s(
   FILE *stream,
   const char *format [,
   argument_list ]
);
int _fprintf_s_l(
   FILE *stream,
   const char *format,
   locale_t locale [,
   argument_list ]
);
int fwprintf_s(
   FILE *stream,
   const wchar_t *format [,
   argument_list ]
);
int _fwprintf_s_l(
   FILE *stream,
   const wchar_t *format,
   locale_t locale [,
   argument_list ]
);
```

### <a name="parameters"></a>Parametry

*Stream*<br/>
Ukazatel na **souboru** struktury.

*Formát*<br/>
Řetězec řízení formátu

*argument_list*<br/>
Volitelné argumenty na řetězec formátu.

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

**fprintf_s –** vrátí počet zapsaných bajtů. **fwprintf_s –** vrátí počet širokých znaků, které jsou zapsány. Každá z těchto funkcí vrací zápornou hodnotu. místo toho při výskytu chyby výstupu.

## <a name="remarks"></a>Poznámky

**fprintf_s –** formátuje a vytiskne řadu znaků a hodnot do výstupu *stream*. Každý argument v *argument_list* (pokud existuje) je převeden a uložen podle odpovídající specifikace formátu v *formátu*. *Formátu* používá argument [formátování syntaxe specifikace pro funkce printf a wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

**fwprintf_s –** je verze širokého znaku **fprintf_s –**; v **fwprintf_s –**, *formátu* je širokoznaký řetězec. Tyto funkce chovají stejně jako v případě, že datový proud je otevřen v režimu ANSI. **fprintf_s –** aktuálně nepodporuje výstup do datového proudu UNICODE.

Verze těchto funkcí s **_l** přípona jsou stejné s tím rozdílem, že používají parametr národního prostředí namísto aktuálního národního prostředí předaného.

> [!IMPORTANT]
> Ujistěte se, že *formátu* není uživatelem definovaný řetězec.

Podobně jako nezabezpečené verze (viz [fprintf _fprintf_l –, fwprintf – _fwprintf_l –](fprintf-fprintf-l-fwprintf-fwprintf-l.md)), tyto funkce ověřují své parametry a vyvolají obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md), pokud buď *stream* nebo *formátu* je ukazatel s hodnotou null. Samotný formátovací řetězec je také ověřován. Pokud neexistují žádné neznámé nebo chybně zformulované formátovací specifikátory, tyto funkce generují výjimku neplatného parametru. Ve všech případech, pokud provádění může pokračovat, vrátí funkce hodnotu -1 a nastaví **errno** k **EINVAL**. Zobrazit [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o těchto a dalších chybových kódech.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ftprintf_s –**|**fprintf_s –**|**fprintf_s –**|**fwprintf_s –**|
|**_ftprintf_s_l –**|**_fprintf_s_l**|**_fprintf_s_l**|**_fwprintf_s_l**|

Další informace najdete v tématu [specifikace formátu](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fprintf_s –**, **_fprintf_s_l –**|\<stdio.h>|
|**fwprintf_s –**, **_fwprintf_s_l –**|\<stdio.h > nebo \<wchar.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_fprintf_s.c
// This program uses fprintf_s to format various
// data and print it to the file named FPRINTF_S.OUT. It
// then displays FPRINTF_S.OUT on the screen using the system
// function to invoke the operating-system TYPE command.

#include <stdio.h>
#include <process.h>

FILE *stream;

int main( void )
{
   int    i = 10;
   double fp = 1.5;
   char   s[] = "this is a string";
   char   c = '\n';

   fopen_s( &stream, "fprintf_s.out", "w" );
   fprintf_s( stream, "%s%c", s, c );
   fprintf_s( stream, "%d\n", i );
   fprintf_s( stream, "%f\n", fp );
   fclose( stream );
   system( "type fprintf_s.out" );
}
```

```Output
this is a string
10
1.500000
```

## <a name="see-also"></a>Viz také:

[Stream vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[_cprintf, _cprintf_l, _cwprintf, _cwprintf_l](cprintf-cprintf-l-cwprintf-cwprintf-l.md)<br/>
[fscanf, _fscanf_l, fwscanf, _fwscanf_l](fscanf-fscanf-l-fwscanf-fwscanf-l.md)<br/>
[sprintf _sprintf_l –, swprintf, _swprintf_l –, \__swprintf_l –](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
