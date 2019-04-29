---
title: _write
ms.date: 11/04/2016
apiname:
- _write
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
- _write
helpviewer_keywords:
- _write function
- write function
- files [C++], writing to
ms.assetid: 7b868c33-766f-4e1a-95a7-e8d25f0604c4
ms.openlocfilehash: b3fa53b21d4ea23c5f8e59de673f4074deedb505
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383409"
---
# <a name="write"></a>_write

Zapíše data do souboru.

## <a name="syntax"></a>Syntaxe

```C
int _write(
   int fd,
   const void *buffer,
   unsigned int count
);
```

### <a name="parameters"></a>Parametry

*fd*<br/>
Popisovač souboru, do kterého se data zapisují souboru.

*Vyrovnávací paměti*<br/>
Data k zapsání.

*Počet*<br/>
Počet bajtů.

## <a name="return-value"></a>Návratová hodnota

V případě úspěšného ověření **_write** vrátí počet aktuálně zapsaných bajtů. Pokud skutečné zbývající místo na disku je menší než velikost vyrovnávací paměti pro funkci je při zápisu na disk, **_write** nezdaří a není vyprázdnit všechny přípravné vyrovnávací paměti obsah na disku. Návratová hodnota-1 označuje chybu. Pokud jsou předány neplatné parametry, tato funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, vrátí funkce hodnotu -1 a **errno** nastavena na jednu ze tří hodnot: **EBADF**, což znamená, že popisovač souboru je neplatná nebo soubor není otevřen pro zápis; **ENOSPC**, což znamená, že není k dispozici dostatek volného místa na zařízení pro operaci; nebo **EINVAL**, což znamená, že *vyrovnávací paměti* byl ukazatel s hodnotou null nebo který odlišným *počet* bajtů byl předán k zápisu do souboru v režimu Unicode.

Další informace o těchto a dalších návratových kódech naleznete v tématu [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Pokud je soubor otevřený v textovém režimu, každý znak odřádkování nahrazena návrat vozíku - odřádkování pár ve výstupu. Nahrazení nemá vliv na návratovou hodnotu.

Když je soubor otevřen v režimu Unicode překladu – například pokud *fd* otevřen použitím **_Otevřít** nebo **_sopen** a režim parametr, který zahrnuje **_O_ WTEXT**, **_O_U16TEXT**, nebo **_O_U8TEXT**, nebo pokud je otevřen pomocí **fopen** a režim parametr, který zahrnuje **ccs = Kódování UNICODE**, **ccs = UTF-16LE**, nebo **ccs = UTF-8**, nebo pokud je režim změnit na režim překladu Unicode pomocí **_setmode**–*vyrovnávací paměti* je interpretován jako ukazatel na pole **wchar_t** obsahující **UTF-16** data. Pokus o zápis lichý počet bajtů v tomto režimu způsobí chybu ověření parametru.

## <a name="remarks"></a>Poznámky

**_Write** funkce zápisy *počet* bajtů z *vyrovnávací paměti* do souboru spojené s *fd*. Zahájení operace zápisu na aktuální pozici ukazatele souboru (pokud existuje) přidružené k danému souboru. Pokud je soubor otevřen pro připojení, zahájení operace na konci aktuálního souboru. Po provedení této operace zápisu ukazatel na soubor je zvýšen počet aktuálně zapsaných bajtů.

Při zápisu do soubory otevřené v režimu textu **_write** zpracovává znak CTRL + Z jako logické koncoví souboru. Při zápisu do zařízení, **_write** zpracovává znak CTRL + Z ve vyrovnávací paměti jako výstupu ukončovací znak.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_write**|\<io.h>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt__write.c
//
// This program opens a file for output and uses _write to write
// some bytes to the file.

#include <io.h>
#include <stdio.h>
#include <stdlib.h>
#include <fcntl.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <errno.h>
#include <share.h>

char buffer[] = "This is a test of '_write' function";

int main( void )
{
   int         fileHandle = 0;
   unsigned    bytesWritten = 0;

   if ( _sopen_s(&fileHandle, "write.o", _O_RDWR | _O_CREAT,
                  _SH_DENYNO, _S_IREAD | _S_IWRITE) )
      return -1;

   if (( bytesWritten = _write( fileHandle, buffer, sizeof( buffer ))) == -1 )
   {
      switch(errno)
      {
         case EBADF:
            perror("Bad file descriptor!");
            break;
         case ENOSPC:
            perror("No space left on device!");
            break;
         case EINVAL:
            perror("Invalid parameter: buffer was NULL!");
            break;
         default:
            // An unrelated error occured
            perror("Unexpected error!");
      }
   }
   else
   {
      printf_s( "Wrote %u bytes to file.\n", bytesWritten );
   }
   _close( fileHandle );
}
```

```Output
Wrote 36 bytes to file.
```

## <a name="see-also"></a>Viz také:

[I/O nízké úrovně](../../c-runtime-library/low-level-i-o.md)<br/>
[fwrite](fwrite.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_read](read.md)<br/>
[_setmode](setmode.md)<br/>
