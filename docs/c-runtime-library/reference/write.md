---
title: _write
ms.date: 4/2/2020
api_name:
- _write
- _o__write
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
- _write
helpviewer_keywords:
- _write function
- write function
- files [C++], writing to
ms.assetid: 7b868c33-766f-4e1a-95a7-e8d25f0604c4
ms.openlocfilehash: a616df570d266c335337d897da59a2a0ec69b40e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367397"
---
# <a name="_write"></a>_write

Zapisuje data do souboru.

## <a name="syntax"></a>Syntaxe

```C
int _write(
   int fd,
   const void *buffer,
   unsigned int count
);
```

### <a name="parameters"></a>Parametry

*Fd*<br/>
Popisovač souboru, do kterého jsou data zapsána.

*Vyrovnávací paměti*<br/>
Data, která mají být zapsána.

*Počet*<br/>
Počet bajtů.

## <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, **vrátí _write** počet zapsaných bajtů. Pokud skutečné místo zbývající na disku je menší než velikost vyrovnávací paměti funkce se pokouší zapsat na disk, **_write** selže a nevyprázdní žádný obsah vyrovnávací paměti na disk. Vrácená hodnota -1 označuje chybu. Pokud jsou předány neplatné parametry, tato funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v [parametru Validation](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, funkce vrátí -1 a **errno** je nastavena na jednu ze tří hodnot: **EBADF**, což znamená, že popisovač souboru je neplatný nebo soubor není otevřen pro zápis; **ENOSPC**, což znamená, že na zařízení není dostatek místa pro provoz; nebo **EINVAL**, což znamená, že *vyrovnávací paměť* byla nulovým ukazatelem nebo že byl předán lichý *počet* bajtů, které mají být zapsány do souboru v režimu Unicode.

Další informace o těchto a dalších návratových kódech naleznete [v tématech errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Pokud je soubor otevřen v textovém režimu, každý znak podavače řádků je nahrazen dvojicí zpětného podávacího kanálu vozíku ve výstupu. Nahrazení nemá vliv na vrácenou hodnotu.

Když je soubor otevřen v režimu překladu Unicode – například Pokud *fd* je otevřen pomocí **_open** nebo **_sopen** a parametr režimu, který zahrnuje **_O_WTEXT**, **_O_U16TEXT**nebo **_O_U8TEXT**, nebo pokud je otevřen pomocí **fopen** a parametr režimu, který zahrnuje **ccs = UNICODE**, **ccs = UTF-16LE**, nebo **ccs = UTF-8**, nebo pokud je režim změněn na režim překladu Unicode pomocí **_setmode**—*vyrovnávací paměť* je interpretován jako ukazatel na pole **wchar_t,** který obsahuje **UTF-16** data. Pokus o zápis lichého počtu bajtů v tomto režimu způsobí chybu ověření parametru.

## <a name="remarks"></a>Poznámky

Funkce **_write** zapisuje *počet* *bajtů* z vyrovnávací paměti do souboru přidruženého k *fd*. Operace zápisu začíná na aktuální pozici ukazatele souboru (pokud existuje) přidružené k danému souboru. Pokud je soubor otevřen pro připojení, operace začíná na aktuálním konci souboru. Po operaci zápisu se ukazatel souboru zvýší o počet zapsaných bajtů.

Při zápisu do souborů otevřených v textovém režimu **_write** považuje znak CTRL+Z za logický konec souboru. Při zápisu do zařízení **_write** zachází se znakem CTRL+Z ve vyrovnávací paměti jako s zakončením výstupu.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_write**|\<io.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

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
            // An unrelated error occurred
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

## <a name="see-also"></a>Viz také

[Vstupně-nosné(v" nízké úrovně](../../c-runtime-library/low-level-i-o.md)<br/>
[fwrite](fwrite.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_read](read.md)<br/>
[_setmode](setmode.md)<br/>
