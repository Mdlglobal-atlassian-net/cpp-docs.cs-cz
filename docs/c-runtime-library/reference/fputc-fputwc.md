---
title: fputc, fputwc
ms.date: 4/2/2020
api_name:
- fputc
- fputwc
- _o_fputc
- _o_fputwc
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
ms.openlocfilehash: 90091bff6a8ee3ced050c359ed540f45afe74f6b
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910207"
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

*r*<br/>
Znak, který se má zapsat

*Stream*<br/>
Ukazatel na strukturu **souborů** .

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrátí napsaný znak. V případě **fputc**označuje návratová hodnota **EOF** chybu. V případě **fputwc**označuje návratová hodnota **WEOF** chybu. Pokud má *datový proud* **hodnotu null**, tyto funkce vyvolají obslužnou rutinu neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí **EOF** a nastaví **errno** na **EINVAL**.

Další informace o těchto a dalších chybových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) .

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí zapisuje jeden znak *c* do souboru na pozici, která je označena ukazatelem pozice přidruženého souboru (je-li definován), a podle potřeby posune ukazatel. V případě **fputc** a **fputwc**je soubor přidružený ke *streamu*. Pokud soubor nemůže podporovat požadavky na umístění nebo byl otevřen v režimu připojení, znak je připojen na konec datového proudu.

Tyto dvě funkce se chovají stejně, pokud je datový proud otevřen v režimu ANSI. **fputc** v současné době nepodporuje výstup do datového proudu Unicode.

Verze s příponou **_nolock** jsou stejné s tím rozdílem, že nejsou chráněny před rušením jinými vlákny. Další informace najdete v tématu[_fputc_nolock _fputwc_nolock](fputc-nolock-fputwc-nolock.md).

Následují poznámky specifické pro rutiny.

|Rutina|Poznámky|
|-------------|-------------|
|**fputc**|Ekvivalent **putc**, ale implementována pouze jako funkce, nikoli jako funkce a makro.|
|**fputwc**|Verze **fputc**pro nejrůznější znaky. Zapisuje *c* jako vícebajtový znak nebo jako velký znak v závislosti na tom, zda je *datový proud* otevřen v textovém režimu nebo v binárním režimu.|

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_fputtc**|**fputc**|**fputc**|**fputwc**|

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fputc**|\<stdio. h>|
|**fputwc**|\<stdio. h> nebo \<WCHAR. h>|

Konzola není v aplikacích Univerzální platforma Windows (UWP) podporována. Standardní popisovače streamů, které jsou spojeny s konzolou –**stdin**, **stdout**a **stderr**– musí být přesměrované před tím, než je funkce běhového běhu v aplikacích pro UWP můžou použít. Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také

[I/O proudu](../../c-runtime-library/stream-i-o.md)<br/>
[fgetc, fgetwc](fgetc-fgetwc.md)<br/>
[putc, putwc](putc-putwc.md)<br/>
