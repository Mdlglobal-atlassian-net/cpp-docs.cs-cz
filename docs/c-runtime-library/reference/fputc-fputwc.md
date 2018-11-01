---
title: fputc, fputwc
ms.date: 11/04/2016
apiname:
- fputc
- fputwc
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
- fputc
- fputwc
- _fputtc
helpviewer_keywords:
- streams, writing characters to
- fputtc function
- _fputtc function
- fputwc function
- fputc function
ms.assetid: 5a0a593d-43f4-4fa2-a401-ec4e23de4d2f
ms.openlocfilehash: fc06c9f2060baae63071339768cef11fc5f34023
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50447174"
---
# <a name="fputc-fputwc"></a>fputc, fputwc

Zapíše znak do datového proudu.

## <a name="syntax"></a>Syntaxe

```C
int fputc(
   int c,
   FILE *stream
);
wint_t fputwc(
   wchar_t c,
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*c*<br/>
Znak k zapsání.

*Stream*<br/>
Ukazatel na **souboru** struktury.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrací napsaný znak. Pro **fputc**, vrácená hodnota **EOF** označuje chybu. Pro **fputwc –**, vrácená hodnota **WEOF** označuje chybu. Pokud *stream* je **NULL**, tyto funkce vyvolají obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí **EOF** a nastavte **errno** k **EINVAL**.

Zobrazit [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o těchto a dalších chybových kódech.

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí zapíše jeden znak *c* do souboru na pozici indikován indikátorem pozice přidruženého souboru (je-li definován) a posune indikátor podle potřeby. V případě třídy **fputc** a **fputwc –**, je soubor spojen s *stream*. Pokud soubor nemůže podporovat požadavky na umístění nebo byl otevřena v režimu připojení, znak je připojen na konec datového proudu.

Tyto dvě funkce se chovají stejně jako v případě, že datový proud je otevřen v režimu ANSI. **fputc** aktuálně nepodporuje výstup do datového proudu UNICODE.

Verze s **_nolock** přípona jsou stejné s tím rozdílem, že nejsou chráněny před rušením jinými vlákny. Další informace najdete v tématu[_fputc_nolock _fputwc_nolock –](fputc-nolock-fputwc-nolock.md).

Následují poznámky specifické pro rutinu.

|Rutina|Poznámky|
|-------------|-------------|
|**fputc**|Ekvivalentní **putc**, ale implementována pouze jako funkce, nikoli jako funkce a makro.|
|**fputwc –**|Širokoznaká verze **fputc**. Zapíše *c* jako vícebajtový znak nebo široký znak podle toho, zda *stream* je otevřen v textovém nebo binárním režimu.|

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_fputtc –**|**fputc**|**fputc**|**fputwc –**|

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fputc**|\<stdio.h>|
|**fputwc –**|\<stdio.h > nebo \<wchar.h >|

Konzole není podporována v aplikacích pro univerzální platformu Windows (UPW). Standardní datový proud popisovačů, které jsou spojeny s konzolou –**stdin**, **stdout**, a **stderr**– musí být přesměrován před funkcí jazyka C za běhu můžete použít v aplikacích pro UWP . Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_fputc.c
// This program uses fputc
// to send a character array to stdout.

#include <stdio.h>

int main( void )
{
   char strptr1[] = "This is a test of fputc!!\n";
   char *p;

   // Print line to stream using fputc.
   p = strptr1;
   while( (*p != '\0') && fputc( *(p++), stdout ) != EOF ) ;

}
```

```Output
This is a test of fputc!!
```

## <a name="see-also"></a>Viz také:

[Stream vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[fgetc, fgetwc](fgetc-fgetwc.md)<br/>
[putc, putwc](putc-putwc.md)<br/>
