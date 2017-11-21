---
title: "getc, getwc – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- getwc
- getc
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
- _gettc
- getwc
- _gettchar
- getc
dev_langs: C++
helpviewer_keywords:
- characters, reading
- _gettc function
- getwchar function
- streams, reading characters from
- reading characters from streams
- getc function
- getwc function
- gettc function
ms.assetid: 354ef514-d0c7-404b-92f5-995f6a834bb3
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 78a94d954631dfffbdcdc4bcad252599c673f44b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="getc-getwc"></a>getc, getwc
Znak číst z datového proudu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int getc(   
   FILE *stream   
);  
wint_t getwc(   
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `stream`  
 Vstupní datový proud.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí znak pro čtení. K označení došlo k chybě nebo podmínku end souborového `getc` vrátí `EOF`, a `getwc` vrátí `WEOF`. Chcete-li pro funkci `getc` zkontrolovat chybu nebo konec souboru, použijte `ferror` nebo `feof` . Pokud `stream` je `NULL`, `getc` a `getwc` vyvolat obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění chcete-li pokračovat, tyto funkce vracejí `EOF` (nebo `WEOF` pro `getwc`) a nastavte `errno` k `EINVAL`.  
  
 V tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o těchto a dalších kódy chyb.  
  
## <a name="remarks"></a>Poznámky  
 Každou rutinu přečte jednoho znaku ze souboru na aktuální pozici a zvýší přidružený soubor ukazatele (je-li definována) tak, aby odkazoval na další znak. Soubor je přidružen `stream`.  
  
 Tyto funkce Uzamknout volající vlákno a proto jsou bezpečné pro přístup z více vláken. Bez uzamčení verze, najdete v části [_getc_nolock –, _getwc_nolock –](../../c-runtime-library/reference/getc-nolock-getwc-nolock.md).  
  
 Postupujte podle konkrétní rutiny poznámky.  
  
|Rutina|Poznámky|  
|-------------|-------------|  
|`getc`|Stejné jako `fgetc`, ale implementovaná jako funkce a jako makra.|  
|`getwc`|Široká charakterová verzi `getc`. Čte vícebajtových znaků nebo široká znaková podle jestli `stream` je otevřen v režimu textových nebo binárního režimu.|  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_gettc`|`getc`|`getc`|`getwc`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`getc`|\<stdio.h >|  
|`getwc`|\<stdio.h > nebo \<wchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
```  
// crt_getc.c  
// Use getc to read a line from a file.  
  
#include <stdio.h>  
  
int main()  
{  
    char buffer[81];  
    int i, ch;  
    FILE* fp;  
  
    // Read a single line from the file "crt_getc.txt".   
  
    fopen_s(&fp, "crt_getc.txt", "r");  
    if (!fp)  
    {  
       printf("Failed to open file crt_getc.txt.\n");  
       exit(1);  
    }  
  
    for (i = 0; (i < 80) && ((ch = getc(fp)) != EOF)  
                         && (ch != '\n'); i++)  
    {  
        buffer[i] = (char) ch;  
    }  
  
    // Terminate string with a null character   
    buffer[i] = '\0';  
    printf( "Input was: %s\n", buffer);  
  
    fclose(fp);  
}  
```  
  
## <a name="input-crtgetctxt"></a>Vstup: crt_getc.txt  
  
```  
Line one.  
Line two.  
```  
  
### <a name="output"></a>Výstup  
  
```  
Input was: Line one.  
```  
  
## <a name="see-also"></a>Viz také  
 [Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)   
 [fgetc –, fgetwc –](../../c-runtime-library/reference/fgetc-fgetwc.md)   
 [_getch –, _getwch –](../../c-runtime-library/reference/getch-getwch.md)   
 [putc –, putwc –](../../c-runtime-library/reference/putc-putwc.md)   
 [ungetc –, ungetwc –](../../c-runtime-library/reference/ungetc-ungetwc.md)