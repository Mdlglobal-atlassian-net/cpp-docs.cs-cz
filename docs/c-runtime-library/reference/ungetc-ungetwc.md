---
title: "ungetc –, ungetwc – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- ungetwc
- ungetc
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
- _ungettc
- ungetwc
- ungetc
dev_langs: C++
helpviewer_keywords:
- ungetwc function
- ungettc function
- characters, pushing back onto stream
- _ungettc function
- ungetc function
ms.assetid: e0754f3a-b4c6-408f-90c7-e6387b830d84
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ba352160afb6dc4a429721cd7af61204f5ef79e1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ungetc-ungetwc"></a>ungetc, ungetwc
Vynutí znak zpět do datového proudu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int ungetc(  
   int c,  
   FILE *stream   
);  
wint_t ungetwc(  
   wint_t c,  
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `c`  
 Znak, který má poslat.  
  
 `stream`  
 Ukazatel na `FILE` struktura.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud úspěšné, každá z těchto funkcí vrátí znak argument `c`. Pokud `c` nelze posunuto nebo žádné znak byl načten, vstupního datového proudu je zrušeno a `ungetc` vrátí `EOF`; `ungetwc` vrátí `WEOF`. Pokud `stream` je `NULL`, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění `EOF` nebo `WEOF` je vrácen a `errno` je nastaven na `EINVAL`.  
  
 Informace o těchto a dalších kódy chyb naleznete v tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Poznámky  
 `ungetc` Funkce nabízených oznámení znak `c` zpět do `stream` a vymaže end souborového indikátoru. Datový proud musí být otevřen pro čtení. Následné operace čtení na `stream` začíná `c`. Pokus o push `EOF` do datového proudu pomocí `ungetc` je ignorována.  
  
 Znaky umístěné v datovém proudu podle `ungetc` může vymazat, pokud `fflush`, `fseek`, `fsetpos`, nebo `rewind` je volána před znak, který je pro čtení z datového proudu. Indikátor pozice souboru bude mít hodnotu, který byl před znaky byly poslat zpět. Odpovídající do datového proudu externího úložiště se nezmění. Na úspěšně `ungetc` volání proti datový proud text indikátoru pozice souboru neurčené dokud všechny poslat zpět znaky jsou přečteny nebo zahozeny. Na každém úspěšném `ungetc` volání proti binární datový proud indikátoru pozice souboru se odečte; pokud její hodnota je 0 před voláním, hodnota není definován po volání.  
  
 Výsledky mohou být nepředvídatelné Pokud `ungetc` je volána dvakrát bez čtení nebo umístění souboru operace mezi dvěma volání. Po volání `fscanf`, volání `ungetc` může selhat, pokud jiné operace čtení (například `getc`) nebylo provedeno. Důvodem je, že `fscanf` samotné volá `ungetc`.  
  
 `ungetwc`široká charakterová verze `ungetc`. Však na každém úspěšné `ungetwc` volání na text nebo binární datový proud, hodnota indikátoru pozice souboru neurčené dokud všechny poslat zpět znaky jsou přečteny nebo zahozeny.  
  
 Tyto funkce jsou bezpečné pro přístup z více vláken a zamknout citlivá data během provádění. Bez uzamčení verze, najdete v části [_ungetc_nolock –, _ungetwc_nolock –](../../c-runtime-library/reference/ungetc-nolock-ungetwc-nolock.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_ungettc`|`ungetc`|`ungetc`|`ungetwc`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`ungetc`|\<stdio.h >|  
|`ungetwc`|\<stdio.h > nebo \<wchar.h >|  
  
 Konzole není podporována v [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikace. Standardní datový proud obslužných rutin, které jsou spojeny s konzolou –`stdin`, `stdout`, a `stderr`– C běhové funkce je mohli používat, musí být přesměrována [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikace. Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_ungetc.c  
// This program first converts a character  
// representation of an unsigned integer to an integer. If  
// the program encounters a character that is not a digit,  
// the program uses ungetc to replace it in the  stream.  
//  
  
#include <stdio.h>  
#include <ctype.h>  
  
int main( void )  
{  
   int ch;  
   int result = 0;  
  
   // Read in and convert number:  
   while( ((ch = getchar()) != EOF) && isdigit( ch ) )  
      result = result * 10 + ch - '0';    // Use digit.  
   if( ch != EOF )  
      ungetc( ch, stdin );                // Put nondigit back.  
   printf( "Number = %d\nNext character in stream = '%c'",   
            result, getchar() );  
}  
```  
  
```Output  
  
      521aNumber = 521  
Next character in stream = 'a'  
```  
  
## <a name="see-also"></a>Viz také  
 [Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)   
 [getc, getwc –](../../c-runtime-library/reference/getc-getwc.md)   
 [putc –, putwc –](../../c-runtime-library/reference/putc-putwc.md)