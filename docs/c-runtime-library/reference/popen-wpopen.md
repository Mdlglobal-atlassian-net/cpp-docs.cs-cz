---
title: _popen, _wpopen
description: Odkaz na funkce _popen knihovny runtime (Microsoft _wpopenC) a .
ms.date: 4/2/2020
api_name:
- _popen
- _wpopen
- _o__popen
- _o__wpopen
api_location:
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
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
no-loc:
- _popen
- _wpopen
- _tpopen
- _doserrno
- errno
- _sys_errlist
- _sys_nerr
- EINVAL
ms.openlocfilehash: 5b478893ef8f201f39cb63ecfc7ab174d16b86de
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338504"
---
# <a name="_popen-_wpopen"></a>_popen, _wpopen

Vytvoří kanál a provede příkaz.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime. Další informace naleznete v tématu [funkce CRT, které nejsou podporovány v aplikacích univerzální platformy Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*Příkaz*\
Příkaz, který má být proveden.

*Režimu*\
Režim vráceného datového proudu.

## <a name="return-value"></a>Návratová hodnota

Vrátí datový proud přidružený k jednomu konci vytvořeného kanálu. Druhý konec kanálu je spojen se standardním vstupem nebo standardním výstupem příkazu. Funkce vrátí **hodnotu NULL** při chybě. Pokud je chyba způsobena neplatným parametrem, **je errno** nastaveno na **EINVAL**. Platné režimy naleznete v části Poznámky.

Informace o těchto a dalších kódech chyb naleznete [v tématu _doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Funkce **_popen** vytvoří potrubí. Potom asynchronně provede zplozenou kopii příkazového procesoru a použije *příkaz* jako příkazový řádek. *Režim* řetězce znaků určuje typ požadovaného přístupu následujícím způsobem.

|Režim přístupu|Popis|
|-|-|
|**"r"**|Volající proces můžete číst zplodil příkazu standardní výstup pomocí vráceného datového proudu.|
|**"w"**|Volající proces můžete zapisovat do standardního vstupu příkazu spawned pomocí vráceného datového proudu.|
|**"b"**|Otevřít v binárním režimu.|
|**"t"**|Otevřít v textovém režimu.|

> [!NOTE]
> Pokud je funkce **systému** Windows použita, vrátí funkce _popen neplatný ukazatel souboru, který způsobí, že program přestane reagovat neomezeně dlouho. **_popen** funguje správně v konzolové aplikaci. Chcete-li vytvořit aplikaci systému Windows, která přesměruje vstup a výstup, přečtěte si informace o [vytvoření podřízeného procesu s přesměrovanou vstupní a výstupní](/windows/win32/ProcThread/creating-a-child-process-with-redirected-input-and-output) sadou Windows VDK.

**_wpopen** je širokoznaková verze **_popen**; argument *cesty* k **_wpopen** je řetězec s širokým znakem. **_wpopen** a **_popen** se chovají stejně jinak.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tpopen**|**_popen**|**_popen**|**_wpopen**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_popen**|\<stdio.h>|
|**_wpopen**|\<stdio.h> \<nebo wchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven c run-time](../../c-runtime-library/crt-library-features.md).

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
      puts(psBuffer);
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

Tento výstup předpokládá, že v aktuálním adresáři `.c` je pouze jeden soubor, který má příponu názvu souboru.

```Output
Volume in drive C is CDRIVE
Volume Serial Number is 0E17-1702

Directory of D:\proj\console\test1

07/17/98  07:26p                   780 popen.c
               1 File(s)            780 bytes
                             86,597,632 bytes free

Process returned 0
```

## <a name="see-also"></a>Viz také

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)\
[_pclose](pclose.md)\
[_pipe](pipe.md)
