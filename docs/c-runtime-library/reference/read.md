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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 2f43fc54a0092afc6ab5855c160a7879747faef7
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919508"
---
# <a name="_read"></a>_read

Načte data ze souboru.

## <a name="syntax"></a>Syntaxe

```C
int _read(
   int const fd,
   void * const buffer,
   unsigned const buffer_size
);
```

### <a name="parameters"></a>Parametry

*FD*<br/>
Popisovač souboru odkazující na otevřený soubor.

*vyrovnávací paměti*<br/>
Umístění úložiště pro data

*buffer_size*<br/>
Maximální počet bajtů, které se mají přečíst

## <a name="return-value"></a>Návratová hodnota

**_read** vrátí počet čtených bajtů, což může být menší než *buffer_size* , pokud je v souboru méně než *buffer_size* bajtů, nebo pokud byl soubor otevřen v textovém režimu. V textovém režimu je každý pár `\r\n` návratových kanálů na řádku nahrazen znakem `\n`s jedním řádkem. V návratové hodnotě se počítá pouze znak jednoduchého čárového kanálu. Náhrada nemá vliv na ukazatel na soubor.

Pokud se funkce pokusí přečíst na konci souboru, vrátí 0. Pokud je *FD* neplatný, soubor není otevřen pro čtení, nebo je soubor uzamčen, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí funkce hodnotu-1 a nastaví **errno** na **EBADF**.

Pokud má *vyrovnávací paměť* **hodnotu null**nebo pokud *buffer_size* > **INT_MAX**, je vyvolána obslužná rutina neplatného parametru. Pokud provádění může pokračovat, funkce vrátí hodnotu-1 a **errno** je nastavena na **EINVAL**.

Další informace o tomto a dalších návratových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Funkce **_read** čte maximálně *buffer_size* bajtů do *vyrovnávací paměti* ze souboru přidruženého ke *FD*. Operace čtení začíná aktuální pozicí ukazatele souboru přidruženého k danému souboru. Po operaci čtení ukazatel na soubor odkazuje na další nepřečtený znak.

Pokud byl soubor otevřen v textovém režimu, je čtení ukončeno, když **_read** nalezne znak CTRL + Z, který je považován za indikátor konce souboru. Pomocí [_lseek](lseek-lseeki64.md) vymažte indikátor konce souboru.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_read**|\<IO. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md).

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

### <a name="input-crt_readtxt"></a>Vstup: crt_read. txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Výstup

```Output
Read 19 bytes from file
```

## <a name="see-also"></a>Viz také

[I/O nízké úrovně](../../c-runtime-library/low-level-i-o.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[fread](fread.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_write](write.md)<br/>
