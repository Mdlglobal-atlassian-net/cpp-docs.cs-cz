---
title: _write
ms.date: 11/04/2016
api_name:
- _write
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
ms.openlocfilehash: 5eaee64c1bf6ad4b4d59c3a7b1a1434741e74454
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821789"
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

*fd*<br/>
Popisovač souboru, do kterého se zapisují data

*vyrovnávací paměti*<br/>
Data, která mají být zapsána.

*výpočtu*<br/>
Počet bajtů

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu **_Write** vrátí počet zapsaných bajtů. Pokud je aktuální místo na disku menší než velikost vyrovnávací paměti, kterou se funkce pokouší zapsat na disk, **_Write** selžou a neuvolní žádný obsah vyrovnávací paměti na disk. Návratová hodnota-1 označuje chybu. Pokud jsou předány neplatné parametry, tato funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, funkce vrátí hodnotu-1 a **errno** je nastavena na jednu ze tří hodnot: **EBADF**, což znamená, že popisovač souboru je neplatný nebo soubor není otevřen pro zápis. **ENOSPC**, což znamená, že na zařízení není k dispozici dostatek místa pro operaci; nebo **EINVAL**, což znamená, že *vyrovnávací paměť* byla ukazatel s hodnotou null nebo byl před zápisem do souboru v režimu Unicode předán lichý *počet* bajtů.

Další informace o těchto a dalších návratových kódech naleznete v tématu [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Pokud je soubor otevřen v textovém režimu, je každý znak kanálu řádku nahrazen dvojicí kanálu návratového řádku ve výstupu. Náhrada nemá vliv na vrácenou hodnotu.

Když je soubor otevřen v režimu překladu Unicode – například je-li *FD* otevřen pomocí **_open** nebo **_sopen** a parametr režimu, který zahrnuje **_O_WTEXT**, **_O_U16TEXT**nebo **_O_U8TEXT**, nebo pokud je otevřen pomocí **FOPEN** a parametr režimu, který obsahuje **CCS = Unicode**, **CCS = UTF-16LE**nebo **CCS = UTF-8**nebo pokud je režim změněn na režim překladu Unicode pomocí **_setmode**–*vyrovnávací paměť* je interpretována jako ukazatel na pole **wchar_t** obsahující data **UTF-16** . Pokus o zápis lichého počtu bajtů v tomto režimu způsobí chybu ověření parametru.

## <a name="remarks"></a>Poznámky

Funkce **_Write** zapisuje *počet* bajtů z *vyrovnávací paměti* do souboru přidruženého ke *FD*. Operace zápisu začíná na aktuální pozici ukazatele souboru (pokud existuje) přidruženého k danému souboru. Pokud je soubor otevřen pro připojení, operace začíná na aktuálním konci souboru. Po operaci zápisu se ukazatel na soubor zvýší o počet zapsaných bajtů.

Při zápisu do souborů otevřených v textovém režimu **_Write** považovat znak CTRL + Z za logický konec souboru. Při zápisu do zařízení **_Write** považovat znak CTRL + Z ve vyrovnávací paměti jako ukončovací výstup.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_write**|\<io.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také:

[I/O nízké úrovně](../../c-runtime-library/low-level-i-o.md)<br/>
[fwrite](fwrite.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_read](read.md)<br/>
[_setmode](setmode.md)<br/>
