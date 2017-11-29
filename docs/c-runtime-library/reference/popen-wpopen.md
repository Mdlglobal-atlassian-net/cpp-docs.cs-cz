---
title: "_popen –, _wpopen – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _popen
- _wpopen
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
- tpopen
- popen
- wpopen
- _popen
- _wpopen
- _tpopen
dev_langs: C++
helpviewer_keywords:
- tpopen function
- pipes, creating
- _popen function
- _tpopen function
- popen function
- wpopen function
- _wpopen function
ms.assetid: eb718ff2-c87d-4bd4-bd2e-ba317c3d6973
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 73c9e19556857c78a530f0a2ac89580ea3fec69c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="popen-wpopen"></a>_popen, _wpopen
Vytváří kanál a provede příkaz.  
  
> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```
FILE *_popen(
const char *command,
const char *mode
);
FILE *_wpopen(
const wchar_t *command,
const wchar_t *mode
);
```  
  
#### <a name="parameters"></a>Parametry  
 *příkaz*  
 Příkaz má být proveden.  
  
 *režim*  
 Režim vráceném datovém proudu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrací datový proud přidružený jeden atribut end objektu vytvořený kanál. Konci kanálu je přidružen vytvářený příkaz standardní vstup nebo standardní výstup. Funkce vrátí **NULL** na chybu. Pokud je chyba neplatný parametr, jako třeba když *příkaz* nebo *režimu* je ukazatel s hodnotou null, nebo *režimu* není platný režim `errno` je nastaven na `EINVAL`. Najdete v části poznámky pro režimy platný.  
  
 Informace o těchto a dalších kódy chyb naleznete v tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Poznámky  
 `_popen` Funkce vytváří kanál a asynchronně zpracuje kopie vytvářený procesor příkazů s zadaný řetězec *příkaz*. Řetězec znaků *režimu* Určuje typ přístupu požadovaná následujícím způsobem.  
  
 **"r"**  
 Volající proces může číst standardní výstup příkazu vytvořená pomocí vráceném datovém proudu.  
  
 **"w"**  
 Volající proces může zapisovat do vytvářený příkaz standardní vstup pomocí vráceném datovém proudu.  
  
 **"b"**  
 Otevřete v binárním režimu.  
  
 **"t"**  
 Otevřete v textovém režimu.  
  
> [!NOTE]
>  Pokud se používá v programu systému Windows, `_popen` funkce vrátí souboru je neplatný. ukazatele, který vede k nereaguje po neomezenou dobu. `_popen`funguje správně v konzolové aplikaci. Vytvoření aplikace systému Windows, který provede přesměrování vstupu a výstupu, naleznete v části [vytváření podřízený proces s přesměrování vstupu a výstupu](http://msdn.microsoft.com/library/windows/desktop/ms682499) ve Windows SDK.  
  
 `_wpopen`široká charakterová verze `_popen`; *cesta* argument `_wpopen` je široká charakterová řetězec. `_wpopen`a `_popen` chovat jinak shodně.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tpopen`|`_popen`|`_popen`|`_wpopen`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_popen`|\<stdio.h >|  
|`_wpopen`|\<stdio.h > nebo \<wchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Knihovny  
 Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_popen.c  
/* This program uses _popen and _pclose to receive a   
 * stream of text from a system process.  
 */  
  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
  
   char   psBuffer[128];  
   FILE   *pPipe;  
  
        /* Run DIR so that it writes its output to a pipe. Open this  
         * pipe with read text attribute so that we can read it   
         * like a text file.   
         */  
  
   if( (pPipe = _popen( "dir *.c /on /p", "rt" )) == NULL )  
      exit( 1 );  
  
   /* Read pipe until end of file, or an error occurs. */  
  
   while(fgets(psBuffer, 128, pPipe))  
   {  
      printf(psBuffer);  
   }  
  
   /* Close pipe and print return value of pPipe. */  
   if (feof( pPipe))  
   {  
     printf( "\nProcess returned %d\n", _pclose( pPipe ) );  
   }  
   else  
   {  
     printf( "Error: Failed to read the pipe to the end.\n");  
   }  
}  
```  
  
## <a name="sample-output"></a>Vzorový výstup  
 Tento výstup předpokládá, že se v aktuálním adresáři s příponu názvu souboru .c pouze jeden soubor.  
  
```  
 Volume in drive C is CDRIVE  
 Volume Serial Number is 0E17-1702  
  
 Directory of D:\proj\console\test1  
  
07/17/98  07:26p                   780 popen.c  
               1 File(s)            780 bytes  
                             86,597,632 bytes free  
  
Process returned 0  
```  
  
## <a name="see-also"></a>Viz také  
 [Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)   
 [_pclose –](../../c-runtime-library/reference/pclose.md)   
 [_pipe –](../../c-runtime-library/reference/pipe.md)