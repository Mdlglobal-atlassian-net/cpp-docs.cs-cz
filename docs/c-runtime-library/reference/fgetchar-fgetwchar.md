---
title: "_fgetchar –, _fgetwchar – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _fgetchar
- _fgetwchar
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
- fgetwchar
- _fgettchar
- _fgetchar
- _fgetwchar
- fgettchar
dev_langs:
- C++
helpviewer_keywords:
- fgetwchar function
- _fgetchar function
- fgettchar function
- _fgetwchar function
- _fgettchar function
- standard input, reading from
- fgetchar function
ms.assetid: 8bce874c-701a-41a3-b1b2-feff266fb5b9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0eabf9bd54764aaa37bd860eb5bdb7d1ac5232ab
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="fgetchar-fgetwchar"></a>_fgetchar, _fgetwchar
Přečte znak z `stdin`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _fgetchar( void );  
wint_t _fgetwchar( void );  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 `_fgetchar` Vrátí znak přečíst jako `int` , nebo může vracet `EOF` udávajících chyba nebo konec souboru. **_** `fgetwchar` vrátí, jako [wint_t –](../../c-runtime-library/standard-types.md), široké znak, který odpovídá znak čtení nebo vrátí `WEOF` udávajících chyba nebo konec souboru. Pro obě funkce použijte `feof` nebo `ferror` rozlišit mezi chybu a podmínku end souboru.  
  
## <a name="remarks"></a>Poznámky  
 Tyto funkce číst jeden znak z `stdin`. Funkce pak zvýší přidružený soubor ukazatele (je-li definována) tak, aby odkazoval na další znak. Pokud datový proud je na konci souboru, je nastavit koncové souboru indikátor pro datový proud.  
  
 `_fgetchar` je ekvivalentní `fgetc( stdin )`. Je také ekvivalentní `getchar`, ale implementována pouze jako funkci, nikoli jako funkce a makra. `_fgetwchar` je verze široká charakterová `_fgetchar`.  
  
 Tyto funkce nejsou kompatibilní se standardem ANSI.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_fgettchar`|`_fgetchar`|`_fgetchar`|`_fgetwchar`|  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Požadovaný hlavičkový soubor|  
|--------------|---------------------|  
|`_fgetchar`|\<stdio.h>|  
|`_fgetwchar`|\<stdio.h > nebo \<wchar.h >|  
  
 Konzole není podporována v aplikacích pro univerzální platformu Windows (UWP). Standardní datový proud obslužných rutin, které jsou spojeny s konzolou –`stdin`, `stdout`, a `stderr`– C běhové funkce je mohli používat, musí být přesměrována [! INCLUDEUWP aplikace. Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_fgetchar.c  
// This program uses _fgetchar to read the first  
// 80 input characters (or until the end of input)  
// and place them into a string named buffer.  
//  
  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   char buffer[81];  
   int  i, ch;  
  
   // Read in first 80 characters and place them in "buffer":  
   ch = _fgetchar();  
   for( i=0; (i < 80 ) && ( feof( stdin ) == 0 ); i++ )  
   {  
      buffer[i] = (char)ch;  
      ch = _fgetchar();  
   }  
  
   // Add null to end string   
   buffer[i] = '\0';  
   printf( "%s\n", buffer );  
}  
```  
  
```Output  
  
      Line one.  
Line two.Line one.  
Line two.  
```  
  
## <a name="see-also"></a>Viz také  
 [Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)   
 [fputc –, fputwc –](../../c-runtime-library/reference/fputc-fputwc.md)   
 [getc, getwc](../../c-runtime-library/reference/getc-getwc.md)