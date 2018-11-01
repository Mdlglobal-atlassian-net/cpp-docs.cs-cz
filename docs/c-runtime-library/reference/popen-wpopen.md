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
ms.openlocfilehash: 5284685f56a73c4c7e48fce981745220651399a1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50498901"
---
# <a name="popen-wpopen"></a>_popen, _wpopen

Vytvoří kanál a spustí příkaz.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*Příkaz*<br/>
Příkaz má být proveden.

*Režim*<br/>
Režim vráceném datovém proudu.

## <a name="return-value"></a>Návratová hodnota

Vrací datový proud přidružený jeden konec vytvořený kanál. Druhém konci kanálu souvisí s vytvářené příkaz standardní vstup nebo standardní výstup. Funkce vrací **NULL** na chybu. Pokud je chyba neplatného parametru, například když *příkaz* nebo *režimu* je ukazatel s hodnotou null, nebo *režimu* není platný režim **errno** nastavený na **EINVAL**. Platné režimy v části poznámky.

Informace o těchto a dalších chybových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

**_Popen –** funkce vytvoří kanál a asynchronně spustí kopii příkazového procesoru pomocí zadaného řetězce vytvářené *příkaz*. Řetězec znaků *režimu* Určuje typ přístupu požadovaná následujícím způsobem.

|Režim přístupu|Popis|
|-|-|
|**"r"**|Standardní výstup příkazu vytvářené pomocí vrácený datový proud může číst volající proces.|
|**"w"**|Volající proces může zapisovat do nové kopie příkaz standardní vstup pomocí vráceném datovém proudu.|
|**"b"**|Otevřít v binárním režimu.|
|**"t"**|Otevřít v textovém režimu.|

> [!NOTE]
> Pokud se používá v programu Windows, **_popen –** funkce vrací neplatný ukazatel na soubor, který způsobí, že program přestane reagovat bez omezení. **_popen –** v konzolové aplikaci funguje správně. Vytvoření aplikace Windows v jazyce, který provede přesměrování vstupu a výstupu najdete v tématu [vytváření podřízeného procesu s přesměrování vstupu a výstupu](/windows/desktop/ProcThread/creating-a-child-process-with-redirected-input-and-output) v sadě Windows SDK.

**_wpopen –** je verze širokého znaku **_popen –**; *cesta* argument **_wpopen –** je širokoznaký řetězec. **_wpopen –** a **_popen –** se jinak chovají stejně.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tpopen –**|**_popen**|**_popen**|**_wpopen**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_popen**|\<stdio.h>|
|**_wpopen**|\<stdio.h > nebo \<wchar.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md).

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

Tento výstup se předpokládá, že je pouze jeden soubor s příponou názvu souboru .c do aktuálního adresáře.

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
