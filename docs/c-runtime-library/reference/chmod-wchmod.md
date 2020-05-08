---
title: _chmod, _wchmod
ms.date: 4/2/2020
api_name:
- _chmod
- _wchmod
- _o__chmod
- _o__wchmod
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
- _chmod
- _wchmod
- wchmod
helpviewer_keywords:
- _chmod function
- wchmod function
- file permissions [C++]
- chmod function
- files [C++], changing permissions
- _wchmod function
ms.assetid: 92f7cb86-b3b0-4232-a599-b8c04a2f2c19
ms.openlocfilehash: b1bc89ce51fff44a847111d68cac8e8b3f58a635
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82916998"
---
# <a name="_chmod-_wchmod"></a>_chmod, _wchmod

Změní nastavení oprávnění souboru.

## <a name="syntax"></a>Syntaxe

```C
int _chmod( const char *filename, int pmode );
int _wchmod( const wchar_t *filename, int pmode );
```

### <a name="parameters"></a>Parametry

*Bitmap*<br/>
Název existujícího souboru.

*pmode*<br/>
Nastavení oprávnění souboru

## <a name="return-value"></a>Návratová hodnota

Tyto funkce vrátí hodnotu 0, pokud je nastavení oprávnění úspěšně změněno. Návratová hodnota-1 označuje chybu. Pokud zadaný soubor nebyl nalezen, **errno** je nastaven na **ENOENT**; Pokud je parametr neplatný, **errno** je nastaven na **EINVAL**.

## <a name="remarks"></a>Poznámky

Funkce **_chmod** změní nastavení oprávnění k souboru určenému parametrem *filename*. Nastavení oprávnění řídí přístup pro čtení a zápis k souboru. Celočíselný výraz *pmode* obsahuje jednu nebo obě následující konstanty manifestu definované v SYS\Stat.h..

| *pmode* | Význam |
|-|-|
| **\_S\_IREAD** | Povoluje se pouze čtení. |
| **\_S\_IWRITE** | Zápis povolen. (V důsledku toho povoluje čtení a zápis.) |
| **\_S\_IREAD** &#124; ** \_s\_IWRITE** | Čtení a zápis jsou povoleny. |

Jsou-li obě konstanty zadány, jsou spojeny s bitovým**\|** operátorem OR (). Pokud není uděleno oprávnění k zápisu, je soubor určen jen pro čtení. Všimněte si, že všechny soubory jsou vždy čitelné; není možné poskytovat oprávnění pouze pro zápis. Proto jsou režimy **_S_IWRITE** a **_S_IREAD** \| **_S_IWRITE** ekvivalentní.

**_wchmod** je verze **_chmod**s velkým znakem; Argument *filename* pro **_wchmod** je řetězec s velkým znakem. **_wchmod** a **_chmod** se chovají identicky jinak.

Tato funkce ověří své parametry. Pokud *pmode* není kombinací jedné z konstant manifestu nebo zahrnuje alternativní sadu konstant, funkce je jednoduše ignoruje. Pokud *název souboru* má **hodnotu null**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, **errno** je nastaven na **EINVAL** a funkce vrátí-1.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tchmod**|**_chmod**|**_chmod**|**_wchmod**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_chmod**|\<IO. h>|\<sys/Types. h> \<, sys/stat. h> \<, errno. h>|
|**_wchmod**|\<IO. h> nebo \<WCHAR. h>|\<sys/Types. h> \<, sys/stat. h> \<, errno. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_chmod.c
// This program uses _chmod to
// change the mode of a file to read-only.
// It then attempts to modify the file.
//

#include <sys/types.h>
#include <sys/stat.h>
#include <io.h>
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

// Change the mode and report error or success
void set_mode_and_report(char * filename, int mask)
{
   // Check for failure
   if( _chmod( filename, mask ) == -1 )
   {
      // Determine cause of failure and report.
      switch (errno)
      {
         case EINVAL:
            fprintf( stderr, "Invalid parameter to chmod.\n");
            break;
         case ENOENT:
            fprintf( stderr, "File %s not found\n", filename );
            break;
         default:
            // Should never be reached
            fprintf( stderr, "Unexpected error in chmod.\n" );
       }
   }
   else
   {
      if (mask == _S_IREAD)
        printf( "Mode set to read-only\n" );
      else if (mask & _S_IWRITE)
        printf( "Mode set to read/write\n" );
   }
   fflush(stderr);
}

int main( void )
{

   // Create or append to a file.
   system( "echo /* End of file */ >> crt_chmod.c_input" );

   // Set file mode to read-only:
   set_mode_and_report("crt_chmod.c_input ", _S_IREAD );

   system( "echo /* End of file */ >> crt_chmod.c_input " );

   // Change back to read/write:
   set_mode_and_report("crt_chmod.c_input ", _S_IWRITE );

   system( "echo /* End of file */ >> crt_chmod.c_input " );
}
```

```Output

A line of text.
```

```Output

      A line of text.Mode set to read-only
Access is denied.
Mode set to read/write
```

## <a name="see-also"></a>Viz také

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[_access, _waccess](access-waccess.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_stat, _wstat funkce](stat-functions.md)<br/>
