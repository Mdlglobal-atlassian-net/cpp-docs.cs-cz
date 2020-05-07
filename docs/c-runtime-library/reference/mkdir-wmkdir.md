---
title: _mkdir, _wmkdir
ms.date: 4/2/2020
api_name:
- _wmkdir
- _mkdir
- _o__mkdir
- _o__wmkdir
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mkdir
- tmkdir
- _tmkdir
- wmkdir
- _wmkdir
helpviewer_keywords:
- _wmkdir function
- folders [C++], creating
- wmkdir function
- directories [C++], creating
- mkdir function
- tmkdir function
- _mkdir function
- _tmkdir function
ms.assetid: 7f22d01d-63a5-4712-a6e7-d34878b2d840
ms.openlocfilehash: f4714e3e763b827772a7d2eb61ae2e14f0aece02
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919151"
---
# <a name="_mkdir-_wmkdir"></a>_mkdir, _wmkdir

Vytvoří nový adresář.

## <a name="syntax"></a>Syntaxe

```C

int _mkdir(
   const char *dirname
);
int _wmkdir(
   const wchar_t *dirname
);
```

### <a name="parameters"></a>Parametry

*dirname*<br/>
Cesta k novému adresáři

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrací hodnotu 0, pokud byl nový adresář vytvořen. Při chybě vrátí funkce hodnotu-1 a nastaví **errno** následujícím způsobem.

**EEXIST** Adresář nebyl vytvořen, protože *dirname* je název existujícího souboru, adresáře nebo zařízení.

**ENOENT** Cesta nebyla nalezena.

Další informace o těchto a dalších návratových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Funkce **_mkdir** vytvoří nový adresář se zadaným *dirname.* **_mkdir** může vytvořit jenom jeden nový adresář pro každé volání, takže jenom poslední součást *dirname* může pojmenovat nový adresář. **_mkdir** nepřevádí oddělovače cest. V systému Windows NT jsou zpětným lomítkem \\() a lomítkem (/) platné oddělovače cest v řetězcích znaků v běhových rutinách.

**_wmkdir** je verze **_mkdir**s velkým znakem; Argument *dirname* pro **_wmkdir** je řetězec s velkým znakem. **_wmkdir** a **_mkdir** se chovají identicky jinak.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmkdir**|**_mkdir**|**_mkdir**|**_wmkdir**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_mkdir**|\<Direct. h>|
|**_wmkdir**|\<Direct. h> nebo \<WCHAR. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Příklad

```C
// crt_makedir.c

#include <direct.h>
#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   if( _mkdir( "\\testtmp" ) == 0 )
   {
      printf( "Directory '\\testtmp' was successfully created\n" );
      system( "dir \\testtmp" );
      if( _rmdir( "\\testtmp" ) == 0 )
        printf( "Directory '\\testtmp' was successfully removed\n"  );
      else
         printf( "Problem removing directory '\\testtmp'\n" );
   }
   else
      printf( "Problem creating directory '\\testtmp'\n" );
}
```

### <a name="sample-output"></a>Vzorový výstup

```Output
Directory '\testtmp' was successfully created
Volume in drive C has no label.
Volume Serial Number is E078-087A

Directory of C:\testtmp

02/12/2002  09:56a      <DIR>          .
02/12/2002  09:56a      <DIR>          ..
               0 File(s)              0 bytes
               2 Dir(s)  15,498,690,560 bytes free
Directory '\testtmp' was successfully removed
```

## <a name="see-also"></a>Viz také

[Řízení adresáře](../../c-runtime-library/directory-control.md)<br/>
[_chdir, _wchdir](chdir-wchdir.md)<br/>
[_rmdir, _wrmdir](rmdir-wrmdir.md)<br/>
