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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 289e1114a936bdaa41fc59a0526db006536461f7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346273"
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

*C*<br/>
Znak, který má být napsán.

*Proudu*<br/>
Ukazatel na **strukturu FILE.**

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrátí napsaný znak. Pro **fputc**, vrácená hodnota **EOF** označuje chybu. Pro **fputwc**, vrácená hodnota **WEOF** označuje chybu. Pokud je *datový proud* **NULL**, tyto funkce vyvolávají neplatnou obslužnou rutinu parametru, jak je popsáno v části [Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, vrátí **EOF** a nastaví **errno** na **EINVAL**.

Další informace o těchto a dalších kódech chyb naleznete v [_doserrno, errno, _sys_errlist a _sys_nerr.](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí zapíše jeden znak *c* do souboru na pozici označené přidruženým indikátorem polohy souboru (pokud je definována) a podle potřeby posune indikátor. V případě **fputc** a **fputwc**je soubor spojen s *streamem*. Pokud soubor nemůže podporovat požadavky na umístění nebo byl otevřen v režimu připojení, znak je připojen na konec datového proudu.

Tyto dvě funkce se chovají stejně, pokud je datový proud otevřen v režimu ANSI. **fputc** v současné době nepodporuje výstup do datového proudu UNICODE.

Verze s **příponou _nolock** jsou identické s tím rozdílem, že nejsou chráněny před rušením jinými vlákny. Další informace naleznete[v tématu _fputc_nolock, _fputwc_nolock](fputc-nolock-fputwc-nolock.md).

Následují poznámky specifické pro rutinu.

|Rutina|Poznámky|
|-------------|-------------|
|**fputc**|Ekvivalentní **putc**, ale implementována pouze jako funkce, nikoli jako funkce a makro.|
|**fputwc řekl:**|Širokoúhlá verze **fputc**. Zapíše *c* jako vícebajtový znak nebo široký znak podle toho, zda je *datový proud* otevřen v textovém nebo binárním režimu.|

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_fputtc**|**fputc**|**fputc**|**fputwc řekl:**|

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fputc**|\<stdio.h>|
|**fputwc řekl:**|\<stdio.h> \<nebo wchar.h>|

Konzola není podporována v aplikacích univerzální platformy Windows (UPW). Standardní popisovače datového proudu, které jsou přidruženy ke konzole –**stdin**, **stdout**a **stderr**– musí být přesměrovány, aby je mohly funkce c run-time používat v aplikacích UPW. Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

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
