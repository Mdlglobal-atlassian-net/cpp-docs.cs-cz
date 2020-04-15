---
title: _read
ms.date: 4/2/2020
api_name:
- _read
- _o__read
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
- _read
helpviewer_keywords:
- data [CRT]
- _read function
- read function
- data [C++], reading
- reading data [C++]
- files [C++], reading
ms.assetid: 2ce9c433-57ad-47fe-9ac1-4a7d4c883d30
ms.openlocfilehash: db3726b85bb4ba7c8e9a691bef3fb063ec5709c9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338136"
---
# <a name="_read"></a>_read

Čte data ze souboru.

## <a name="syntax"></a>Syntaxe

```C
int _read(
   int const fd,
   void * const buffer,
   unsigned const buffer_size
);
```

### <a name="parameters"></a>Parametry

*Fd*<br/>
Popisovač souboru odkazující na otevřený soubor.

*Vyrovnávací paměti*<br/>
Umístění úložiště pro data.

*buffer_size*<br/>
Maximální počet přečtených bajtů.

## <a name="return-value"></a>Návratová hodnota

**_read** vrátí počet přečtených bajtů, což může být menší než *buffer_size,* pokud v souboru zbývá méně než *buffer_size* bajtů nebo pokud byl soubor otevřen v textovém režimu. V textovém režimu je každý `\r\n` pár posuvu zpětného `\n`řádku vozíku nahrazen jedním znakem posuzu . V návratové hodnotě se počítá pouze jeden znak posuvu řádku. Nahrazení nemá vliv na ukazatel souboru.

Pokud se funkce pokusí číst na konci souboru, vrátí hodnotu 0. Pokud *fd* není platný, soubor není otevřen pro čtení nebo je soubor uzamčen, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, funkce vrátí -1 a nastaví **errno** na **EBADF**.

Pokud je *vyrovnávací paměť* **null**nebo *buffer_size* > **INT_MAX**, je vyvolána neplatná obslužná rutina parametru. Pokud je spuštění povoleno pokračovat, funkce vrátí -1 a **errno** je nastavena na **EINVAL**.

Další informace o tomto a dalších návratových kódech naleznete [v tématu _doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Funkce **_read** přečte maximálně *buffer_size* bajtů do *vyrovnávací paměti* ze souboru přidruženého k *fd*. Operace čtení začíná na aktuální pozici ukazatele souboru přidruženého k danému souboru. Po operaci čtení ukazatel souboru odkazuje na další nepřečtený znak.

Pokud byl soubor otevřen v textovém režimu, čtení se ukončí, když **_read** narazí na znak CTRL+Z, který je považován za indikátor konce souboru. Pomocí [_lseek](lseek-lseeki64.md) vymažte indikátor konce souboru.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_read**|\<io.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven c run-time](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Příklad

```C
// crt_read.c
/* This program opens a file named crt_read.txt
* and tries to read 60,000 bytes from
* that file using _read. It then displays the
* actual number of bytes read.
*/

#include <fcntl.h>      /* Needed only for _O_RDWR definition */
#include <io.h>
#include <stdlib.h>
#include <stdio.h>
#include <share.h>

char buffer[60000];

int main( void )
{
   int fh, bytesread;
   unsigned int nbytes = 60000;

   /* Open file for input: */
   if ( _sopen_s( &fh, "crt_read.txt", _O_RDONLY, _SH_DENYNO, 0 ))
   {
      perror( "open failed on input file" );
      exit( 1 );
   }

   /* Read in input: */
   if (( bytesread = _read( fh, buffer, nbytes )) <= 0 )
      perror( "Problem reading file" );
   else
      printf( "Read %u bytes from file\n", bytesread );

   _close( fh );
}
```

### <a name="input-crt_readtxt"></a>Vstup: crt_read.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Výstup

```Output
Read 19 bytes from file
```

## <a name="see-also"></a>Viz také

[Vstupně-nosné(v" nízké úrovně](../../c-runtime-library/low-level-i-o.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[fread](fread.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_write](write.md)<br/>
