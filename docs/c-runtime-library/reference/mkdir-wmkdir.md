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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 56e525dd765ff2594eebcfe9a0aed37670b12e3e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338789"
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
Cesta pro nový adresář.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrátí hodnotu 0, pokud byl vytvořen nový adresář. Při chybě funkce vrátí -1 a nastaví **errno** následujícím způsobem.

**EEXIST** Adresář nebyl vytvořen, protože *dirname* je název existujícího souboru, adresáře nebo zařízení.

**ENOENT** Cesta nebyla nalezena.

Další informace o těchto a dalších návratových kódech naleznete [v tématech _doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Funkce **_mkdir** vytvoří nový adresář se zadaným *dirnamem.* **_mkdir** můžete vytvořit pouze jeden nový adresář pro volání, takže pouze poslední součást *dirname* může pojmenovat nový adresář. **_mkdir** nepřekládá oddělovače cest. V systému Windows NT \\jsou zpětné lomítko ( ) i lomítko (/ ) platné oddělovače cest v řetězcích znaků v rutinách běhu.

**_wmkdir** je širokoznaková verze **_mkdir**; *dirname* argument **_wmkdir** je řetězec široký znak. **_wmkdir** a **_mkdir** se chovají stejně jinak.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmkdir**|**_mkdir**|**_mkdir**|**_wmkdir**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_mkdir**|\<direct.h>|
|**_wmkdir**|\<direct.h> \<nebo wchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven c run-time](../../c-runtime-library/crt-library-features.md).

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

[Řízení adresářů](../../c-runtime-library/directory-control.md)<br/>
[_chdir, _wchdir](chdir-wchdir.md)<br/>
[_rmdir, _wrmdir](rmdir-wrmdir.md)<br/>
