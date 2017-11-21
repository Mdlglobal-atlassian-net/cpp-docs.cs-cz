---
title: "putchar –, putwchar – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- putchar
- putwchar
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
- putchar
- putwchar
- _puttchar
dev_langs: C++
helpviewer_keywords:
- putchar function
- _puttchar function
- characters, writing
- standard output, writing to
- putwchar function
ms.assetid: 93657c7f-cca1-4032-8e3a-cd6ab6193748
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a1999c32aea84e613ce9e1a34b0c5b913d313ac7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="putchar-putwchar"></a>putchar, putwchar
Zapíše znak pro **stdout**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      int putchar(  
   int c   
);  
wint_t putwchar(  
   wchar_t c   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `c`  
 Znak, který má být zapsána.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí znak zapsána. K označení chyba nebo podmínku end souboru `putc` a `putchar` vrátit `EOF`; `putwc` a `putwchar` vrátit **weof –**. Pro všechny čtyři rutiny, použijte [ferror –](../../c-runtime-library/reference/ferror.md) nebo [feof –](../../c-runtime-library/reference/feof.md) zkontrolujte chyba nebo konec souboru. Pokud pro předán ukazatele null `stream`, tyto funkce vygeneruje výjimka neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění chcete-li pokračovat, že budou vracet `EOF` nebo **weof –** a nastavte `errno` k `EINVAL`.  
  
 V tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o těchto a dalších kódy chyb.  
  
## <a name="remarks"></a>Poznámky  
 `putc` Rutiny zapíše jednoho znaku `c` k výstupu `stream` na aktuální pozici. Jakékoliv celé číslo se dá předat do `putc`, ale jsou zapsány pouze nižších 8 bitů. `putchar` Rutiny je stejný jako **putc – (** `c` **, stdout)**. Pro každou rutinu Pokud dojde k chybě čtení, označení chyb pro datový proud nastavena. `putc`a `putchar` jsou podobné `fputc` a `_fputchar`, ale jsou implementované jako funkce i jako makra (najdete v části [výběru mezi funkcemi a makry](../../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md)). `putwc`a `putwchar` jsou verze široká charakterová `putc` a `putchar`, v uvedeném pořadí.  
  
 Verzi pomocí **jazyka _nolock** příponu jsou shodné s tím rozdílem, že nejsou chráněny z narušení jiná vlákna. Může být rychlejší, protože nevznikají nároky na uzamčení jiná vlákna. Tyto funkce lze používejte pouze v kontextu vláken jako je například aplikace nebo kde oboru volání již zpracovává izolace přístup z více vláken.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_puttchar`|`putchar`|`putchar`|**putwchar –**|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`putchar`|\<stdio.h >|  
|`putwchar`|\<stdio.h > nebo \<wchar.h >|  
  
 Konzole není podporována v [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikace. Standardní datový proud obslužných rutin, které jsou spojeny s konzolou –`stdin`, `stdout`, a `stderr`– C běhové funkce je mohli používat, musí být přesměrována [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikace. Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Knihovny  
 Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_putchar.c  
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
  
   for( p = buffer; (ch != EOF) && (*p != '\0'); p++ )  
      ch = putchar( *p );  
}  
```  
  
## <a name="output"></a>Výstup  
  
```  
This is the line of output  
```  
  
## <a name="see-also"></a>Viz také  
 [Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)   
 [fputc –, fputwc –](../../c-runtime-library/reference/fputc-fputwc.md)   
 [getc, getwc –](../../c-runtime-library/reference/getc-getwc.md)