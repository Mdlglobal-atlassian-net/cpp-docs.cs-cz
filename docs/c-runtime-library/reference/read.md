---
title: _read
ms.date: 02/13/2019
apiname:
- _read
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
- _read
helpviewer_keywords:
- data [CRT]
- _read function
- read function
- data [C++], reading
- reading data [C++]
- files [C++], reading
ms.assetid: 2ce9c433-57ad-47fe-9ac1-4a7d4c883d30
ms.openlocfilehash: 40f52ea37ae5419fe986aa505aad4fddfe8403ff
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62357652"
---
# <a name="read"></a>_read

Přečte data ze souboru.

## <a name="syntax"></a>Syntaxe

```C
int _read(
   int const fd,
   void * const buffer,
   unsigned const buffer_size
);
```

### <a name="parameters"></a>Parametry

*fd*<br/>
Popisovač souboru odkazující na otevřený soubor.

*Vyrovnávací paměti*<br/>
Umístění úložiště pro data.

*buffer_size*<br/>
Maximální počet bajtů ke čtení.

## <a name="return-value"></a>Návratová hodnota

**_získat** vrátí počet bajtů, přečtěte si, který může být menší než *buffer_size* Pokud jsou kratší než *buffer_size* left bajtů v souboru, nebo pokud byl soubor otevřen v textovém režimu. V textovém režimu, každý návrat na začátek řádku return-LF pár `\r\n` nahradí znak odřádkování jeden `\n`. Pouze jeden znak odřádkování znak, který se počítá v návratové hodnotě. Pokud chcete nahrazení nemá vliv na ukazatel na soubor.

Pokud funkce se pokusí načíst na konci souboru, vrátí hodnotu 0. Pokud *fd* není platný soubor není otevřen pro čtení, nebo je soubor uzamčen, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, vrátí funkce hodnotu -1 a nastaví **errno** k **EBADF**.

Pokud *vyrovnávací paměti* je **NULL**, nebo pokud *buffer_size* > **INT_MAX**, je vyvolána obslužná rutina neplatného parametru. Pokud smí provádění pokračovat, vrátí funkce hodnotu -1 a **errno** je nastavena na **EINVAL**.

Další informace o tomto a dalších návratových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

**_Read** funkce přečte maximálně *buffer_size* bajtů do *vyrovnávací paměti* ze souboru spojené s *fd*. Operace čtení začíná na aktuální pozici ukazatele soubor přidružený k danému souboru. Po operaci čtení ukazatel na soubor odkazuje na další nepřečtené znak.

Pokud soubor byl otevřen v textovém režimu, čtení skončí, když **_read** zaznamená znak CTRL + Z, která se používá jako indikátor konce souboru. Použití [_lseek –](lseek-lseeki64.md) zrušte indikátor konce souboru.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_read**|\<io.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md).

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

### <a name="input-crtreadtxt"></a>Vstup: crt_read.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Výstup

```Output
Read 19 bytes from file
```

## <a name="see-also"></a>Viz také:

[I/O nízké úrovně](../../c-runtime-library/low-level-i-o.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[fread](fread.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_write](write.md)<br/>
