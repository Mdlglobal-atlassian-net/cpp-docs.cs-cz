---
title: _popen, _wpopen
ms.date: 11/04/2016
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
helpviewer_keywords:
- tpopen function
- pipes, creating
- _popen function
- _tpopen function
- popen function
- wpopen function
- _wpopen function
ms.assetid: eb718ff2-c87d-4bd4-bd2e-ba317c3d6973
ms.openlocfilehash: 03eb36573abe8e26c47e6dd38c009e5819e60f8f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69499601"
---
# <a name="_popen-_wpopen"></a>_popen, _wpopen

Vytvoří kanál a provede příkaz.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
FILE *_popen(
    const char *command,
    const char *mode
);
FILE *_wpopen(
    const wchar_t *command,
    const wchar_t *mode
);
```

### <a name="parameters"></a>Parametry

*systému*<br/>
Příkaz, který má být spuštěn.

*Mode*<br/>
Režim vráceného datového proudu.

## <a name="return-value"></a>Návratová hodnota

Vrátí datový proud přidružený k jednomu konci vytvořeného kanálu. Druhý konec kanálu je přidružený ke standardnímu vstupnímu nebo standardnímu výstupu příkazu vytvořenému příkazem. Funkce vrací **hodnotu null** u chyby. Pokud je chyba neplatným parametrem, například pokud je *příkaz* nebo *režim* ukazatel s hodnotou null, nebo *režim* není platným režimem, **errno** je nastaven na **EINVAL**. Platné režimy najdete v části s poznámkami.

Informace o těchto a dalších chybových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Funkce **_popen** vytvoří kanál a asynchronně spustí vytvořenou kopii příkazového procesoru se zadaným řetězcovým *příkazem*. *Režim* řetězce znaků Určuje typ požadovaného přístupu, jak je uvedeno níže.

|Režim přístupu|Popis|
|-|-|
|**í**|Volající proces může přečíst standardní výstup příkazu vytvořený pomocí vráceného datového proudu.|
|**"w"**|Volající proces může zapisovat do standardního vstupu příkazu vytvořeného pomocí vráceného datového proudu.|
|**b**|Otevřete v binárním režimu.|
|**š**|Otevřete v textovém režimu.|

> [!NOTE]
> Při použití v programu systému Windows vrátí funkce **_popen** neplatný ukazatel na soubor, který způsobí, že program přestane reagovat po neomezenou dobu. **_popen** funguje správně v konzolové aplikaci. Chcete-li vytvořit aplikaci systému Windows, která přesměruje vstup a výstup, viz téma [Vytvoření podřízeného procesu s přesměrovaným vstupem a výstupem](/windows/win32/ProcThread/creating-a-child-process-with-redirected-input-and-output) v Windows SDK.

**_wpopen** je **_popen**verze s velkým znakem; Argument *cesty* pro **_wpopen** je řetězec s velkým znakem. **_wpopen** a **_popen** se chovají stejně jinak.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tpopen**|**_popen**|**_popen**|**_wpopen**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_popen**|\<stdio.h>|
|**_wpopen**|\<stdio. h > nebo \<WCHAR. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Příklad

```C
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

### <a name="sample-output"></a>Vzorový výstup

Tento výstup předpokládá, že v aktuálním adresáři je pouze jeden soubor s příponou názvu souboru. c.

```Output
Volume in drive C is CDRIVE
Volume Serial Number is 0E17-1702

Directory of D:\proj\console\test1

07/17/98  07:26p                   780 popen.c
               1 File(s)            780 bytes
                             86,597,632 bytes free

Process returned 0
```

## <a name="see-also"></a>Viz také:

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[_pclose](pclose.md)<br/>
[_pipe](pipe.md)<br/>
