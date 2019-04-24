---
title: fprintf, _fprintf_l, fwprintf, _fwprintf_l
ms.date: 11/04/2016
apiname:
- fwprintf
- fprintf
- _fprintf_l
- _fwprintf_l
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
- fprintf
- fwprintf
- _ftprintf
helpviewer_keywords:
- _fwprintf_l function
- fprintf function
- fprintf_l function
- _fprintf_l function
- _ftprintf function
- fwprintf function
- ftprintf_l function
- ftprintf function
- _ftprintf_l function
- print formatted data to streams
- fwprintf_l function
ms.assetid: 34a87e1c-6e4d-4d48-a611-58314dd4dc4b
ms.openlocfilehash: d84ef50e6fd522e393bb87664fb1eb47f3d32bb4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62333193"
---
# <a name="fprintf-fprintfl-fwprintf-fwprintfl"></a>fprintf, _fprintf_l, fwprintf, _fwprintf_l

Tisk formátovaných dat do datového proudu. Bezpečnější verze těchto funkcí jsou k dispozici. Zobrazit [fprintf_s – _fprintf_s_l –, fwprintf_s – _fwprintf_s_l –](fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md).

## <a name="syntax"></a>Syntaxe

```C
int fprintf(
   FILE *stream,
   const char *format [,
   argument ]...
);
int _fprintf_l(
   FILE *stream,
   const char *format,
   locale_t locale [,
   argument ]...
);
int fwprintf(
   FILE *stream,
   const wchar_t *format [,
   argument ]...
);
int _fwprintf_l(
   FILE *stream,
   const wchar_t *format,
   locale_t locale [,
   argument ]...
);
```

### <a name="parameters"></a>Parametry

*stream*<br/>
Ukazatel na **souboru** struktury.

*Formát*<br/>
Řetězec řízení formátu

*argument*<br/>
Volitelné argumenty

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

**fprintf** vrátí počet zapsaných bajtů. **fwprintf –** vrátí počet širokých znaků, které jsou zapsány. Každá z těchto funkcí vrací zápornou hodnotu. místo toho při výskytu chyby výstupu. Pokud *stream* nebo *formátu* je **NULL**, tyto funkce vyvolají obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, vrátí funkce hodnotu -1 a nastaví **errno** k **EINVAL**. Formátovací řetězec není kontroluje platnost znaků formátování je to, jestli používáte **fprintf_s –** nebo **fwprintf_s –**.

Zobrazit [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o těchto a dalších chybových kódech.

## <a name="remarks"></a>Poznámky

**fprintf** formátuje a vytiskne řadu znaků a hodnot do výstupu *stream*. Každá funkce *argument* (pokud existuje) je převeden a uložen podle odpovídající specifikace formátu v *formátu*. Pro **fprintf**, *formátu* argument má stejnou syntaxi a použití, který má v **printf**.

**fwprintf –** je verze širokého znaku **fprintf**; v **fwprintf –**, *formátu* je širokoznaký řetězec. Tyto funkce chovají stejně jako v případě, že datový proud je otevřen v režimu ANSI. **fprintf** aktuálně nepodporuje výstup do datového proudu UNICODE.

Verze těchto funkcí s **_l** přípona jsou stejné s tím rozdílem, že používají parametr národního prostředí předaného namísto aktuálního národní prostředí pro vlákno.

> [!IMPORTANT]
> Ujistěte se, že *formátu* není uživatelem definovaný řetězec.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ftprintf**|**fprintf**|**fprintf**|**fwprintf**|
|**_ftprintf_l**|**_fprintf_l**|**_fprintf_l**|**_fwprintf_l**|

Další informace najdete v tématu [specifikace formátu](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fprintf**, **_fprintf_l**|\<stdio.h>|
|**fwprintf**, **_fwprintf_l**|\<stdio.h > nebo \<wchar.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_fprintf.c
/* This program uses fprintf to format various
* data and print it to the file named FPRINTF.OUT. It
* then displays FPRINTF.OUT on the screen using the system
* function to invoke the operating-system TYPE command.
*/

#include <stdio.h>
#include <process.h>

FILE *stream;

int main( void )
{
   int    i = 10;
   double fp = 1.5;
   char   s[] = "this is a string";
   char   c = '\n';

   fopen_s( &stream, "fprintf.out", "w" );
   fprintf( stream, "%s%c", s, c );
   fprintf( stream, "%d\n", i );
   fprintf( stream, "%f\n", fp );
   fclose( stream );
   system( "type fprintf.out" );
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
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[Syntaxe specifikace formátu: funkce printf a wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)<br/>
