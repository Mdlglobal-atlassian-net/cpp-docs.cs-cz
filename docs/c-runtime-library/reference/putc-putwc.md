---
title: "putc –, putwc – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- putwc
- putc
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
- _puttc
- putwc
- putc
dev_langs:
- C++
helpviewer_keywords:
- streams, writing characters to
- characters, writing
- putwc function
- putc function
- _puttc function
- puttc function
ms.assetid: a37b2e82-9d88-4565-8190-ff8d04c0ddb9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4a3c07cab44f6b709affa22f470dfd7a8840b729
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="putc-putwc"></a>putc, putwc
Znak se zapíše do datového proudu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      int putc(  
   int c,  
   FILE *stream   
);  
wint_t putwc(  
   wchar_t c,  
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `c`  
 Znak, který má být zapsána.  
  
 `stream`  
 Ukazatel na **souboru** struktura.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí znak zapsána. K označení chyba nebo podmínku end souboru `putc` a `putchar` vrátit `EOF`; `putwc` a `putwchar` vrátit **weof –**. Pro všechny čtyři rutiny, použijte [ferror –](../../c-runtime-library/reference/ferror.md) nebo [feof –](../../c-runtime-library/reference/feof.md) zkontrolujte chyba nebo konec souboru. Pokud pro předán ukazatele null `stream`, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění chcete-li pokračovat, tyto funkce vracejí `EOF` nebo **weof –** a nastavte `errno` k `EINVAL`.  
  
 V tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o těchto a dalších kódy chyb.  
  
## <a name="remarks"></a>Poznámky  
 `putc` Rutiny zapíše jednoho znaku `c` k výstupu `stream` na aktuální pozici. Jakékoliv celé číslo se dá předat do `putc`, ale jsou zapsány pouze nižších 8 bitů. `putchar` Rutiny je stejný jako **putc – (** `c` **, stdout)**. Pro každou rutinu Pokud dojde k chybě čtení, označení chyb pro datový proud nastavena. `putc` a `putchar` jsou podobné `fputc` a `_fputchar`, ale jsou implementované jako funkce i jako makra (najdete v části [výběru mezi funkcemi a makry](../../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md)). `putwc` a `putwchar` jsou verze široká charakterová `putc` a `putchar`, v uvedeném pořadí. `putwc` a `putc` chovají stejně jako datový proud se při otevření v režimu ANSI. `putc` nepodporuje aktuálně výstup do proudu kódování UNICODE.  
  
 Verzi pomocí **jazyka _nolock** příponu jsou shodné s tím rozdílem, že nejsou chráněny z narušení jiná vlákna. Další informace najdete v tématu **_putc_nolock –, _putwc_nolock –**.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_puttc`|`putc`|`putc`|**putwc**|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`putc`|\<stdio.h>|  
|`putwc`|\<stdio.h > nebo \<wchar.h >|  
  
Konzole není podporována v aplikacích pro univerzální platformu Windows (UWP). Standardní datový proud obslužných rutin, které jsou spojeny s konzolou, `stdin`, `stdout`, a `stderr`, C běhové funkce mohli používat v aplikacích pro UPW, musí být přesměrována. Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).
  
## <a name="libraries"></a>Knihovny  
 Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_putc.c  
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
      ch = putc( *p, stream );  
}  
```  
  
## <a name="output"></a>Výstup  
  
```  
This is the line of output  
```  
  
## <a name="see-also"></a>Viz také  
 [Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)   
 [fputc –, fputwc –](../../c-runtime-library/reference/fputc-fputwc.md)   
 [getc, getwc](../../c-runtime-library/reference/getc-getwc.md)