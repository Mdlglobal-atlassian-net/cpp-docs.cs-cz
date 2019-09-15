---
title: fprintf, _fprintf_l, fwprintf, _fwprintf_l
ms.date: 11/04/2016
api_name:
- fwprintf
- fprintf
- _fprintf_l
- _fwprintf_l
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
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 1a296b8ac97a7f20a3834814c1ca3b7319720148
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956990"
---
# <a name="fprintf-_fprintf_l-fwprintf-_fwprintf_l"></a>fprintf, _fprintf_l, fwprintf, _fwprintf_l

Tisk formátovaných dat do datového proudu. K dispozici jsou bezpečnější verze těchto funkcí; viz [fprintf_s, _fprintf_s_l, fwprintf_s, _fwprintf_s_l](fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md).

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
Ukazatel na strukturu **souborů** .

*format*<br/>
Řetězec řízení formátu

*argument*<br/>
Volitelné argumenty

*jazyka*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

**fprintf –** vrátí počet zapsaných bajtů. **fwprintf** vrátí počet zapsaných velkých znaků. Každá z těchto funkcí vrací zápornou hodnotu, pokud dojde k chybě výstupu. Pokud má *datový proud* nebo *Formát* **hodnotu null**, tyto funkce vyvolají obslužnou rutinu neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí funkce hodnotu-1 a nastaví **errno** na **EINVAL**. Formátovací řetězec není kontrolován pro platné formátovací znaky, protože je použit **fprintf_s** nebo **fwprintf_s**.

Další informace o těchto a dalších chybových kódech naleznete v tématech [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) .

## <a name="remarks"></a>Poznámky

**fprintf –** formátuje a tiskne řadu znaků a hodnot do výstupního *datového proudu*. Každý *argument* funkce (pokud existuje) je převeden a výstup podle odpovídající specifikace formátu ve *formátu*. Pro **fprintf –** má argument *Format* stejnou syntaxi a používá ho v **printf**.

**fwprintf** je **fprintf –** verze s velkým znakem; ve **fwprintf**je *Formát* řetězec s velkým znakem. Tyto funkce se chovají stejně, pokud je datový proud otevřen v režimu ANSI. **fprintf –** v současné době nepodporuje výstup do datového proudu Unicode.

Verze těchto funkcí s příponou **_l** jsou stejné s tím rozdílem, že používají předaný parametr národního prostředí namísto aktuálního národního prostředí vlákna.

> [!IMPORTANT]
> Ujistěte se, že *Formát* není uživatelem definovaný řetězec.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ftprintf**|**fprintf –**|**fprintf –**|**fwprintf**|
|**_ftprintf_l**|**_fprintf_l**|**_fprintf_l**|**_fwprintf_l**|

Další informace najdete v tématu [specifikace formátu](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fprintf**, **_fprintf_l**|\<stdio.h>|
|**fwprintf**, **_fwprintf_l**|\<stdio. h > nebo \<WCHAR. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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

[Vstup/výstup datového proudu](../../c-runtime-library/stream-i-o.md)<br/>
[_cprintf, _cprintf_l, _cwprintf, _cwprintf_l](cprintf-cprintf-l-cwprintf-cwprintf-l.md)<br/>
[fscanf, _fscanf_l, fwscanf, _fwscanf_l](fscanf-fscanf-l-fwscanf-fwscanf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[Syntaxe specifikace formátu: funkce printf a wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)<br/>
