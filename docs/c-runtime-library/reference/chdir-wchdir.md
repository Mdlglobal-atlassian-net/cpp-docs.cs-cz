---
title: "_chdir –, _wchdir – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 37cb327b13fafafdb357a6a53f624c494ee317b6
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="chdir-wchdir"></a>_chdir, _wchdir
Změní aktuální pracovní adresář.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _chdir(   
   const char *dirname   
);  
int _wchdir(   
   const wchar_t *dirname   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dirname`  
 Cesta nové pracovní adresář.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tyto funkce vrátit hodnotu 0, pokud bylo úspěšné. Vrácená hodnota -1 označuje selhání. Pokud zadaná cesta nebyla nalezena, `errno` je nastaven na `ENOENT`. Pokud `dirname` má hodnotu NULL, je vyvolána obslužná rutina neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění `errno` je nastaven na `EINVAL` a funkce vrátí hodnotu -1.  
  
## <a name="remarks"></a>Poznámky  
 `_chdir` Funkce změní aktuální pracovní adresář na adresář zadaný `dirname`. `dirname` Parametr musí odkazovat na existující adresář. Tuto funkci můžete změnit aktuální pracovní adresář na žádné jednotky. Jestliže se v nové písmeno jednotky `dirname`, je také změnit výchozí písmeno jednotky. Například pokud A je výchozí písmeno jednotky a \BIN je aktuální pracovní adresář, následující volání změny aktuální pracovní adresář pro jednotky C: a vytváří C jako nový výchozí jednotce:  
  
```  
_chdir("c:\\temp");  
```  
  
 Při použití volitelné lomítka (`\`) v cestách, je nutné umístit dvě zpětná lomítka (`\\`) v C řetězcový literál představují jeden zpětné lomítko (`\`).  
  
 `_wchdir` široká charakterová verze `_chdir`; `dirname` argument `_wchdir` je řetězec znaků celou`. _wchdir` a `_chdir` chovat jinak shodně.  
  
### <a name="generic-text-routine-mapping"></a>Mapování obecného textu rutiny:  
  
|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tchdir`|`_chdir`|`_chdir`|`_wchdir`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|Nepovinné hlavičkové|  
|-------------|---------------------|---------------------|  
|`_chdir`|\<direct.h>|\<errno.h>|  
|`_wchdir`|\<Direct.h > nebo \<wchar.h >|\<errno.h>|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
  
```  
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
 [Ovládací prvek adresáře](../../c-runtime-library/directory-control.md)   
 [_mkdir, _wmkdir](../../c-runtime-library/reference/mkdir-wmkdir.md)   
 [_rmdir, _wrmdir](../../c-runtime-library/reference/rmdir-wrmdir.md)   
 [system, _wsystem](../../c-runtime-library/reference/system-wsystem.md)