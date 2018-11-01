---
title: _fputchar, _fputwchar
ms.date: 11/04/2016
apiname:
- _fputchar
- _fputwchar
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- fputtchar
- _fputwchar
- fputwchar
- _fputtchar
- fputchar
- _fputchar
helpviewer_keywords:
- fputchar function
- standard output, writing to
- _fputtchar function
- fputwchar function
- _fputwchar function
- fputtchar function
- _fputchar function
ms.assetid: b92ff600-a924-4f2b-b0e7-3097ee31bdff
ms.openlocfilehash: 57ec2350fa1d0b681c6eed0c4cfc4ec4660977e8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50477971"
---
# <a name="fputchar-fputwchar"></a>_fputchar, _fputwchar

Zapíše znak do **stdout**.

## <a name="syntax"></a>Syntaxe

```C
int _fputchar(
   int c
);
wint_t _fputwchar(
   wchar_t c
);
```

### <a name="parameters"></a>Parametry

*c*<br/>
Znak k zapsání.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrací napsaný znak. Pro **_fputchar**, vrácená hodnota **EOF** označuje chybu. Pro **_fputwchar –**, vrácená hodnota **WEOF** označuje chybu. Pokud je c **NULL**, tyto funkce generují výjimku neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí **EOF** (nebo **WEOF**) a nastavte **errno** k **EINVAL**.

Další informace o těchto a dalších chybových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Obě tyto funkce zapíše jeden znak *c* k **stdout** a posune indikátor podle potřeby. **_fputchar** je ekvivalentní `fputc( stdout )`. Je také ekvivalentní **putchar**, ale implementována pouze jako funkce, nikoli jako funkce a makro. Na rozdíl od **fputc** a **putchar**, tyto funkce nejsou kompatibilní se standardem ANSI.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_fputtchar –**|**_fputchar**|**_fputchar**|**_fputwchar**|

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_fputchar**|\<stdio.h>|
|**_fputwchar**|\<stdio.h > nebo \<wchar.h >|

Konzole není podporována v aplikacích pro univerzální platformu Windows (UPW). Standardní datový proud popisovačů, které jsou spojeny s konzolou –**stdin**, **stdout**, a **stderr**– musí být přesměrován před funkcí jazyka C za běhu můžete použít v aplikacích pro UWP . Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_fputchar.c
// This program uses _fputchar
// to send a character array to stdout.

#include <stdio.h>

int main( void )
{
    char strptr[] = "This is a test of _fputchar!!\n";
    char *p = NULL;

    // Print line to stream using _fputchar.
    p = strptr;
    while( (*p != '\0') && _fputchar( *(p++) ) != EOF )
      ;
}
```

```Output
This is a test of _fputchar!!
```

## <a name="see-also"></a>Viz také:

[Stream vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[fgetc, fgetwc](fgetc-fgetwc.md)<br/>
[putc, putwc](putc-putwc.md)<br/>
