---
title: fprintf_s –, _fprintf_s_l –, fwprintf_s –, _fwprintf_s_l – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ea8e9d28a960149d0f199b090daa98e76049f291
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32404214"
---
# <a name="fprintfs-fprintfsl-fwprintfs-fwprintfsl"></a>fprintf_s, _fprintf_s_l, fwprintf_s, _fwprintf_s_l

Tisk formátovaných dat do datového proudu. Toto jsou verze [fprintf, _fprintf_l –, fwprintf –, _fwprintf_l –](fprintf-fprintf-l-fwprintf-fwprintf-l.md) vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*Datový proud*<br/>
Ukazatel na **souboru** struktura.

*Formát*<br/>
Řetězec řízení formátu

*argument_list*<br/>
Nepovinné argumenty řetězce formátu.

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

**fprintf_s –** vrátí počet zapsaných bajtů. **fwprintf_s –** vrátí počet široké znaky zapsána. Každá z těchto funkcí vrátí zápornou hodnotu. místo toho při výskytu chyby výstupu.

## <a name="remarks"></a>Poznámky

**fprintf_s –** naformátuje a vytiskne řady znaků a hodnot pro výstup *datového proudu*. Každý argument v *argument_list* (pokud existuje) je převeden a výstup podle odpovídající specifikaci formátu v *formátu*. *Formátu* používá argument [formátu syntaxe specifikace pro funkce printf a wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

**fwprintf_s –** je verze široká charakterová **fprintf_s –**; v **fwprintf_s –**, *formát* je široká charakterová řetězec. Tyto funkce chovají stejně jako datový proud se při otevření v režimu ANSI. **fprintf_s –** nepodporuje aktuálně výstup do proudu kódování UNICODE.

Verze tyto funkce s **_l** příponu jsou shodné s tím rozdílem, že používají parametr národního prostředí předaná místo aktuální národní prostředí.

> [!IMPORTANT]
> Ujistěte se, že *formát* není řetězec definovaný uživatelem.

Jako verze nezabezpečeného (najdete v části [fprintf, _fprintf_l –, fwprintf –, _fwprintf_l –](fprintf-fprintf-l-fwprintf-fwprintf-l.md)), tyto funkce ověřit jejich parametrů a vyvolat obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md), pokud má jedna *datového proudu* nebo *formát* je ukazatel s hodnotou null. Formátovací řetězec se také byl ověřen. Pokud neexistují žádné neznámá nebo chybně vytvořen. formátování specifikátory, tyto funkce generování výjimek neplatný parametr. Ve všech případech, pokud chcete pokračovat, je povoleno spuštění funkce vrátí hodnotu -1 a nastavte **errno** k **einval –**. V tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o těchto a dalších kódy chyb.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ftprintf_s –**|**fprintf_s –**|**fprintf_s –**|**fwprintf_s –**|
|**_ftprintf_s_l –**|**_fprintf_s_l**|**_fprintf_s_l**|**_fwprintf_s_l**|

Další informace najdete v tématu [specifikace formátu](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fprintf_s –**, **_fprintf_s_l –**|\<stdio.h>|
|**fwprintf_s –**, **_fwprintf_s_l –**|\<stdio.h > nebo \<wchar.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také

[Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[_cprintf, _cprintf_l, _cwprintf, _cwprintf_l](cprintf-cprintf-l-cwprintf-cwprintf-l.md)<br/>
[fscanf, _fscanf_l, fwscanf, _fwscanf_l](fscanf-fscanf-l-fwscanf-fwscanf-l.md)<br/>
[sprintf, _sprintf_l –, swprintf –, _swprintf_l –, \__swprintf_l –](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
