---
title: _chdir –, _wchdir – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wchdir
- _chdir
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- tchdir
- _chdir
- _wchdir
- _tchdir
- wchdir
dev_langs:
- C++
helpviewer_keywords:
- _tchdir function
- _chdir function
- _wchdir function
- tchdir function
- wchdir function
- chdir function
- directories [C++], changing
ms.assetid: 85e9393b-62ac-45d5-ab2a-fa2217f6152e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b81ace9c9fe5cf21d93f7e7dd4a8b5f2f2c5d726
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2018
---
# <a name="chdir-wchdir"></a>_chdir, _wchdir

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

*adresář*<br/>
Cesta nové pracovní adresář.

## <a name="return-value"></a>Návratová hodnota

Tyto funkce vrátit hodnotu 0, pokud bylo úspěšné. Vrácená hodnota -1 označuje selhání. Pokud zadaná cesta nebyla nalezena, **errno** je nastaven na **enoent –**. Pokud *adresář* je **NULL**, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění **errno** je nastaven na **einval –** a funkce vrátí hodnotu -1.

## <a name="remarks"></a>Poznámky

**_Chdir –** funkce změní aktuální pracovní adresář na adresář zadaný *adresář*. *Adresář* parametr musí odkazovat na existující adresář. Tuto funkci můžete změnit aktuální pracovní adresář na žádné jednotky. Jestliže se v nové písmeno jednotky *adresář*, je také změnit výchozí písmeno jednotky. Například pokud A je výchozí písmeno jednotky a \BIN je aktuální pracovní adresář, následující volání změny aktuální pracovní adresář pro jednotky C: a vytváří C jako nový výchozí jednotce:

```C
_chdir("c:\temp");
```

Při použití volitelné lomítka (**&#92;**) v cestách, je nutné umístit dvě zpětná lomítka (**&#92;&#92;**) v C řetězcový literál představují jeden zpětné lomítko ( **&#92;**).

**_wchdir –** je verze široká charakterová **_chdir –**; *adresář* argument **_wchdir –** je široká charakterová řetězec. **_wchdir –** a **_chdir –** chovat jinak shodně.

### <a name="generic-text-routine-mapping"></a>Mapování obecného textu rutiny:

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tchdir –**|**_chdir**|**_chdir**|**_wchdir**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Nepovinné hlavičkové|
|-------------|---------------------|---------------------|
|**_chdir**|\<Direct.h >|\<errno.h>|
|**_wchdir**|\<Direct.h > nebo \<wchar.h >|\<errno.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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

[Ovládací prvek adresáře](../../c-runtime-library/directory-control.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_rmdir, _wrmdir](rmdir-wrmdir.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
