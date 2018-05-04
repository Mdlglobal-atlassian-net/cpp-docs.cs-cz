---
title: _set_fmode – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _set_fmode
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
- _set_fmode
- set_fmode
dev_langs:
- C++
helpviewer_keywords:
- file translation [C++], default mode
- _set_fmode function
- file translation [C++], setting mode
- set_fmode function
ms.assetid: f80eb9c7-733b-4652-a9bc-6b3790a35f12
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 64b8be6d678a6907fc63018c99dd38d2fc8407ea
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="setfmode"></a>_set_fmode

Nastaví výchozí režim překladu souboru pro vstupně-výstupní operace.

## <a name="syntax"></a>Syntaxe

```C
errno_t _set_fmode( 
   int mode 
);
```

### <a name="parameters"></a>Parametry

*Režim*<br/>
Režim překladu souboru požadovaného: **_o_text –** nebo **_o_binary –**.

## <a name="return-value"></a>Návratová hodnota

Vrátí nula v případě úspěchu, kód chyby při selhání. Pokud *režimu* není **_o_text –** nebo **_o_binary –** nebo **_O_WTEXT**, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, tato funkce nastaví **errno** k **einval –** a vrátí **einval –**.

## <a name="remarks"></a>Poznámky

Nastaví funkce [_fmode –](../../c-runtime-library/fmode.md) – globální proměnná. Tato proměnná Určuje výchozí režim překladu souboru pro vstupně-výstupní operace **_Otevřít** a **_pipe –**.

**_O_text –** a **_o_binary –** jsou definovány v Fcntl.h. **Einval –** je definována v Errno.h.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Nepovinné hlavičkové|
|-------------|---------------------|---------------------|
|**_set_fmode**|\<stdlib.h>|\<fcntl.h>, \<errno.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_set_fmode.c
#include <stdlib.h>
#include <stdio.h>
#include <fcntl.h>     /* for _O_TEXT and _O_BINARY */
#include <errno.h>     /* for EINVAL */
#include <sys\stat.h>  /* for _S_IWRITE */
#include <share.h>     /* for _SH_DENYNO */

int main()
{
   int mode, fd, ret;
   errno_t err;
   int buf[12] = { 65, 66, 67, 68, 69, 70, 71, 72, 73, 74,
                   75, 76 };
   char * filename = "fmode.out";

   err = _get_fmode(&mode);
   if (err == EINVAL)
   {
      printf( "Invalid parameter: mode\n");
      return 1;
   }
   else
      printf( "Default Mode is %s\n", mode == _O_TEXT ? "text" :
              "binary");

   err = _set_fmode(_O_BINARY);
   if (err == EINVAL)
   {
      printf( "Invalid mode.\n");
      return 1;
   }

   if ( _sopen_s(&fd, filename, _O_RDWR | _O_CREAT, _SH_DENYNO, _S_IWRITE | _S_IREAD) != 0 )
   {
      printf( "Error opening the file %s\n", filename);
      return 1;
   }

   if (ret = _write(fd, buf, 12*sizeof(int)) < 12*sizeof(int))
   {
      printf( "Problem writing to the file %s.\n", filename);
      printf( "Number of bytes written: %d\n", ret);
   }

   if (_close(fd) != 0)
   {
      printf("Error closing the file %s. Error code %d.\n",
             filename, errno);
   }

   system("type fmode.out");
}
```

```Output
Default Mode is binary
A   B   C   D   E   F   G   H   I   J   K   L
```

## <a name="see-also"></a>Viz také

[_fmode](../../c-runtime-library/fmode.md)<br/>
[_get_fmode](get-fmode.md)<br/>
[_setmode](setmode.md)<br/>
[I/O soubor textového a binárního režimu](../../c-runtime-library/text-and-binary-mode-file-i-o.md)<br/>
