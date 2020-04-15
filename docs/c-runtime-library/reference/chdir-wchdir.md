---
title: _chdir, _wchdir
ms.date: 4/2/2020
api_name:
- _wchdir
- _chdir
- _o__chdir
- _o__wchdir
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
- api-ms-win-crt-filesystem-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- tchdir
- _chdir
- _wchdir
- _tchdir
- wchdir
helpviewer_keywords:
- _tchdir function
- _chdir function
- _wchdir function
- tchdir function
- wchdir function
- chdir function
- directories [C++], changing
ms.assetid: 85e9393b-62ac-45d5-ab2a-fa2217f6152e
ms.openlocfilehash: a3f224e68e4b5a43274616892012ceba737d6d17
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333390"
---
# <a name="_chdir-_wchdir"></a>_chdir, _wchdir

Změní aktuální pracovní adresář.

## <a name="syntax"></a>Syntaxe

```C
int _chdir(
   const char *dirname
);
int _wchdir(
   const wchar_t *dirname
);
```

### <a name="parameters"></a>Parametry

*dirname*<br/>
Cesta nového pracovního adresáře.

## <a name="return-value"></a>Návratová hodnota

Tyto funkce vrátí hodnotu 0 v případě úspěchu. Vrácená hodnota -1 označuje selhání. Pokud zadanou cestu nelze najít, je **chybná cesta** nastavena na **eNOENT**. Pokud *dirname* je **NULL**, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, **errno** je nastavena na **EINVAL** a funkce vrátí -1.

## <a name="remarks"></a>Poznámky

Funkce **_chdir** změní aktuální pracovní adresář na adresář určený *dirnamem*. Parametr *dirname* musí odkazovat na existující adresář. Tato funkce může změnit aktuální pracovní adresář na libovolné jednotce. Pokud je v *dirname*zadáno nové písmeno jednotky , změní se také výchozí písmeno jednotky. Pokud je například A výchozím písmenem jednotky a \BIN je aktuální pracovní adresář, následující volání změní aktuální pracovní adresář pro jednotku C a vytvoří c jako novou výchozí jednotku:

```C
_chdir("c:\temp");
```

Při použití volitelného znaku zpětného lomítka (**&#92;**) v cestách, musíte umístit dvě zpětná lomítka** (&#92;&#92;**) v literálu řetězce C, aby reprezentovala jedno zpětné lomítko (**&#92;**).

**_wchdir** je širokoznaková verze **_chdir**; *dirname* argument **_wchdir** je řetězec široký znak. **_wchdir** a **_chdir** se chovají stejně jinak.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mapping"></a>Mapování rutiny obecného textu:

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tchdir**|**_chdir**|**_chdir**|**_wchdir**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelná hlavička|
|-------------|---------------------|---------------------|
|**_chdir**|\<direct.h>|\<errno.h>|
|**_wchdir**|\<direct.h> \<nebo wchar.h>|\<errno.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_chdir.c
// arguments: C:\WINDOWS

/* This program uses the _chdir function to verify
   that a given directory exists. */

#include <direct.h>
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

int main( int argc, char *argv[] )
{

   if(_chdir( argv[1] ) )
   {
      switch (errno)
      {
      case ENOENT:
         printf( "Unable to locate the directory: %s\n", argv[1] );
         break;
      case EINVAL:
         printf( "Invalid buffer.\n");
         break;
      default:
         printf( "Unknown error.\n");
      }
   }
   else
      system( "dir *.exe");
}
```

```Output
Volume in drive C has no label.
Volume Serial Number is 2018-08A1

Directory of c:\windows

08/29/2002  04:00 AM         1,004,032 explorer.exe
12/17/2002  04:43 PM            10,752 hh.exe
03/03/2003  09:24 AM            33,792 ieuninst.exe
10/29/1998  04:45 PM           306,688 IsUninst.exe
08/29/2002  04:00 AM            66,048 NOTEPAD.EXE
03/03/2003  09:24 AM            33,792 Q330994.exe
08/29/2002  04:00 AM           134,144 regedit.exe
02/28/2003  06:26 PM            46,352 setdebug.exe
08/29/2002  04:00 AM            15,360 TASKMAN.EXE
08/29/2002  04:00 AM            49,680 twunk_16.exe
08/29/2002  04:00 AM            25,600 twunk_32.exe
08/29/2002  04:00 AM           256,192 winhelp.exe
08/29/2002  04:00 AM           266,752 winhlp32.exe
              13 File(s)      2,249,184 bytes
               0 Dir(s)  67,326,029,824 bytes free
```

## <a name="see-also"></a>Viz také

[Řízení adresářů](../../c-runtime-library/directory-control.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_rmdir, _wrmdir](rmdir-wrmdir.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
