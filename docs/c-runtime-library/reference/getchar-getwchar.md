---
title: "GetChar getwchar – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- gettchar function
- characters, reading
- getwchar function
- _gettchar function
- standard input, reading from
ms.assetid: 19fda588-3e33-415c-bb60-dd73c028086a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b2e3af8fbc613a3c1634e24011e22283dd8520f7
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
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
 Každá rutina načte jeden znak ze standardního vstupu `stdin` a zvýší přidružený ukazatel na soubor, aby ukazoval na další znak. `getchar` je stejný jako [_fgetchar –](../../c-runtime-library/reference/fgetc-fgetwc.md), ale jsou implementované jako funkce a jako makra.  
  
 Tyto funkce Uzamknout volající vlákno a proto jsou bezpečné pro přístup z více vláken. Bez uzamčení verze, najdete v části [_getchar_nolock –, _getwchar_nolock –](../../c-runtime-library/reference/getchar-nolock-getwchar-nolock.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_gettchar`|`getchar`|`getchar`|`getwchar`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`getchar`|\<stdio.h>|  
|`getwchar`|\<stdio.h > nebo \<wchar.h >|  
  
Konzole není podporována v aplikacích pro univerzální platformu Windows (UWP). Standardní datový proud obslužných rutin, které jsou spojeny s konzolou, `stdin`, `stdout`, a `stderr`, C běhové funkce mohli používat v aplikacích pro UPW, musí být přesměrována. Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).
  
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
 [_getch, _getwch](../../c-runtime-library/reference/getch-getwch.md)   
 [putc –, putwc –](../../c-runtime-library/reference/putc-putwc.md)   
 [ungetc, ungetwc](../../c-runtime-library/reference/ungetc-ungetwc.md)