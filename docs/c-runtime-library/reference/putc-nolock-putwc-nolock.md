---
title: _putc_nolock, _putwc_nolock
ms.date: 4/2/2020
api_name:
- _putc_nolock
- _putwc_nolock
- _o__putc_nolock
- _o__putwc_nolock
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
- _puttc_nolock
- puttc_nolock
- putwc_nolock
- _putwc_nolock
- _putc_nolock
- putc_nolock
helpviewer_keywords:
- puttc_nolock function
- putc_nolock function
- _putc_nolock function
- streams, writing characters to
- characters, writing
- putwc_nolock function
- _puttc_nolock function
- _putwc_nolock function
ms.assetid: 3cfc7f21-c9e8-4b7f-b0fb-af0d4d85e7e1
ms.openlocfilehash: aa96275b29d2510400622f52fa34c58ae251ff6c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338472"
---
# <a name="_putc_nolock-_putwc_nolock"></a>_putc_nolock, _putwc_nolock

Zapíše znak do datového proudu bez uzamčení vlákna.

## <a name="syntax"></a>Syntaxe

```C
int _putc_nolock(
   int c,
   FILE *stream
);
wint_t _putwc_nolock(
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

Viz **putc, putwc**.

## <a name="remarks"></a>Poznámky

**_putc_nolock** a **_putwc_nolock** jsou shodné s verzemi bez **přípony _nolock** s tím rozdílem, že nejsou chráněny před rušením jinými vlákny. Mohou být rychlejší, protože jim nevznikají režie uzamčení jiných vláken. Tyto funkce používejte pouze v kontextech bezpečných pro přístup z více vláken, jako jsou aplikace s jedním vláknem nebo kde již volající obor zpracovává izolaci vlákna.

**_putwc_nolock** je širokoznaková verze **_putc_nolock**; tyto dvě funkce se chovají stejně, pokud je datový proud otevřen v režimu ANSI. **_putc_nolock** aktuálně nepodporuje výstup do datového proudu UNICODE.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_puttc_nolock**|**_putc_nolock**|**_putc_nolock**|**_putwc_nolock**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_putc_nolock**|\<stdio.h>|
|**_putwc_nolock**|\<stdio.h> \<nebo wchar.h>|

Konzola není podporována v aplikacích univerzální platformy Windows (UPW). Standardní popisovače datového proudu, které jsou přidruženy ke **konzole, stdin**, **stdout**a **stderr**, musí být přesměrovány před c run-time funkce je možné použít v aplikacích UPW. Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven c run-time](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Příklad

```C
// crt_putc_nolock.c
/* This program uses putc to write buffer
* to a stream. If an error occurs, the program
* stops before writing the entire buffer.
*/

#include <stdio.h>

int main( void )
{
   FILE *stream;
   char *p, buffer[] = "This is the line of output\n";
   int  ch;

   ch = 0;
   /* Make standard out the stream and write to it. */
   stream = stdout;
   for( p = buffer; (ch != EOF) && (*p != '\0'); p++ )
      ch = _putc_nolock( *p, stream );
}
```

### <a name="output"></a>Výstup

```Output
This is the line of output
```

## <a name="see-also"></a>Viz také

[I/O proudu](../../c-runtime-library/stream-i-o.md)<br/>
[fputc, fputwc](fputc-fputwc.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
