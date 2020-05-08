---
title: _fputchar, _fputwchar
ms.date: 4/2/2020
api_name:
- _fputchar
- _fputwchar
- _o__fputchar
- _o__fputwchar
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fputtchar
- _fputwchar
- fputwchar
- _fputtchar
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
ms.openlocfilehash: 08997730e0ef80072e29de5bc5e7c106cb6cb9e0
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912016"
---
# <a name="_fputchar-_fputwchar"></a>_fputchar, _fputwchar

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

*r*<br/>
Znak, který se má zapsat

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrátí napsaný znak. Pro **_fputchar**návratová hodnota **EOF** označuje chybu. U **_fputwchar**vrácená hodnota **WEOF** označuje chybu. Pokud je c **null**, tyto funkce generují výjimku neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí **EOF** (nebo **WEOF**) a nastaví **errno** na **EINVAL**.

Další informace o těchto a dalších chybových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Obě tyto funkce zapisují jeden znak *c* do **stdout** a podle potřeby posunou ukazatel. **_fputchar** je ekvivalentem `fputc( stdout )`. Je také ekvivalentní **putchar**, ale je implementována pouze jako funkce, nikoli jako funkce a makro. Na rozdíl od **fputc** a **putchar**nejsou tyto funkce kompatibilní se standardem ANSI.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_fputtchar**|**_fputchar**|**_fputchar**|**_fputwchar**|

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_fputchar**|\<stdio. h>|
|**_fputwchar**|\<stdio. h> nebo \<WCHAR. h>|

Konzola není v aplikacích Univerzální platforma Windows (UWP) podporována. Standardní popisovače streamů, které jsou spojeny s konzolou –**stdin**, **stdout**a **stderr**– musí být přesměrované před tím, než je funkce běhového běhu v aplikacích pro UWP můžou použít. Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také

[I/O proudu](../../c-runtime-library/stream-i-o.md)<br/>
[fgetc, fgetwc](fgetc-fgetwc.md)<br/>
[putc, putwc](putc-putwc.md)<br/>
