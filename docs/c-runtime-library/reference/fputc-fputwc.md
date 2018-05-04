---
title: fputc –, fputwc – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- streams, writing characters to
- fputtc function
- _fputtc function
- fputwc function
- fputc function
ms.assetid: 5a0a593d-43f4-4fa2-a401-ec4e23de4d2f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: af93e0c42002dc557f691daadd2fc003dced0247
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="fputc-fputwc"></a>fputc, fputwc

Znak se zapíše do datového proudu.

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
Znak, který má být zapsána.

*Datový proud*<br/>
Ukazatel na **souboru** struktura.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrátí znak zapsána. Pro **fputc –**, návratová hodnota **EOF** označuje chybu. Pro **fputwc –**, návratová hodnota **weof –** označuje chybu. Pokud *datového proudu* je **NULL**, tyto funkce vyvolat obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění chcete-li pokračovat, že budou vracet **EOF** a nastavte **errno** k **einval –**.

V tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o těchto a dalších kódy chyb.

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí zapíše jednoho znaku *c* do souboru na pozici indikován označení pozice přidružený soubor (je-li definována) a přejde na indikátor podle potřeby. U **fputc –** a **fputwc –**, soubor je přidružen *datového proudu*. Pokud je soubor nemůže podporovat umísťovací požadavky nebo byl otevřen v režimu připojení, znak, který je připojen na konec datového proudu.

Dvě funkce chovají stejně jako datový proud se při otevření v režimu ANSI. **fputc –** výstup aktuálně nepodporuje do proudu kódování UNICODE.

Verzi pomocí **jazyka _nolock** příponu jsou shodné s tím rozdílem, že nejsou chráněny z narušení jiná vlákna. Další informace najdete v tématu[_fputc_nolock –, _fputwc_nolock –](fputc-nolock-fputwc-nolock.md).

Postupujte podle konkrétní rutiny poznámky.

|Rutina|Poznámky|
|-------------|-------------|
|**fputc –**|Ekvivalentní **putc –**, ale implementována pouze jako funkci, nikoli jako funkce a makra.|
|**fputwc –**|Široká charakterová verzi **fputc –**. Zapíše *c* jako vícebajtových znaků nebo široká znaková podle jestli *datového proudu* je otevřen v režimu textových nebo binárního režimu.|

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_fputtc –**|**fputc –**|**fputc –**|**fputwc –**|

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fputc –**|\<stdio.h>|
|**fputwc –**|\<stdio.h > nebo \<wchar.h >|

Konzole není podporována v aplikacích pro univerzální platformu Windows (UWP). Standardní datový proud obslužných rutin, které jsou spojeny s konzolou –**stdin –**, **stdout**, a **stderr**– musí být přesměrována C běhové funkce mohli používat v aplikacích pro UPW . Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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

[Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[fgetc, fgetwc](fgetc-fgetwc.md)<br/>
[putc, putwc](putc-putwc.md)<br/>
