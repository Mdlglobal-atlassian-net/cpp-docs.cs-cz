---
title: "_fputc_nolock –, _fputwc_nolock – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _fputwc_nolock
- _fputc_nolock
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
- _fputc_nolock
- fputwc_nolock
- fputc_nolock
- fputtc_nolock
- _fputwc_nolock
- _fputtc_nolock
dev_langs: C++
helpviewer_keywords:
- streams, writing characters to
- fputwc_nolock function
- fputtc_nolock function
- _fputc_nolock function
- fputc_nolock function
- _fputtc_nolock function
- _fputwc_nolock function
ms.assetid: c63eb3ad-58fa-46d0-9249-9c25f815eab9
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 635000fb21aa215c6db1c56d49ee365457473a12
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="fputcnolock-fputwcnolock"></a>_fputc_nolock, _fputwc_nolock
Zapíše znak na datový proud, bez blokování vlákno.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _fputc_nolock(  
   int c,  
   FILE *stream   
);  
wint_t _fputwc_nolock(  
   wchar_t c,  
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `c`  
 Znak, který má být zapsána.  
  
 `stream`  
 Ukazatel `FILE` struktura.  
  
## <a name="return-value"></a>Návratová hodnota  
 Každá z těchto funkcí vrátí znak zapsána. Informace o chybě, najdete v části [fputc –, fputwc –](../../c-runtime-library/reference/fputc-fputwc.md).  
  
## <a name="remarks"></a>Poznámky  
 `_fputc_nolock`a `_fputwc_nolock` jsou stejné jako `fputc` a `fputwc`, s tím rozdílem, že nejsou chráněny z narušení jiná vlákna. Může být rychlejší, protože nevznikají nároky na uzamčení jiná vlákna. Tyto funkce lze používejte pouze v kontextu vláken jako je například aplikace nebo kde oboru volání již zpracovává izolace přístup z více vláken.  
  
 Dvě funkce chovají stejně jako datový proud se při otevření v režimu ANSI. `_fputc_nolock`aktuálně nepodporuje výstup do proudu kódování UNICODE.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_fputtc_nolock`|`_fputc_nolock`|`_fputc_nolock`|`_fputwc_nolock`|  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Požadovaný hlavičkový soubor|  
|--------------|---------------------|  
|`_fputc_nolock`|\<stdio.h >|  
|`_fputwc_nolock`|\<stdio.h > nebo \<wchar.h >|  
  
 Konzole není podporována v [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikace. Standardní datový proud obslužných rutin, které jsou spojeny s konzolou –`stdin`, `stdout`, a `stderr`– C běhové funkce je mohli používat, musí být přesměrována [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikace. Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_fputc_nolock.c  
// This program uses _fputc_nolock  
// to send a character array to stdout.  
  
#include <stdio.h>  
  
int main( void )  
{  
   char strptr1[] = "This is a test of _fputc_nolock!!\n";  
   char *p;  
  
   // Print line to stream using fputc.   
   p = strptr1;  
   while( (*p != '\0') && _fputc_nolock( *(p++), stdout ) != EOF ) ;  
  
}  
```  
  
```Output  
This is a test of _fputc_nolock!!  
```  
  
## <a name="see-also"></a>Viz také  
 [Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)   
 [fgetc –, fgetwc –](../../c-runtime-library/reference/fgetc-fgetwc.md)   
 [putc –, putwc –](../../c-runtime-library/reference/putc-putwc.md)