---
title: "GetChar getwchar – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- getchar
- getwchar
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
- getwchar
- GetChar
dev_langs: C++
helpviewer_keywords:
- gettchar function
- characters, reading
- getwchar function
- _gettchar function
- standard input, reading from
ms.assetid: 19fda588-3e33-415c-bb60-dd73c028086a
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3b82e9debd0ebb5084bb730a6ad06a0b8cba42df
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="getchar-getwchar"></a>getchar, getwchar
Čte znak z standardní vstup.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int getchar();  
wint_t getwchar();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí znak pro čtení. K označení došlo k chybě nebo podmínku end souborového `getchar` vrátí `EOF`, a `getwchar` vrátí `WEOF`. Chcete-li pro funkci `getchar` zkontrolovat chybu nebo konec souboru, použijte `ferror` nebo `feof` .  
  
## <a name="remarks"></a>Poznámky  
 Každá rutina načte jeden znak ze standardního vstupu `stdin` a zvýší přidružený ukazatel na soubor, aby ukazoval na další znak. `getchar`je stejný jako [_fgetchar –](../../c-runtime-library/reference/fgetc-fgetwc.md), ale jsou implementované jako funkce a jako makra.  
  
 Tyto funkce Uzamknout volající vlákno a proto jsou bezpečné pro přístup z více vláken. Bez uzamčení verze, najdete v části [_getchar_nolock –, _getwchar_nolock –](../../c-runtime-library/reference/getchar-nolock-getwchar-nolock.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_gettchar`|`getchar`|`getchar`|`getwchar`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`getchar`|\<stdio.h >|  
|`getwchar`|\<stdio.h > nebo \<wchar.h >|  
  
 Konzole není podporována v [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikace. Standardní datový proud obslužných rutin, které jsou spojeny s konzolou –`stdin`, `stdout`, a `stderr`– C běhové funkce je mohli používat, musí být přesměrována [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikace. Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_getchar.c  
// Use getchar to read a line from stdin.  
  
#include <stdio.h>  
  
int main()  
{  
    char buffer[81];  
    int i, ch;  
  
    for (i = 0; (i < 80) && ((ch = getchar()) != EOF)  
                         && (ch != '\n'); i++)  
    {  
        buffer[i] = (char) ch;  
    }  
  
    // Terminate string with a null character   
    buffer[i] = '\0';  
    printf( "Input was: %s\n", buffer);  
}  
```  
  
```Output  
  
This textInput was: This text  
```  
  
## <a name="see-also"></a>Viz také  
 [Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)   
 [getc, getwc –](../../c-runtime-library/reference/getc-getwc.md)   
 [fgetc –, fgetwc –](../../c-runtime-library/reference/fgetc-fgetwc.md)   
 [_getch –, _getwch –](../../c-runtime-library/reference/getch-getwch.md)   
 [putc –, putwc –](../../c-runtime-library/reference/putc-putwc.md)   
 [ungetc –, ungetwc –](../../c-runtime-library/reference/ungetc-ungetwc.md)